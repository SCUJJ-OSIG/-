# python包管理conda命令

[TOC]



## 1.创建一个新环境



```shell
#创建环境
conda create -n your_env_name python=X.X 
conda create --name your_env_name python=X.X
-n即--name，your_env_name是你自定义的环境名称


```

例如：

conda create -n newenv python=3.7

 python=3.7会安装最新的python3.7系列版本（如3.7.12）

如要指定更详细的版本，需使用python=3.7.2

## 2.激活某个环境

```shell

##2.激活某个环境
#激活，activate。即进入某个环境。

Windows系统：
conda activate your_env_name


Linux系统：
source activate your_env_name

激活环境后，可检查当前环境下的Python版本：
python --version


```

## 3.包的安装和删除、环境删除

```shell


#3.包的安装和删除、环境删除
#激活到指定环境后，可直接向环境中安装所需的包：

#安装包：

conda install [package] 

#如：conda install numpy
 #指定包版本：conda install xlrd=1.2.0 (注意是单等于号）
 #也可以使用pip install安装 pip install xlrd==1.2.0 (注意是双等于号）
 #查看可用的版本：pip install spyder==*
 
 
#删除当前环境中的某个包：

conda remove [package] 
 请注意：并非conda uninstall
 pip指令下才有 pip uninstall
#升级某个包：

conda update [package]
 conda update --all 升级所有包
#退出当前虚拟环境：

source deactivate  # Linux环境

conda deactivate # Windows环境
#删除某个虚拟环境：

conda remove -n your_env_name --all
 -n即--name
#复制某个虚拟环境：

conda create --name new_env_name --clone old_env_name 
在安装前的确认[Y/N]的时候，false表示由用户再做决定，而不直接进行： 

conda config --set always_yes false
```







## 4.环境查询
```shell

#查看安装了哪些包：

conda list
#查看当前有哪些虚拟环境：

conda env list
conda info --envs

#查询环境python版本：
python --version

#查询conda版本：

conda --version
#更新conda：

conda update conda
#查看conda环境详细信息：

conda info

```




## 5.分享/备份环境

```	shell


#一个分享环境的快速方法就是给他一个你的环境的.yml文件。

#首先激活到要分享的环境，在当前工作目录下生成一个environment.yml文件。

conda env export > environment.yml
#对方拿到environment.yml文件后，将该文件放在工作目录下，可以通过以下命令从该文件创建环境。

conda env create -f environment.yml
```




## 6.镜像源



```shell
#conda方法：

#查看镜像源：

conda config --show channels
#添加镜像源（如清华源）：

conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
conda config --set show_channel_urls yes

 conda config --set show_channel_urls yes  #的意思是从channel中安装包时显示channel的url，这样就可以知道包的安装来源了。
#清除索引缓存，保证用的是镜像站提供的索引： 
conda clean -i

#搜索包： 

conda search [package]

#切换回默认源：

conda config --remove-key channels
#移除某个镜像源（如清华源）：

conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/


#pip方法：

#临时指定安装某个包使用的镜像源：

pip install [package] -i https://pypi.tuna.tsinghua.edu.cn/simple/
pip install [package] -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com

#



```

```html

清华：https://pypi.tuna.tsinghua.edu.cn/simple
腾讯：https://mirrors.cloud.tencent.com/pypi/simple
阿里云：http://mirrors.aliyun.com/pypi/simple/
中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/
华中理工大学：http://pypi.hustunique.com/
山东理工大学：http://pypi.sdutlinux.org/ 
豆瓣：http://pypi.douban.com/simple/
```





## 7.清理






```shell
#删除没有用的包：

conda clean -p     
#删除tar包：

conda clean -t     
#删除所有的安装包及cache：

conda clean -y --all 
```





