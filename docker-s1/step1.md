### 入门篇
Docker 是典型的 C/S 架构，其守护进程(dockerd)与命令行(docker)是通过 REST API 进行交互的。所以要想掌握 docker ，那熟练使用命令行工具是必不可少的。

#### 求助命令
* 时刻记住不会就求助 `docker --help`{{execute}} 

#### 运行容器
* 查看下如何运行容器 `docker run --help`{{execute}}
* 启动一个 nginx 容器 `docker run -d nginx`{{execute}}
* 启动一个 nginx 并且对外暴露端口 `docker run -d -p 8080:80 nginx`{{execute}}


#### 查看容器详情
* 查看下如何查看容器信息 `docker ps --hel-`{{execute}}
* 查看正在运行的容器 `docker ps`{{execute}}
* 查看所有的容器 `docker ps -a`{{execute}}