
## ubuntu22.04 fabric使用
1. 安装python3.9
fil集群可跳过此步骤（因为已经安装过监控）

```shell
sudo apt update -y

# 安装software-properties-common软件管理器
sudo apt install software-properties-common -y

# 引入新的apt源
# deadsnakes 在其软件仓库中给出了大量python版本的安装包，这些安装包都是预编译好的，
# 我们不需要进行进一步的编译
sudo add-apt-repository ppa:deadsnakes/ppa   # 需要按下回车

sudo apt update -y 
sudo apt install python3.9 -y

# 接下来，由于有了多版本 Python ，那么设置虚拟环境是必须的，使用以下命令安装虚拟环境套件:
sudo apt install python3.9-venv -y
```

如果是fil集群

```shell
sudo cat >>/home/ps/.bashrc<<'EOF'
export PATH=/home/ps/share/ssd/script/fabric/lotus_monitor_lite/bin:$PATH
EOF
```

普通集群

```shell
mkdir /home/ps/python -p
cd /home/ps/python

# 由于Python3.9，`venv`命令行实用程序有一个`--upgrade-deps`选项，这将强制在新创建的虚拟环境中对pip和setuptools进行UDUpdate
python3.9 -m venv --upgrade-deps .
sudo cat >>/home/ps/.bashrc<<'EOF'
export PATH=/home/ps/python/bin:$PATH
EOF
```

2. 安装对应fabric版本

```shell
> pip install Fabric3==1.14.post1
# 检查并测试fab命令
> fab -V
Fabric3 1.14.post1
Paramiko 2.12.0
# 进入对应fabfile.py目录
> fab hello
```



