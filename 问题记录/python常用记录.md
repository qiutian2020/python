python一键导入所有第三方库requirements

将当前虚拟环境中的依赖包以版本好生成至文件中
```shell
pip freeze > requirements.txt
```

当需要创建这个虚拟环境的完全副本，可以创建一个新的虚拟环境：
```shell
pip install -r requirements.txt
```
