在上一步中我们接触了 nginx、ubuntu 这两个镜像，那么这些镜像都是怎么制作出来的呢?

### Dockerfile 构建镜像

编写应用代码这里以 python 程序为例子 `app.py`{{open}}，复制如下代码:

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5050, debug=True)

```{{copy}}

编写应用依赖 `requirements.txt`{{open}},复制如下代码:

```txt
Flask==1.1.1
```{{copy}}


在命令行中编辑 `Dockerfile`{{open}}，复制如下代码:

```Dockerfile
FROM python
WORKDIR /root/demo

COPY . .
RUN pip install -r requirements.txt

CMD ["python", "app.py"]
```{{copy}}

切换到 demo 目录 `cd demo`{{execute}}

构建镜像 `docker build -t flask-app:v1.0.0 .`{{execute}}

构建镜像成功后执行 `docker images`{{execute}} 命令可以看到刚才我们构建的镜像

运行容器 `docker run -d -p 5050:5050 --name flask-app flask-app:v1.0.0`{{execute}}

### 用 commit 命令构建镜像

进入到 flask-app 容器内，`docker exec -it flask-app bash`{{execute}}

创建一个文件，然后退出容器(注意这里是在容器内部) `touch test.txt && exit`{{execute}}

执行 `docker commit flask-app flask-app:v1.0.1`{{execute}}

再次执行 `docker images`{{execute}} 查看镜像

### 发布镜像
在发布镜像之前我们需要使用 `docker login`{{execute}} 命令登录到相关的 registy(默认登录到 docker hub),根据命令行提示，输入 username、password。

当然如果你需要把镜像发布到其它的镜像仓库，可以使用 `docker login --help`{{execute}} 命令查看如何登录。

按照 [docker hub 使用文档](https://docs.docker.com/docker-hub/) 发布镜像，如：

`docker tag flask-app:v1.0.0 yzihua/flask-app:v1.0.0`{{copy}}，(这里需要把 yzihua 换成上一步你登录的账户名)

`docker push yzihua/flask-app:v1.0.0`{{copy}} (这里需要把 yzihua 换成上一步你登录的账户名)，注意镜像默认是公开的

完了上面两步后可以到 docker hub 网站上查看刚刚发布的镜像详情，也可以通过如下命令验证:

使用 `docker search flask-app`{{execute}}

复制 `docker push yzihua/flask-app:v1.0.0`{{copy}} (这里需要把 yzihua 换成上一步你登录的账户名) 到笔记本上执行


### 删除镜像
`docker images`{{execute}} 查看镜像

`docker rmi flask-app`{{execute}} 或者强制删除 `docker rmi flask-app`{{execute}} 

