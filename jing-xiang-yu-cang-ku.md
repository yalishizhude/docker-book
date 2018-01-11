\# 什么是镜像

虽然Docker已经安装好了，但是我们要真正开始使用它创建容器，还需要另一个东西：镜像（image）。

镜像相当于容器的模板，我们必须通过它才能创建镜像。举个例子，镜像就好比我们平常使用软件时下载的“安装程序”，而容器就是运行安装程序之后系统安装的“软件”。安装程序我们可以从软件中心下载，而镜像的下载地方称为镜像仓库（registry）。

\# 怎么获取镜像

\#\# 搜索镜像

\#\#\# 网页

官方提供给我们的镜像仓库现在叫做\[Docker Hub\]\(\[[https://hub.docker.com/\)，现在被集成到\[Docker\]\(https://hub.docker.com/\)，现在被集成到\[Docker](https://hub.docker.com/%29，现在被集成到[Docker]%28https://hub.docker.com/%29，现在被集成到[Docker)\) Store\]\([https://store.docker.com/search?q=&source=verified&type=image\)中。](https://store.docker.com/search?q=&source=verified&type=image%29中。)

登录后会看到类似如下页面（因为Docker Store的页面一直在变，不保证你访问网址看到的页面如图所示），点击上方“Explore”即可查看镜像。

![](/assets/160a7880c8a01c77.jpg)

中间有个搜索框，可以根据镜像名称进行模糊搜索，左边有搜索条件进行过滤，其中“TYPE”条件比较常用。“Store”类型为官方提供的镜像，“Community”为个人上传的公开镜像。相对而言，官方镜像下载次数更高，也更加稳定。

\#\#\# 命令行

如果我们在服务器上没有图形界面可以通过命令行来进行镜像搜索。比如我们要搜索 ubuntu 镜像，打开终端输入：

\`docker search ubuntu\`

将看到如下结果

![](/assets/160a797a6faae37a.jpg)

这个搜索结果列表显示了所有迷宫昵称带有ubuntu的镜像，按照STARS（收藏）数量进行排序，显示了名字（NAME）、描述（DESCRIPTION）、收藏数（STARS）、官方镜像（OFFICIAL值为“OK”），AUTOMATED已经废弃，我们不用管它。

如果你仔细观察就会发现官方镜像和非官方镜像在命名上就有一个显著的特征，非官方镜像名称都有前缀，用斜杠和名字分隔。而这些前缀其实是个人仓库名，代表了镜像的上传者。

\#\# 镜像信息

虽然两种方式都可以搜索镜像，但还是推荐通过网页进行搜索，尤其是使用某个不熟悉的镜像时，因为页面展现的信息往往更丰富。譬如我们在Docker Store上搜索 nginx 镜像并点击查看其详情。

![](/assets/160aae22396ebb9d.jpg)

官方镜像一般介绍都比较丰富，镜像信息大致可以分两块来看。

上面“...Dockerfilelinks”部分所示的内容皆为该镜像的版本，从1.12到1.13都有，还有不同的后缀，比如“alpine”代表该镜像基于alpine镜像进行封装，体积一般会比其它版本的镜像小很多。

下面的详细内容介绍了利用镜像创建容器时添加不同参数会产生什么效果以及一些注意事项，这一块我们使用的时候再关注。

\#\# 拉取镜像

如果你仔细观察上一张截图就会发现，在页面的右边有一条可以复制的命令：

\`docker pull nginx\`

它就是用来下载镜像的，现在打开命令行，输入并执行它吧~

![](/assets/160aaeb31b24915d.jpg)

docker进程会下载该镜像到本地，默认下载的是nginx的“latest”版本，如果我们要下载其它版本的镜像可以在镜像名称后面加上版本号，以冒号“:”分割，例如\`nginx:1.12\`。输入命令查看一下本地的已有的镜像

\`docker images\`

如果之前的\`pull\`命令执行成功，应该可以在命令行窗口中找到nginx镜像。

\# 怎么使用镜像

启动镜像我们会用到\`docker run\`命令，基本格式如下：

\`docker run \[可选参数\] &lt;镜像&gt; \[可选命令\]\`

当然如果镜像不存在的话，Docker会尝试去镜像仓库下载该镜像。

之前已经下载了nginx镜像，可以尝试用它创建容器

\`docker run nginx\`

然后你会发现\*\*什么也没发生！？\*\*进程好像被阻塞了。正确地使用姿势还需要加上一些参数，下一节我们再来继续介绍~

---

本书地址\[[https://yalishizhude.gitbooks.io/docker-book/](https://yalishizhude.gitbooks.io/docker-book/%29\)\]\([https://yalishizhude.gitbooks.io/docker-book/](https://yalishizhude.gitbooks.io/docker-book/%29\)\)

更多web技术内容请关注公众号“web学习社”

![](/assets/webclub.jpg)

