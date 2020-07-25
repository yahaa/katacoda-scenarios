在前面两步中我们学会了，如何使用 docker 命令行工具运行容器，以及制作镜像，那运行中的容器怎么管理呢？

### 容器管理
查看当前系统运行的容器 `docker ps`{{execute}} 

运行一个容器 `docker run -d -p 6789:80 --name nginx1 nginx`{{execute}} 

停止上一步运行的容器 `docker stop nginx1`{{execute}} 

查看当前系统运行的容器 `docker ps`{{execute}} 

查看当前系统所有的容器 `docker ps -a`{{execute}} 

重启上一步 stop 掉的 nginx1 容器 `docker start nginx1`{{execute}} 

强制停止 nginx1 容器 `docker kill nginx1`{{execute}}

彻底删除 nginx1 容器 `docker rm nginx`{{execute}}

查看 nginx1 容器在宿主机的 pid `docker top nginx1`{{execute}}
