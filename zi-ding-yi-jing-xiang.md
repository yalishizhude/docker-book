现在我们已经能够使用Docker来搭建开发环境，但是它并不适合直接部署到生产环境，它还需要获取代码、安装依赖、编译等操作，不能做到一键部署，理想的方式是直接打包生成一个文件，直接执行一条命令就可以运行。Docker就提供了这样的功能，通过生成自定义镜像。



\# 生成镜像

\#\# commit

一种简单的生成自定义镜像的方式就是通过\`docker commit\`命令。



\`docker commit &lt;容器id或容器名&gt; &lt;仓库/镜像tag&gt;\`



这种方式会把某个容器所有更改的信息全部保存提交成镜像，但是配置参数和卷/挂载的文件不会保存。但是这种操作方式并不提倡，原因如下：

\* 镜像提交的时候容器会暂停运行。

\* 提交生成镜像对使用者来说像个黑盒子，无法知晓到底进行了哪些修改。



这种方式更多的是用来排查问题，比如某个容器运行出错了，但是在服务器上排查不便，那么可以commit提交成镜像，然后镜像拉取到本地创建容器进行调试。



\#\# build

比较推荐的方式是编写镜像配置文件\`Dockerfile\`，通过\`docker build\`命令构建。除了可以弥补以上缺点外，还自带缓存，未变更的命令或文件在再次构建镜像时可以直接读取缓存，节省时间。它唯一的缺点就是\`Dockerfile\`有自己的命令，需要一定的学习时间，不过和任何一种高级语言相比，学习难度低很多。



\#\#\# Dockerfile

\`Dockerfile\`的命令比较多，这里以我其中一个项目为例进行分析，学习常用的命令



\`\`\`

\# api-server

FROM node:8

WORKDIR /app

EXPOSE 2018

COPY ./Hongkong /etc/localtime

RUN npm set registry https://registry.npm.taobao.org

RUN yarn global add pm2

COPY ./template /app/template

COPY ./node\_modules /app/node\_modules

COPY ./dist /app

ENTRYPOINT pm2-docker start ./app.js

\`\`\`



\* “\#”，行级注释，不会对编译造成任何影响。

\* “FROM”，依赖的基础镜像，当镜像不存在时会从仓库拉取。

\* “WORKDIR”，创建容器时默认工作目录，可以被覆盖。

\* “EXPOSE”，可供容器外部访问的端口，值可以为数组。

\* “COPY”，将主机的文件或目录复制到容器中。

\* “RUN” ，在容器中执行一行shell脚本命令，这里先将Node.js的仓库设置为国内仓库，然后全局安装模块pm2.

\* “ENTRYPOINT”，容器被创建时执行的shell脚本命令。

 

这样的Dockerfile包含了全局模块安装和文件的拷贝，省略了编译过程，会节省不少时间。但是缺点也明显，需要安装好模块（\`./node\_modules\`）和编译好的文件（\`./dist\`）才能构建成功，是有状态的。而这些文件是一般不会保存到代码仓库上的。



如果要做到无状态的话，我们需要把编译流程也加上：



\`\`\`

\# api-server

FROM node:8

WORKDIR /app

EXPOSE 2018

COPY ./Hongkong /etc/localtime

RUN npm set registry https://registry.npm.taobao.org

RUN yarn global add pm2

COPY ./ /tmp

\# 安装依赖

RUN yarn install

\# 编译代码

RUN yarn run compile

\# 拷贝文件到工作目录

RUN cp -rf /tmp/template /app/template

RUN cp -rf /tmp/node\_modules /app/node\_modules

RUN cp -rf /tmp/dist /app

ENTRYPOINT pm2-docker start ./app.js

\`\`\`



把Dockerfile和源代码保存在一起，当其他人下载源代码后，即可执行\`docker build\`命令构建镜像了。



\#\#\# 构建参数



\# 传输镜像

\#\# 离线传输



\#\# 在线传输



\# 镜像仓库

\#\# 公有仓库

\#\# 私有仓库

