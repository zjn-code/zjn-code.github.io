# Conda 虚拟环境中使用pip安装包

## 搭建conda虚拟环境命令
最近尝试使用conda搭建python虚拟环境，这里记录一些常用的命令。 

```bash
# 创建虚拟环境
conda create -n your_virtual_environment_name python=your_python_version
# 删除虚拟环境
conda remove -n your_virtual_environment_name --all
# 激活虚拟环境
conda activate your_virtual_environment_name
# 关闭当前虚拟环境
conda deactivate
# 在指定虚拟环境中安装包
conda install -n your_virtual_environment_name [package]
# 在当前虚拟环境中安装包
conda install [package]
# 查看安装了哪些包
conda list
``` 

在pycharm中可以指定使用conda虚拟环境 
位置为settings->project->python interpreter 然后在添加解释器中可以找到创建的conda虚拟环境。

## 在虚拟环境中使用pip安装包
虚拟环境搭建好之后出现了另一个问题，有些包无法使用conda install命令安装，这时我想到能不能在虚拟环境中使用pip进行安装呢？先试了一下pip list命令，发现列出的是本地环境中的包，而不是虚拟环境中的。在虚拟环境中pip install了一下果然装进了本地环境中。

在网上找了挺长时间，终于找到能用的方法，这里记录一下 
需要更改当前虚拟环境中的site.py文件，路径是`your_virtual_environment_path/lib/python.version/site.py` 

原本的内容为 
```
USER_SITE = None
USER_BASE = None
``` 
更改为
```
USER_SITE = your_virtual_environment_path/lib/python.version/site-packages
USER_BASE = your_virtual_environment_path
```

