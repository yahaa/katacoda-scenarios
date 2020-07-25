Docker 是典型的 C/S 架构，其守护进程(dockerd)与命令行(docker)是通过 REST API 进行交互的。所以要想掌握 docker ，那熟练使用命令行工具是必不可少的。

#### 求助命令
万能的 --help `docker --help`{{execute}} 

#### 运行容器
查看下如何运行容器 `docker run --help`{{execute}}

后台启动一个 nginx 容器 `docker run -d nginx`{{execute}}

后台启动一个 nginx 并且对外暴露端口 `docker run -d -p 8080:80 nginx`{{execute}}

前台运行容器 `docker run -it ubuntu bash`{{execute}}

挂载宿主机目录至容器中(持久化数据) `mkdir -p test && docker run -it -p 8081:80 -v $(pwd)/test:/root/test nginx`{{execute}}

前台启动退出后自动删除镜像 `docker run -it --rm ubuntu bash`{{execute}}

覆盖镜像指定的 entrypoint(常用来定检测镜像是否构建正确) `docker run -it --rm --entrypoint bash nginx`{{execute}}


#### 查看容器详情
查看下如何查看容器信息 `docker ps --hel-`{{execute}}

查看正在运行的容器 `docker ps`{{execute}}

查看所有的容器 `docker ps -a`{{execute}}