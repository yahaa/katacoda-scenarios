当节点上的容器、镜像变多后我们要怎么管理容器和镜像呢？如何查看 docker 有多少种网络?

### 管理 Docker 节点

查看 system 子命令使用详情 `docker system --help`{{execute}}

查看节点容器、镜像、存储卷、Cache 详情 `docker system df`{{execute}}

删除节点上不用的镜像，停止运行的容器 `docker system prune`{{execute}}

查看 docker 节点网络详情 `docker network ls`{{execute}}

