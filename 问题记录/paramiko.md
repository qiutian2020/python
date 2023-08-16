
ssh协议的实现

作用：

1.远程执行命令

2.文件下载、上传

安装模块

```shell
> pip install paramiko
```


安装paramiko报错
```shell
(pra) ➜  python_practic pip install paramiko
```

报错如下：

<img width="806" alt="image" src="https://github.com/qiutian2020/python/assets/66943119/83cf39b7-61de-466a-9a0f-25c1dd6f513a">


<img width="962" alt="image" src="https://github.com/qiutian2020/python/assets/66943119/8e43a4f2-c073-418d-b520-68c8d9d2c18b">



解决方法：
```shell
(pra) ➜  python_practic pip install -U pip setuptools
```

<img width="345" alt="image" src="https://github.com/qiutian2020/python/assets/66943119/a112c567-7b77-4c3e-b6a5-64e08a6b7ec0">

再次安装成功
