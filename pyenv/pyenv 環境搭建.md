## pyenv 環境搭建



### **創建python用戶**

```shell
[root@localhost ~]# useradd python 
[root@localhost ~]# passwd python 
Changing password for user python.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.
```



### **安裝依賴環境軟件**

```shell
[root@localhost ~]#  yum -y install gcc make patch gdbm-devel  openssl-devel sqlite-devel readline-devel zlib-devel bzip2-devel git
```



### 切換用戶

```shell
[root@localhost ~]#  su - python 
```





### pyenv 脚本



```shell
https://github.com/pyenv/pyenv-installer
```

##### **pyenv installer**

```
This tool installs [pyenv](https://github.com/pyenv/pyenv) and friends. It is inspired by [rbenv-installer](https://github.com/rbenv/rbenv-installer).
```

##### Prerequisites

```shell
In general, compiling your own Python interpreter requires the installation of the appropriate libraries and packages. The installation wiki provides a list of these for common operating systems.
```

Installation / Update / Uninstallation

Once prerequisites have been installed correctly:

### Install:

```
$ curl https://pyenv.run | bash
```

`pyenv.run` redirects to the install script in this repository and the invocation above is equivalent to:

```
$ curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```

Restart your shell so the path changes take effect:

```
$ exec $SHELL
```

You can now begin using pyenv.

If you need, `export USE_GIT_URI` to use `git://` instead of `https://` for git clone.

### Update:

```
$ pyenv update
```

### Uninstall:

`pyenv` is installed within `$PYENV_ROOT` (default: `~/.pyenv`). To uninstall, just remove it:

```
$ rm -fr ~/.pyenv
```

then remove these three lines from `.bashrc`:

```
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

and finally, restart your shell:

```
$ exec $SHELL
```



### 下載python 包

以3.5.3爲例子 

下面為python 3.5.3 的鏈接

```shell
https://www.python.org/ftp/python/3.5.3/Python-3.5.3.tar.xz
```



### 安裝python 

加速軟件編譯 

```shell
[python@localhost ~]$ cd .pyenv/
[python@localhost ~]$ mkdir cacahe
[python@localhost ~]$ cp /home/python/Python-3.5.3.tar.xz  . 
```

編譯python 軟件

```shell
[python@localhost ~]$ pyenv install 3.5.3
```

```shell
[python@localhost ~]$ python
python             python3            python3.5-gdb.py   python3-config     
python2            python3.5          python3.5m         python-config      
python2.7          python3.5-config   python3.5m-config  
```



### Virtualenv 

###### Project description

 A tool for creating isolated ‘virtual’ python environments.

```she
https://pypi.org/project/virtualenv/
```



##### Virtualenv 搭建

```shell
[python@localhost ~]$ pip install virtualenv
```

```shell
[python@localhost python3.5]$ pip install virtualenv
Collecting virtualenv
  Downloading https://files.pythonhosted.org/packages/62/77/6a86ef945ad39aae34aed4cc1ae4a2f941b9870917a974ed7c5b6f137188/virtualenv-16.7.8-py2.py3-none-any.whl (3.4MB)
     |████████████████████████████████| 3.4MB 2.6MB/s 
Installing collected packages: virtualenv
Successfully installed virtualenv-16.7.8

```



##### virtualenv 的使用

```shell
[python@localhost python3.5]$ pyenv virtualenv 3.5.3 mypython
```

```shell
Using base prefix '/home/python/.pyenv/versions/3.5.3'
New python executable in /home/python/.pyenv/versions/3.5.3/envs/mypython/bin/python3.5
Also creating executable in /home/python/.pyenv/versions/3.5.3/envs/mypython/bin/python
Installing setuptools, pip, wheel...
done.
Requirement already satisfied: setuptools in /home/python/.pyenv/versions/3.5.3/envs/mypython/lib/python3.5/site-packages
Requirement already satisfied: pip in /home/python/.pyenv/versions/3.5.3/envs/mypython/lib/python3.5/site-packages
```



##### 查看python 環境版本

```shell
[python@localhost python3.5]$ pyenv version
```

```shell
3.5.3 (set by /home/python/python3.5/.python-version)
[python@localhost python3.5]$ pyenv versions
  system
* 3.5.3 (set by /home/python/python3.5/.python-version)
  3.5.3/envs/mypython
  mypython
```

##### 切換python 環境版本

```shell 
[python@localhost python3.5]$ pyenv local python version
```



```shell 
[python@localhost ~]$ pyenv 
pyenv 1.2.15
Usage: pyenv <command> [<args>]

Some useful pyenv commands are:
   commands    List all available pyenv commands
   activate    Activate virtual environment
   commands    List all available pyenv commands
   deactivate   Deactivate virtual environment
   doctor      Verify pyenv installation and development tools to build pythons.
   exec        Run an executable with the selected Python version
   global      Set or show the global Python version
   help        Display help for a command
   hooks       List hook scripts for a given pyenv command
   init        Configure the shell environment for pyenv
   install     Install a Python version using python-build
   local       Set or show the local application-specific Python version
   prefix      Display prefix for a Python version
   rehash      Rehash pyenv shims (run this after installing executables)
   root        Display the root directory where versions and shims are kept
   shell       Set or show the shell-specific Python version
   shims       List existing pyenv shims
   uninstall   Uninstall a specific Python version
   version     Show the current Python version and its origin
   --version   Display the version of pyenv
   version-file   Detect the file that sets the current pyenv version
   version-name   Show the current Python version
   version-origin   Explain how the current Python version is set
   versions    List all Python versions available to pyenv
   virtualenv   Create a Python virtualenv using the pyenv-virtualenv plugin
   virtualenv-delete   Uninstall a specific Python virtualenv
   virtualenv-init   Configure the shell environment for pyenv-virtualenv
   virtualenv-prefix   Display real_prefix for a Python virtualenv version
   virtualenvs   List all Python virtualenvs found in `$PYENV_ROOT/versions/*'.
   whence      List all Python versions that contain the given executable
   which       Display the full path to an executable

See `pyenv help <command>' for information on a specific command.
For full documentation, see: https://github.com/pyenv/pyenv#readme

```







