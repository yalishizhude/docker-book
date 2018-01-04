\# 安装必要条件

Docker利用的操作系统提供的虚拟化功能，而操作系统的虚拟化功能需要硬件——CPU的支持，所以安装Docker前请确认你的CPU支持并开启了虚拟化技术。所以第一步你需要\*\*确认你的CPU是否支持虚拟化功能\*\*。

可以通过查询你的CPU官网或者通过搜索引擎搜索你的CPU参数，AMD的CPU需要支持AMD-v技术，Intel的CPU需要支持VT-x技术。下图为我机器CPU参数查询结果，看到高级技术部分VT-x技术为Yes，代表支持该技术。

!\[\]\(/assets/160a6bc083b66eab.jpg\)

\*\*确认CPU支持该功能后，请在BIOS的高级设置中开启它\*\*。由于每台机器BIOS页面不同，需要读者认真查找对应技术名称并开启。

\# Docker版本

Docker并不是系统默认安装的软件，我们使用它之前需要从官方网站上进行下载。

Docker分为两个版本Community Edition（社区版本，免费）和Enterprise Edition（企业版本，收费），简称为 Docker CE 和 Docker EE，我们将使用的版本是Docker CE。

而 Docker CE 又分为两个可下载的版本 Stable 和 Edge。

\* Stable版本是被使用和测试过的，功能相对最稳定，适合生产环境，安装程序每个季度更新一次。

\* Edge版本会提供一些最新的功能，但是可能会有一些bug，有兴趣的开发者可以尝试，安装程序每个月更新一次。

\# 在Windows下安装Docker

\#\# 安装前的准备

\*\*首先确保以下条件满足\*\*

\* 至少是Windows8以上的系统。

\* 系统已开启Hyper-V功能。

启动Hypver-V功能操作如下：

1. 右键单击 Windows 按钮并选择“应用和功能”。

2. 选择“打开或关闭 Windows 功能”。

3. 选择“Hyper-V”，然后单击“确定”。

!\[\]\([https://user-gold-cdn.xitu.io/2017/12/30/160a6bfcab13f18a?w=417&h=370&f=png&s=12564\](https://user-gold-cdn.xitu.io/2017/12/30/160a6bfcab13f18a?w=417&h=370&f=png&s=12564\)\)

\#\# 安装

确保满足以上条件之后，进入官方下载页面后，选择其中过一个版本进行下载。官方下载页面：\[[https://store.docker.com/editions/community/docker-ce-desktop-windows\]\(https://store.docker.com/editions/community/docker-ce-desktop-windows\](https://store.docker.com/editions/community/docker-ce-desktop-windows]%28https://store.docker.com/editions/community/docker-ce-desktop-windows\)\)

!\[\]\([https://user-gold-cdn.xitu.io/2017/12/30/160a68f15f09bd98?w=673&h=915&f=jpeg&s=192539\](https://user-gold-cdn.xitu.io/2017/12/30/160a68f15f09bd98?w=673&h=915&f=jpeg&s=192539\)\)

下载后双击运行，点击“accept”和“next”就可以了，安装完成后会弹出欢迎界面。

!\[\]\([https://user-gold-cdn.xitu.io/2017/12/30/160a6b08c87564e8?w=358&h=823&f=png&s=170590\](https://user-gold-cdn.xitu.io/2017/12/30/160a6b08c87564e8?w=358&h=823&f=png&s=170590\)\)

如果任务栏出现白色（红色代表启动失败或停止）的驮着许多集装箱的小鲸鱼，代表Docker服务已经启动了！

\#\# 设置

安装完成之后为了之后方便使用，还需要进行一些配置。右键任务栏白色鲸鱼图标，选择“Settings...”，

在弹出页面点击“Shared Drives”，选择一个你想与容器共享的目录（可以选择你用来放置代码的磁盘），我这里选择的是C盘。

!\[\]\([https://user-gold-cdn.xitu.io/2017/12/30/160a6db423039147?w=833&h=542&f=jpeg&s=92974\](https://user-gold-cdn.xitu.io/2017/12/30/160a6db423039147?w=833&h=542&f=jpeg&s=92974\)\)

点击右下角“Apply”后Docker开始重启。

\*\*这一步不是必须的，但是国内用户为了更流畅的体验，最好设置一下镜像仓库（你懂的）\*\*：

然后点击“Daemon”，把右边的Basic开关打开，在下面的json对象的“registry-mirrors”数组中输入一个国内的镜像地址，这里我输入的是阿里云的地址（可以在\[阿里云开发者平台\]\([https://dev.aliyun.com\)上申请）：\`https://cpnpza13.mirror.aliyuncs.com\`。主要用来加速镜像下载。](https://dev.aliyun.com%29上申请）：`https://cpnpza13.mirror.aliyuncs.com`。主要用来加速镜像下载。)

!\[\]\([https://user-gold-cdn.xitu.io/2017/12/30/160a6db52c128277?w=829&h=538&f=jpeg&s=102885\](https://user-gold-cdn.xitu.io/2017/12/30/160a6db52c128277?w=829&h=538&f=jpeg&s=102885\)\)

忽略红色警告文字，依然点击右下角“Apply”按钮重启Docker。

\# 在Linux下安装Docker

\#\# 安装

直接使用系统自带的包管理器命令进行安装即可。

\`apt-get install docker\`

或者

\`yum install -y docker\`

因为在Linux系统下大多没有图形界面，我们启动服务来检查是否安装成功。启动docker服务

\`systemctl docker start\`

然后执行一条命令，返回docker版本信息代表安装启动成功

\`docker -v\`

\#\# 设置

\*\*这一步不是必须的，但是国内用户为了更流畅的体验，最好设置一下镜像仓库（你懂的）\*\*：

\`vi /etc/docerk/daemon.json\`

\`\`\`

{

```
"registry-mirrors": \["https://cpnpza13.mirror.aliyuncs.com"\]
```

}

\`\`\`

\# 在Mac下安装Docker

可选择直接从官网下载安装包进行安装。

官方下载页面：\[[https://store.docker.com/editions/community/docker-ce-desktop-mac\]\(https://store.docker.com/editions/community/docker-ce-desktop-mac\](https://store.docker.com/editions/community/docker-ce-desktop-mac]%28https://store.docker.com/editions/community/docker-ce-desktop-mac\)\)

也可以使用命令安装

\`brew cask install docker\`

右下角出现鲸鱼图标代表成功安装启动。

镜像仓库设置与Windows操作基本一致。

