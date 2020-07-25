前面 4 步提到的命令都是一些常用命令，但是在实际使用中我们更多的是组合 linux 其它命令来使用，下面介绍常用的组合命令。

### 常用组合命令

强制删除所有镜像 `docker images | awk '{print $3}'|xargs docker rmi -f`{{execute}}

运行一个 demo `docker run -d -p 8886:80 --name nginx-demo nginx`{{execute}}

获取 containerID `docker ps`{{execute}}

用 nsenter 进入容器的 network namespace `docker top <containerID> |grep -v PID| awk '{print $2}'| xargs -I pid nsenter -t pid -n`{{copy}}

grep 关键字定位程序异常日志 `docker logs -f nginx-demo | grep xxx`{{execute}} 

