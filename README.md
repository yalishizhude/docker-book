# Docker是什么？

Docker是一个跨平台的开源容器引擎，可以用它来构建、管理、运行容器。

而容器是利用虚拟化技术，\*\*将应用程序（你的代码）和所需运行环境（代码依赖）封装成独立的进程\*\*。

从Docker这个单词来分析，它在英语中的意思是码头工人，而Docker中运行的容器（container）对应的是集装箱。

如果从命名上来理解。我们可以把不用的应用程序看成是集装箱中的货物，而容器像集装箱一样把它们包装在一起，彼此隔离，然后再由码头工人Docker负责管理和搬运。

延伸一下，集装箱虽然看似简单，但却是世界上最伟大的发明之一。它的出现改变了世界运输历史，《集装箱改变世界》这本书就阐述了它的贡献和作用。可能命名者也希望Docker和容器会像集装箱的出现一样改变软件开发的世界吧~

# 传统应用运行方式的弊端

## 运行环境

传统应用依赖部署在一台主机上，共用系统环境，这样就很容易带来一些问题，譬如端口冲突（一台机器上起了多个数据库给不同应用使用，但是都想使用3306端口）、环境变量冲突（每个应用都可以访问系统资源，环境变量只是系统资源中的一种）、不同应用程序需要不同版本依赖（一个老项目只能在低版本的Node.js中运行，而新项目需要在高版本的Node.js上运行）等。

## 安装依赖

而部署应用的过程也很痛苦，为了让一个程序正常运行，需要安装各种依赖。很可能会因为一些参数不同而导致安装、部署过程报错，开发者不得不为了解决这些问题而耗费大量时间。而即使安装过程不报错，每次部署到不同机器上都需要重新安装依赖和配置环境，这种机械而重复的劳动应该被避免。

# Docker容器化技术的优势

而如果利用虚拟化技术将这些应用都部署到容器中，然后保存成镜像，则可以避免上述两个问题。

首先\*\*容器内部与外部的环境是隔离的\*\*，容器内部配置的环境变量和安装的依赖对其它容器不会产生影响。

其次\*\*Docker是跨平台的\*\*，在容器中正常运行的容器保存成镜像，即可在其它平台运行，从而实现快速部署。

下面这张图对比了容器化应用和传统应用的区别：

![](/assets/160a630b05cf81c9.jpg)

# 学习Dokcer有什么用？

学完本小册后你将掌握下列“神技”（之所以称之为神技，是因为它可以跨平台、跨语言使用，不管你是喜欢windows系统还是用惯了Mac，不管你是用JavaScript开发浏览器端还是Java开发服务端，都可以使用，\*\*一旦学会，终身受益\*\*）：

\* 让你的应用程序启动更快速，秒级启动！

\* 让你摆脱环境依赖不一致造成的困扰，实现一处编译，随处运行！

\* 让一台机器上同时运行需要不同依赖的应用程序，每个容器都是隔离的，就像开了多个虚拟机（比虚拟机消耗的资源少多了）一样！

\* 为应用程序创建多个副本，实现高可用！

\* 让应用实现伸缩、灰度部署、自愈等高级功能......

---

本书地址\[[https://yalishizhude.gitbooks.io/docker-book/](https://yalishizhude.gitbooks.io/docker-book/%29\)\]\([https://yalishizhude.gitbooks.io/docker-book/](https://yalishizhude.gitbooks.io/docker-book/%29\)\)

更多web技术内容请关注公众号“web学习社”

![](/assets/webclub.jpg)

