# 前言 #

> 只有光头才能变强


提前预警：本文**适合Java新手阅读**(老手可在评论区给下建议)，希望大家看完能有所收获。


# 一、为什么我要写下这篇文章 #

## 1.1直接缘由： ##

- 在今天(2018年11月4日)有个同学给我发微信找我
	- 同学：能不能给他一个网页他改一下，他想参考一下，然后用于做毕业设计。
	- 3y：可以啊，你的题目是什么啊？想用Java来写吗？
	- 同学：对啊，我现在在学Java呢(ps:之前跟该同学聊天的时候"我看着这些代码就头晕，我对电脑真不感兴趣"....真香！)
	- 随后这个同学发了一个小视频过来，说自己在学Java。我看了一下：大概是在练习`&^|`这些操作符。

![同学发过来的小视频图--截取](https://user-gold-cdn.xitu.io/2018/11/5/166e21cd4b29040a?w=1017&h=503&f=png&s=81028)

最后，我告诉这同学："你去找视频看吧，你现在学这些对你的毕业设计没有什么帮助的啊"。然后让他去B站找视频看了


> ps:我并不是说学&^|这些运算符是没用的，但如果单纯是想自己用Java来写毕业设计的话，这些知识点应该是用不上的。


## 1.2间接缘由： ##

**自身经历：**

我学习Java也是自学的，在大学期间也是一直一个人在学(身边的同学可能家里有矿)。即便我在学习的时候也去**搜了不少的意见**，例如在知乎上找<Java如何快速入门>，<Java应该怎么样学？>，<给刚开始学Java的年轻人一些建议>等等类似的话题，**但是**现在回过头来看，我还是走了不少的"弯路"了。

比如说，当时我花了蛮多的精力去学JSP，最后整理成博客发到网上去。网友的评论：

- “不玩 JSP 十几年了“。
- “jsp不是老掉牙的技术吗”。
- “看这个有一种穿越的感觉……码了6w多字，看着就心疼……”。
- “这十年前的技术都被挖出来了？”
- “刚毕业时写过好几个自定义标签，那时候感觉好有成就感，但是现在，用于view的jsp，似乎有点过时了，view一般用【模板】或者【完全静态 + ajax + json】了”

![JSP博文](https://user-gold-cdn.xitu.io/2018/11/5/166e21cd15f13a71?w=1558&h=913&f=png&s=55826)

嗯...那篇文章我当时在2018.02.07发布。我学JSP的时候是在2017年初吧，其实在2017年JSP也已经是落后的技术了，但我还是花了不少的时间去学习JSP的各种用法(自定义标签，JSTL，EL表达式等等)。

网友们其实说得都没有毛病，对我来说：在2017年花了**不少时间**去学如何使用JSP(过期的技术)，这就是我认为的**"弯路"**。

- ps:在2018年花点时间了解JSP是没毛病的，但深入学习的话是没必要的。


> "弯路"说明：如果你有**充裕的时间，怎么学都不是事**，毕竟你是真真正正地在学编程。只要在学编程，就不是弯路，最怕你不学。


----------

**以这篇文章回复我部分的读者：**

写博客以来，还是有部分读者是零基础学Java的，有转行的、也有年轻的师弟师妹的。一般他们也问我应该怎么学Java比较好，学习Java的路线应该是怎么样的。

emmmm，我一般都是**比较简单**的回复一下：让他们多做笔记啊，接下来应该花时间学什么，不学什么...就完了..

所以，写完这篇文章，遇到再问我如何学习Java的时候，我直接发个链接就完事了(懒人必备)..


## 1.3目的 ##

**如果你：**

- 想要用Java在短短的几个月时间内写出自己的毕业设计。
- 想要用Java体验一下如何从零搭建一个属于自己的网站。


那么可以看一下我下面所写的**不成熟的建议**。


# 二、如何快速学Java #

> 这里我以Java EE(Jakarta EE)/Java Web的经验来说哦。(都把你们看做是零基础入门的了)


学习Java EE(Jakarta EE)总体来说会有以下三大模块：

- Java
- 数据库
- Web前端


![数据库、Java、Web前端](https://user-gold-cdn.xitu.io/2018/11/5/166e21cd4de506d8?w=1247&h=837&f=png&s=129163)


在我看来，无论学习什么技术都好，在**学习该项技术的细节之前**都得知道：**这项技术是什么，为什么我要学习这项技术，学习了这项技术有什么好处**。

- 看似好像我在说多余的话，但如果你在学习某项技术的时候无法回答上面的三个问题。再过几天，你很大程度上会**忘记**这项你所“学过”的技术。
- 比如说，如何你连“为什么要用多线程”你都无法用通俗的话来解释清楚。即便你**当时**学习的时候知道多线程可以用xxx方式来创建，多线程的xxx的api。那再过两个月，人家问你”Java多线程有什么用啊？”。你想想你还能答什么，我认为你是记不住“多线程可以用xxx方式来创建、多线程的xxx的api”这些知识点了。
- 再比如说，如果学习Spring时不知道IOC和new对象有什么区别，那我为啥不直接new对象而要那么麻烦去学Spring呢？


简单来说：**如果你不知道学习某项技术是干嘛用的，那先不要学**。

----------


如果你是零基础学习Java并**理解力不是爆棚**的话，我建议以**视频**学习为主。

**可能**你会看到这样类似的言论：

- “看视频学习太慢了”
- “直接看源码啊，源码就是最好的解释”
- “有问题直接Google啊，用什么百度”
- “最好的资料是官网文档”
- .....


但是，那都是对有经验的人或者高智商的人群来讲的。

如果是**零基础普通人**，看视频学习/看不懂源码/用百度/看中文博客来学习**不丢人**。


> ps:如果看的视频讲师的语速不是特别快，建议以1.5或者1.75倍速观看。



## 2.1关于视频资源 ##

我在学习Java的时候也收集了很多的视频资源，并不是每个都有看过。只是在混群的时候发现有人发了，就复制下来整理一下罢了。

**关注我的公众号，回复“视频”即可免费领取全部资源！**

![视频资源](https://user-gold-cdn.xitu.io/2018/11/5/166e21cd155c6b03?w=1227&h=826&f=png&s=66178)


其他的视频资源：

- B站：(bilibili.com)一个神奇的网站。如果你想看哪个视频，可以先搜一下B站有没有。
- 慕课网：(imooc.com)里头也有挺多的视频资源。
- 公众号/混qq群/微信群：不少人手里都有几t的资源，如果跟群友的关系不错，一般都会免费给你发的
- ......

## 2.1学习Java基础 ##

零基础学习Java的路线我简单总结为以下：

- 首先去官网下个JDK，按现在常用的版本**JDK1.8**就够学习了
	- 下载地址：JDK1.8下载：[https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- 随后去下载现在Java常用的编辑器**IDEA**(也可以用eclipse，但现在IDEA的确是好用)..
	- 下载地址：IDEA下载：[https://www.jetbrains.com/idea/](https://www.jetbrains.com/idea/)
- 以**1.5/1.75倍速观看**Java基础视频(以刘意为例)

![刘意视频](https://user-gold-cdn.xitu.io/2018/11/5/166e21cd16b2f635?w=1920&h=1030&f=png&s=64077)


在学习Java基础时，我简单来说一下**什么东西可以不碰**：

- `&^|`位运算符，`++i`和`i++`类似这种绕死人的语法
- 内部类
- AWT,SWING编程
- 注解


需要**深入理解**的知识点：

- 流程控制
- 面向对象的概念
- Java语法
	- this指针、重写和重载、final、static等等这些基础的东西
- 集合(包括泛型)
	- 常用的集合类
- IO流
	- IO流代码的编写  
- (理解这些知识点，能够在有提示的情况下码出代码，但**不要为了一些细节钻牛角尖**)

**简单过一遍**的知识：

- 异常
- 多线程
- 网络编程
- 反射机制
- (你**得知道这个知识点是干嘛用的**，为什么要学这个知识点，能看懂具体的代码！)



对于上面所说**深入理解**的知识点，我个人是**非常建议在学习期间写笔记(博客)的**。如果你想写笔记的话，**最好直接**就用`markdown`语法来编写，而不是用word/简单的记事本。

markdown语法非常好学，几分钟跟着就可以学习了，几乎所有的it博客网站都支持`markdown`：

- markdown学习：[https://www.jianshu.com/p/q81RER](https://www.jianshu.com/p/q81RER)

如果喜欢**画思维导图**的，我这里推荐processOn就可以了。无需下载Xmind这么麻烦了：

- ProcessOn来画思维导图：[https://www.processon.com/i/5815483ce4b0baccb2d1f8c6](https://www.processon.com/i/5815483ce4b0baccb2d1f8c6)

有的时候并不需要使用IDEA打开一个`.java`或者`.xml`这样的文件，可以使用`notepad++`记事本：

- NotePad++记事本：[https://notepad-plus-plus.org/](https://notepad-plus-plus.org/)

学会科学上网和使用Chrome浏览器，比如说下载拦截广告插件，英语翻译插件

- Chrome浏览器：[https://www.google.com/chrome/](https://www.google.com/chrome/)
- 拦截广告插件：[https://chrome.google.com/webstore/search/uBlock%20Origin?hl=zh-CN&_category=extensions](https://chrome.google.com/webstore/search/uBlock%20Origin?hl=zh-CN&_category=extensions)
- 英语翻译插件：[https://chrome.google.com/webstore/search/%E6%B2%99%E6%8B%89%20%E6%9F%A5%20%E8%AF%8D?hl=zh-CN](https://chrome.google.com/webstore/search/%E6%B2%99%E6%8B%89%20%E6%9F%A5%20%E8%AF%8D?hl=zh-CN)


虽然是快速学习Java，但学完上面的**估计得一个月了**(:..

一个月发现都是面向控制台编程(console)，输入输出一些数据来玩。

![控制台](https://user-gold-cdn.xitu.io/2018/11/5/166e21cd47774fc5?w=1223&h=639&f=png&s=6371)

期间可能就学习IO的时候可以复制文件，修改文件名有点意思。**但好日子就要来临了**！


## 2.2学习Java Web基础 ##


首先我们可以学习一下Web前端的知识(此部分都简单过一下就好了)

- HTML/CSS/JavaScript/jQuery
- CSS框架(都有中文手册，很快就上手了，选一个自己喜欢的就好了)：
	- BootStrap：[http://www.bootcss.com/](http://www.bootcss.com/)
	- Materialize：[http://www.materializecss.cn/](http://www.materializecss.cn/)


到目前为止，学完上面这些可以搭建“能看”的静态网页了。曾经看过一段话来总结上面的技术：

- “**HTML是名词，CSS是形容词，JavaScript是动词**”



随后学习JavaWeb的路线如下：

- Tomcat(简单过一下)
- XML/注解(简单过一下)
- Servlet(**重点理解**)
- HTTP协议(**重点理解**)
- Filter过滤器(**重点理解**)
- Listener监听器(简单过一下)
- JSP(简单过一下)
- AJAX、JSON(简单过一下)

![Servlet知识点](https://user-gold-cdn.xitu.io/2018/11/5/166e21cd9fc1962e?w=4593&h=2139&f=png&s=839719)


基于上面的学习，起码已经可以使用request对象来接收前端发送过来的数据，使用response对象将Java后端的数据返回给前端，使用Filter拦截器来处理中文乱码问题(Tomcat默认的编码是ISO-88591)。总的来说已经可以实现**前后端交互了**！






## 2.3学习数据库 ##

数据库这里指的是关系型数据库，一般我们以**MySQL**来入门就足够了。


在学习期间，其实很多时间都耗费在**配置环境**上面，比如我之前安装JDK，安装MySQL，安装Oracle就耗费了不少时间。后来我也将其写成博客，需要重新安装的时候翻一下博客就好了。

- 比如MySQL安装教程：[https://segmentfault.com/a/1190000013530782](https://segmentfault.com/a/1190000013530782)


主要学习SQL的基本使用吧：

- **创建表(create table)**
- **增删改查(insert,delete,update,select)**
- 对于存储过程、触发器这些了解一下即可
- 对于索引、锁后面再学(**此部分很重要**，但以快速入门来说，可以先不看)


![MySQL基本语法](https://user-gold-cdn.xitu.io/2018/11/5/166e21cda44ce9bf?w=3390&h=1833&f=png&s=472008)


## 2.4学习Java连接数据库(JDBC) ##


到这里，我们Java Web、数据库、Web前端的基础都已经基本学完了，但此时Java和数据库是相互独立的。我们想要以**程序**的方式来对数据库的数据进行操作，那就要学习一下Java连接数据库(JDBC)。


JDBC这项技术并不难呀，就是模板代码，来来去去就几个步骤：

- 导入MySQL或者Oracle驱动包
- 装载数据库驱动程序
- 获取到与数据库连接
- 获取可以执行SQL语句的对象
- 执行SQL语句
- 关闭连接

由于这些代码可能会重复出现，那我们可以学习一下**DbUtils**这个组件：可以帮我们减少编写JDBC的模板代码。

## 2.6项目管理和框架的学习 ##

经过上面的学习，已经是可以在本地写一个Web项目了。

- 页面框架使用BootStrap/Materialize框架来搭好
- 请求处理交由Servlet，返回的数据可以通过AJAX或者使用JSP，DAO层可以使用DbUtils。
- 数据保存在MySQL中


为了让写代码变得**更爽**，我建议用半天学一下**Maven**(项目管理工具)，用几天学一下**SpringBoot**。

- 从Servlet直接跳到SpringBoot可能有点难理解，但多搞几天我相信还是可以的..

## 2.7Linux学习 ##

最后，我们在本地上写完的项目想要让其他人都看得见，一般都会部署在Linux环境下的。(此部分的学习可以等到将项目写完，想要部署项目才学习)


我是不推荐使用虚拟机再搞Linux的，**直接买一台方便很多**

如果要买阿里云服务的，不妨通过这个链接去购买(可以领劵)

- https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=pfn5xpli

# 三、总结 #

总结一下我认为学习Java的路线：

- Java基础-->流程控制-->面向对象(包括Java语法)-->Java集合-->Java IO流-->异常-->多线程-->网络编程-->反射
- JavaWeb基础-->HTML/CSS/JavaScript/jQuery-->Tomcat-->XML/注解->Servlet-->HTTP-->Filter过滤器和监听器-->JSP-->AJAX/JSON-->数据库(MySQL)-->JDBC和DbUtils
- 项目管理和框架-->Maven-->SpringBoot
- Linux基本命令



最后我们的项目是这样的：

- 以Maven来管理我们的项目
- 前端通过BootStrap来搭建页面框架
- SpringBoot来搭建Java后端环境，SpringMVC处理前端请求(SpringBoot整合了)
- DAO层使用DbUtils组件来完成，MySQL作为数据库

当然了，我的Java路线不一定就是对的，我这里只是给出一种路线。

再次说明：这套路线是以“快速”学习Java的，**如果你想要找到一份好工作，上面的知识点是不够的**！

**如果是你，你会给出一条怎么样的Java路线？不妨在评论区留言~~**



> 一个**坚持原创的Java技术公众号：Java3y**，欢迎大家关注


3y所有的原创文章：

- **文章的目录导航(脑图+海量视频资源)**：[https://github.com/ZhongFuCheng3y/3y](https://github.com/ZhongFuCheng3y/3y)

### 如果觉得还不错： ###

关注公众号：Java3y推送最新的**干货**技术文章，进入公众号回复“1”加入**Java交流群**！

![](https://user-gold-cdn.xitu.io/2018/2/28/161dc06a373e4f4d?w=258&h=258&f=jpeg&s=27005)


加微信，回复“1”加入交流群：


![](https://user-gold-cdn.xitu.io/2019/7/13/16be9f6350187ae2?w=564&h=786&f=png&s=156728)



#### :sparkling_heart:坚持原创不易，给博主加鸡腿 ####


如果要买阿里云服务的，不妨通过这个链接去购买(可以领劵，**有优惠**！)

- https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=pfn5xpli

