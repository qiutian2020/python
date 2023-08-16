

## Linux环境
Linux环境自带了Python 2.x版本，但是如果要跟新到3.x的版本，可以在[Python的官方网站](https://www.python.org)下载Python的源代码构建安装的方式进行安装，具体的步骤如下所示

1. 安装依赖库（因为没有这些依赖库可能在源代码构建安装时因为缺失底层依赖库而失败）

参考：
[Python-100-days](https://github.com/jackfrued/Python-100-Days/blob/master/Day01-15/01.%E5%88%9D%E8%AF%86Python.md)

```shell
yum -y install wget gcc zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel libffi-devel
```

2. 下载Python源代码并解压到指定目录

```shell
wget https://www.python.org/ftp/python/3.7.6/Python-3.7.6.tar.xz
xz -d Python-3.7.6.tar.xz
tar -xvf Python-3.7.6.tar
```

3. 切换至Python源代码目录并执行下面的命令进行配置和安装

```shell
cd Python-3.7.6
./configure --prefix=/usr/local/python37 --enable-optimizations
# --enable-optimizations选项将启用优化，以提高Python的性能

# make -j $(nproc)
# make -j $(nproc)命令会使用所有可用的CPU核心来加速编译过程
make && make install
```





4.修改用户主目录下名为.bash_profile(或.bashrc)的文件，配置PATH环境变量并使其生效

```shell
cd ~
vim .bash_profile
```

```shell
# ... 此处省略上面的代码  ...

export PATH=$PATH:/usr/local/python37/bin

# ... 此处省略上面的代码  ...
```

5.激活环境变量

```Shell
source .bash_profile
```




报错：
```shell
[root@centos7 Python-3.9.0]# ./configure --prefix=/usr/local/python37 --enable-optimizations

[root@centos7 Python-3.9.0]# make

Could not import runpy module
Traceback (most recent call last):
  File "/root/Python-3.9.0/Lib/runpy.py", line 15, in <module>
    import importlib.util
  File "/root/Python-3.9.0/Lib/importlib/util.py", line 2, in <module>
    from . import abc
  File "/root/Python-3.9.0/Lib/importlib/abc.py", line 17, in <module>
    from typing import Protocol, runtime_checkable
  File "/root/Python-3.9.0/Lib/typing.py", line 21, in <module>
    import collections
SystemError: <built-in function compile> returned NULL without setting an error
generate-posix-vars failed
make[1]: *** [pybuilddir.txt] 错误 1
make[1]: 离开目录“/root/Python-3.9.0”
make: *** [profile-opt] 错误 2
[root@centos7 Python-3.9.0]# 

```


解决：

```shell
[root@centos7 Python-3.9.0]# make clean     # 清除上次的 make命令 所产生的object文件

导致原因
在低版本的gcc版本中带有 --enable-optimizations 参数时会出现上面问题
gcc 8.1.0修复此问题

解决方法如下
1、升级gcc至8.1.0【不推荐】
2、./configure参数中去掉 --enable-optimizations
```



设置pip镜像源

```shell
#检查当前的pip配置
pip3 config list
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip3 config list
```
参考：[Linux (centos) 安装Python3.9](https://blog.csdn.net/rock1112uhhgg/article/details/131938042)






```shell
[root@centos7 ~]# ls -l /usr/bin/python
lrwxrwxrwx 1 root root 16 8月  15 15:56 /usr/bin/python -> /usr/bin/python2
[root@centos7 ~]# ls -l /usr/bin/python2
lrwxrwxrwx. 1 root root 9 6月  25 22:38 /usr/bin/python2 -> python2.7
```


创建虚拟环境

方法一

使用虚拟环境：由于Python包的各种版本和依赖关系，安装某些包可能会影响其他项目的运行。可以使用Python虚拟环境来隔离每个项目的依赖和版本。例如，使用venv创建虚拟环境：

```shell
python -m venv myenv
source myenv/bin/activate 


$ python3 -m venv venv
$ source venv/bin/activate   # 开启虚拟环境 (在Linux系统中)
$ venv/bin/deactivate        # 关闭虚拟环境

$ venv\Scripts\activate      #(在Windows系统中)
```

方法二
通过virtualenv 命令来创建虚拟环境，首先通过 pip 命令安装虚拟环境工具

```shell
pip install virtualenv
```

然后，创建虚拟环境
```shell
virtualenv venv
```

参考
[pycharm设置虚拟环境与更换镜像教程](https://www.jb51.net/article/221977.htm)


虚拟环境三方包安装的位置

/Users/qt/100_20211110/env_demo/lib/python3.6/site-packages
