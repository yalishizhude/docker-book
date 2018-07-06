# Docker是什么？

Docker是一个跨平台的开源容器引擎，可以用它来构建、管理、运行容器。

而容器是利用虚拟化技术，\*\*将应用程序（你的代码）和所需运行环境（代码依赖）封装成独立的进程\*\*。

从Docker这个单词来分析，它在英语中的意思是码头工人，而Docker中运行的容器（container）对应的是集装箱。

如果从命名上来理解。我们可以把不用的应用程序看成是集装箱中的货物，而容器像集装箱一样把它们包装在一起，彼此隔离，然后再由码头工人Docker负责管理和搬运。

延伸一下，集装箱虽然看似简单，但却是世界上最伟大的发明之一。它的出现改变了世界运输历史，《集装箱改变世界》这本书就阐述了它的贡献和作用。从Docker的命名来看也能窥见其野心——希望像集装箱改变运输历史一样改变软件开发的世界。

# 传统应用运行方式的弊端

## 运行环境

传统应用依赖部署在一台主机上，共用系统环境，这样就很容易带来一些问题，譬如端口冲突（一台机器上起了多个数据库给不同应用使用，但是都想使用3306端口）、环境变量冲突（每个应用都可以访问系统资源，环境变量只是系统资源中的一种）、不同应用程序需要不同版本依赖（一个老项目只能在低版本的Node.js中运行，而新项目需要在高版本的Node.js上运行）等。

## 安装依赖

而部署应用的过程也很痛苦，为了让一个程序正常运行，需要安装各种依赖。很可能会因为一些参数不同而导致安装、部署过程报错，开发者不得不为了解决这些问题而耗费大量时间。而即使安装过程不报错，每次部署到不同机器上都需要重新安装依赖和配置环境，这种机械而重复的劳动应该被避免。

# 虚拟化技术

为了解决以上问题，比较成熟和常用的解决方案是通过虚拟机来对运行环境进行封装和隔离。但是这种方案也并不完美，如果你在电脑上安装过vmware或virtualbox这类虚拟机就能体会到，搭建一台虚拟机并不是太容易的事情。而且虚拟机不仅消耗空闲的磁盘、内存等硬件资源，而且也不利于快速部署和扩展。

但是Docker容器就弥补了以上缺点，首先作为一种虚拟化技术，具有虚拟机同样的有点，比如容器内部与外部的环境是隔离的，容器内部配置的环境变量和安装的依赖对其它容器不会产生影响。其次是跨平台的，现在主流操作系统Windows、Mac、Linux都支持Docker。同时它还具有一些独特的优点，比如可以节省硬件资源、可以生成镜像快速部署和启停、具有强大的编排工具可以批量跨机器操作容器等。

下面这张图能帮助我们更好的理解容器化应用和传统应用的区别：

![](/assets/160a630b05cf81c9.jpg)

---

本书地址\[[https://yalishizhude.gitbooks.io/docker-book/](https://yalishizhude.gitbooks.io/docker-book/%29\)\]\([https://yalishizhude.gitbooks.io/docker-book/](https://yalishizhude.gitbooks.io/docker-book/%29%29\)

更多web技术内容请关注公众号“web学习社”

![](/assets/webclub.jpg)

