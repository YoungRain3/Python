# python jupyter 記事本

**Jupyter**（[![聆听](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Speakerlink-new.svg/11px-Speakerlink-new.svg.png)](https://upload.wikimedia.org/wikipedia/commons/c/c5/En-us-Jupiter.ogg)**[i](https://zh.wikipedia.org/wiki/File:En-us-Jupiter.ogg)**[/ˈdʒuːpɪtər/](https://zh.wikipedia.org/wiki/Help:英語國際音標)）是一个[非营利组织](https://zh.wikipedia.org/wiki/非营利组织)，旨在“为数十种编程语言的[交互式计算](https://zh.wikipedia.org/w/index.php?title=交互式计算&action=edit&redlink=1)开发[开源软件](https://zh.wikipedia.org/wiki/开源软件)，开放标准和服务”。2014年由Fernando Pérez从[IPython](https://zh.wikipedia.org/wiki/IPython)中衍生出来，Jupyter支持几十种语言的执行环境。Jupyter Project的名称是对Jupyter支持的三种核心编程语言的引用，这三种语言是[Julia](https://zh.wikipedia.org/wiki/Julia_(编程语言))、[Python](https://zh.wikipedia.org/wiki/Python)和[R](https://zh.wikipedia.org/wiki/R语言)，也是对[伽利略](https://zh.wikipedia.org/wiki/伽利略)记录发现[木星的卫星](https://zh.wikipedia.org/wiki/木星的卫星)的笔记本的致敬。Jupyter项目开发并支持交互式计算产品Jupyter Notebook、JupyterHub和JupyterLab，这是Jupyter Notebook的下一代版本。



LINUX 系統配置

新建目錄

```shell
[python@localhost ~]$ mkdir python 
[python@localhost ~]$ ll
drwxrwxr-x. 3 python python 97 Jan  4 03:40 python
```

進入目錄

```shell
[python@localhost ~]$ cd  python 
```

```shell
[python@localhost python]$ pip install jupyter
```



啓動python 

```python

[python@localhost python]$ python
Python 3.6.0 (default, Jan  4 2020, 03:03:00)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>

```

```python
>>> from notebook.auth import passwd
>>> passwd() 會提示你輸入密碼，輸入就好了
```

你會得到一串哈希字符串,保存好。

```shell
'sha1:2ec0a730f8be:378eda5781ccc576a0ea4f379347141333a38449'
```

退出python 環境

```python
>>> quit() or Ctrl-D (i.e. EOF) to exit
```



生成jupyter的配置文件

```shell
[python@localhost python]$ jupyter notebook --generate-config
```

修改jupyter配置文件, 配置文件是以#開頭為注釋

```shell
c.NotebookApp.ip = '*'
c.NotebookApp.password = u'sha1:2ec0a730f8be:378eda5781ccc576a0ea4f379347141333a38449' 

```

```shell
注意 哈希字符串前面是有字母 u 的。
```



在python 目錄裏 啓動 jupyter    ok 了

```shell
[python@localhost python]$ jupyter-notebook
[W 04:08:24.917 NotebookApp] WARNING: The notebook server is listening on all IP addresses and not using encryption. This is not recommended.
[I 04:08:24.920 NotebookApp] Serving notebooks from local directory: /home/python/python
[I 04:08:24.920 NotebookApp] The Jupyter Notebook is running at:
[I 04:08:24.920 NotebookApp] http://localhost.localdomain:8888/
[I 04:08:24.920 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
```



linux 網路配置

selinux  關閉

```shell
[root@localhost ~]# setenforce 0            臨時的
```

```shell
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled        改這裏 改爲  disabled
# SELINUXTYPE= can take one of three values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
```





防護墻 

關閉 方式自己選擇

```shell
iptables 關閉防護墻
[root@localhost ~]# iptables -F

firewalld 關閉
[root@localhost ~]# systemctl stop firewalld.service
[root@localhost ~]# systemctl disable  firewalld.service
```

或者端口放行 port  8888 

重啓機器

```shell
[root@localhost ~]#  reboot
```













