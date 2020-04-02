# 解决pip下载速度慢问题

PyPI (Python Package Index) 是 Python 编程语言的软件存储库。开发者可以通过 PyPI 查找和安装由 Python 社区开发和共享的软件，也可以将自己开发的库上传至 PyPI 。

## 配置方法

a. 找到下列文件

```shell
~/.pip/pip.conf
```

b. 在上述文件中添加或修改:

```shell
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/

[install]
trusted-host=mirrors.aliyun.com
```



>https://developer.aliyun.com/mirror/pypi?spm=a2c6h.13651102.0.0.3e221b11ZP96Ev
