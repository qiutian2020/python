参考：
https://github.com/jackfrued/Python-100-Days/blob/master/Day01-15/01.%E5%88%9D%E8%AF%86Python.md

wget https://www.python.org/ftp/python/3.7.6/Python-3.7.6.tar.xz
xz -d Python-3.7.6.tar.xz
tar -xvf Python-3.7.6.tar

cd Python-3.7.6
./configure --prefix=/usr/local/python37 --enable-optimizations
# --enable-optimizations选项将启用优化，以提高Python的性能

# make -j $(nproc)
#make -j $(nproc)命令会使用所有可用的CPU核心来加速编译过程
make && make install


cd ~
vim .bash_profile


export PATH=$PATH:/usr/local/python37/bin


source .bash_profile
