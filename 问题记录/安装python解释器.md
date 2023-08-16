

## Linux环境
Linux环境自带了Python 2.x版本，但是如果要跟新到3.x的版本，可以在[Python的官方网站](https://www.python.org)下载Python的源代码构建安装的方式进行安装，具体的步骤如下所示

1. 安装依赖库（因为没有这些依赖库可能在源代码构建安装时因为缺失底层依赖库而失败）

参考：
https://github.com/jackfrued/Python-100-Days/blob/master/Day01-15/01.%E5%88%9D%E8%AF%86Python.md

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


