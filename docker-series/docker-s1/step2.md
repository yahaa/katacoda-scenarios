在上一步中我们接触了 nginx、ubuntu 这两个镜像，那么这些镜像都是怎么制作出来的呢?

### Dockerfile

* 编写应用代码这里以 python 程序为例子 `app.py`{{open}}，复制如下代码:

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5050, debug=True)

```{{copy}}

* 编写应用依赖 `requestments.txt`{{open}},复制如下代码:

```txt
Flask==1.1.1
```{{copy}}


在命令行中编辑 `Dockerfile`{{open}}，复制如下代码:

```Dockerfile
FROM python
WORKDIR /root/demo

COPY app.py .
RUN pip install -r requirements.txt

CMD ["python", "app.py"]
```{{copy}}

