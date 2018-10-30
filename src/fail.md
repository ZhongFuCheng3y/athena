# 前言 #

> 只有光头才能变强


在读《Redis设计与实现》关于哈希表扩容的时候，发现这么一段话：

> 执行BGSAVE命令或者BGREWRITEAOF命令的过程中，Redis需要创建当前服务器进程的子进程，而大多数操作系统都采用**写时复制（copy-on-write）来优化子进程的使用效率**，所以在子进程存在期间，服务器会提高负载因子的阈值，从而避免在子进程存在期间进行哈希表扩展操作，避免不必要的内存写入操作，最大限度地节约内存。




触及到知识的盲区了，于是就去搜了一下copy-on-write写时复制这个技术究竟是怎么样的。发现涉及的东西蛮多的，也挺难读懂的。于是就写下这篇笔记来记录一下我学习copy-on-write的过程。



本文**力求简单讲清copy-on-write这个知识点**，希望大家看完能有所收获。


# 一、Linux下的copy-on-write #

在说明Linux下的copy-on-write机制前，我们首先要知道两个函数：`fork()`和`exec()`。需要注意的是`exec()`并不是一个函数, 其实它只是**一组函数的统称**, 它包括`execl()`、`execlp()`等等


## 1.1简单来用用fork ##

首先我们来看一下`fork()`函数是什么鬼：

> fork is an operation whereby a process creates a copy of itself.

fork是类Unix操作系统上**创建进程的主要方法**。fork实际上就是：**创建子进程**(自身进程的副本)。

- 新的进程要通过老的进程复制自身得到，这就是fork！


如果接触过Linux，我们会知道Linux下**init进程是所有进程的爹**(相当于Java中的Object对象)

- Linux的进程都由init进程或init的子进程fork(vfork)出来的。

下面以例子说明一下fork吧：

```c

#include <unistd.h>  
#include <stdio.h>  
 
int main ()   
{   
    pid_t fpid; //fpid表示fork函数返回的值  
    int count=0;
	
	// 调用fork，创建出子进程  
    fpid=fork();

	// 所以下面的代码有两个进程执行！
  
    if (fpid < 0)   
        printf("创建进程失败!/n");   
    else if (fpid == 0) {  
        printf("我是子进程，由父进程fork出来/n");   
        count++;  
    }  
    else {  
        printf("我是父进程/n");   
        count++;  
    }  
    printf("统计结果是: %d/n",count);  
    return 0;  
}  
```

得到的结果输出为：

```c

我是子进程，由父进程fork出来

统计结果是: 1

我是父进程

统计结果是: 1

```

解释一下：

- fork作为一个函数被调用。这个函数会有**两次返回**，将**子进程的PID返回给父进程，0返回给子进程**。(如果小于0，则说明创建子进程失败)。
- 当进程fork的时候(**创建出的子进程实际上就是自身的副本**，所以子进程同样会执行if代码块的代码。)


所以说：

- 父进程在执行if代码块的时候，`fpid变量`的值是子进程的pid
- 子进程在执行if代码块的时候，`fpid变量`的值是0

## 1.2再来看看exec()函数 ##

从上面我们已经知道了fork实际上会创建一个自身的副本作为子进程。很容易理解的是：**既然创建的是副本，那跟原来的进程的数据不是一样吗**？？对，的确是一样的。


exec函数的作用就是：**装载一个新的程序**（可执行映像）覆盖**当前进程**内存空间中的映像，从而执行不同的任务。

我去画张图来理解一下：

![exec函数的作用](https://i.imgur.com/Nt5yopz.png)


参考资料：

- 程序员必备知识——fork和exec函数详解[https://blog.csdn.net/bad_good_man/article/details/49364947](https://blog.csdn.net/bad_good_man/article/details/49364947)
- linux中fork（）函数详解（原创！！实例讲解）：[https://blog.csdn.net/jason314/article/details/5640969](https://blog.csdn.net/jason314/article/details/5640969)
- linux c语言 fork() 和 exec 函数的简介和用法：[https://blog.csdn.net/nvd11/article/details/8856278](https://blog.csdn.net/nvd11/article/details/8856278)
- Linux下Fork与Exec使用：[https://www.cnblogs.com/hicjiajia/archive/2011/01/20/1940154.html](https://www.cnblogs.com/hicjiajia/archive/2011/01/20/1940154.html)


## 1.3回头来看Linux下的COW是怎么一回事 ##

> fork()会产生一个和父进程完全相同的子进程

所以，按我们正常的思维，会将父进程的数据拷贝到子进程中

![父进程的数据拷贝到子进程中](https://i.imgur.com/XybsxWn.png)

但是，以我们的使用经验来说：往往子进程都会执行`exec()`来做自己想要实现的功能。

- 所以，如果按照上面的做法的话，一开始复制过去的数据是无效的(子进程执行`exec()`，子进程数据肯定会被改写)


既然很多时候复制过去给子进程的数据是无效的，于是就有了Copy On Write这项技术了，原理也很简单：

- fork形成的子进程，**与父进程共享内存空间**。也就是说，如果子进程**不对内存空间进行写入操作的话，内存空间中的数据并不会复制**。
- 并且如果在fork函数返回之后，子进程**第一时间**exec一个新的可执行映像，那么就不会浪费时间和内存空间了。

更好的表达方式：

> 在fork之后exec之前两个进程**用的是相同的物理空间**（内存区），子进程的代码段、数据段、堆栈都是指向父进程的物理空间，也就是说，两者的虚拟空间不同，但其对应的**物理空间是同一个**。

> 当父子进程中**有更改相应段的行为发生时**，再**为子进程相应的段分配物理空间**。


> 如果不是因为exec，内核会给子进程的数据段、堆栈段分配相应的物理空间（至此两者有各自的进程空间，互不影响），而代码段继续共享父进程的物理空间（两者的代码完全相同）。


> 而如果是因为exec，由于两者执行的代码不同，子进程的代码段也会分配单独的物理空间。 




参考资料：

- Linux进程基础：[http://www.cnblogs.com/vamei/archive/2012/09/20/2694466.html](http://www.cnblogs.com/vamei/archive/2012/09/20/2694466.html)
- Linux写时拷贝技术(copy-on-write)[http://www.cnblogs.com/biyeymyhjob/archive/2012/07/20/2601655.html](http://www.cnblogs.com/biyeymyhjob/archive/2012/07/20/2601655.html)
- 当你在 Linux 上启动一个进程时会发生什么？[https://zhuanlan.zhihu.com/p/33159508](https://zhuanlan.zhihu.com/p/33159508)
- Linux fork()所谓的写时复制(COW)到最后还是要先复制再写吗？[https://www.zhihu.com/question/265400460](https://www.zhihu.com/question/265400460)




























































# 最后 #


如果大家有更好的理解方式或者文章有错误的地方还请大家不吝在评论区留言，大家互相学习交流~~~




> 一个**坚持原创的Java技术公众号：Java3y**，欢迎大家关注


3y所有的原创文章：

- **文章的目录导航(脑图+海量视频资源)**：[https://github.com/ZhongFuCheng3y/3y](https://github.com/ZhongFuCheng3y/3y)





