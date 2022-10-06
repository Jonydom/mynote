# pytorch

## 一、视频号

[bilibili](https://www.bilibili.com/video/BV1hE411t7RN?spm_id_from=333.337.search-card.all.click&vd_source=25c1c7416638ddccf9477db8b230e316)

## 二、安装

1. 安装anaconda

官网地址：[官方渠道](www.anaconda.com)

安装后可以在命令行中键入如下命令，创造python3.7环境。

`conda create -n pytorch python=3.7`

执行如下命令，进入python3.7环境。

`conda activate pytorch`

2. 安装pytorch

官网地址：[官方渠道](https://pytorch.org/)

选择配置，"Stable(1.12.1)-Windows-Conda-Python-CUDA 11.3"，然后弹出安装命令：

`conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch`

在刚才创建的pytorch环境中，键入如上命令，进行pytorch的安装。

命令行输入python，进入python命令行，可以通过两条命令查看pytorch安装是否成功。

`import pytorch`或者`pytorch.cuda.is_available()`

3. 安装jupyter notebook

安装完anaconda之后，默认是安装了jupyter的，但是在jupyter的实际使用中，还要添加一些资源配置，键入如下命令：

`conda install nb_conda`

安装之后，就可以在jupyter notebook中使用conda来进行创建文件等操作。

<img src="assets\image-20220906185800599.png" alt="image-20220906185800599" style="zoom:25%;" />

## 三、课程学习

### 两个函数理解package包里的函数作用

**dir()**

> dir()函数用来列出某个类或者某个模块中的全部内容，包括变量、方法、函数和类等，它的用法为：
>
> `dir(obj)`
>
> obj 表示要查看的对象。obj 可以不写，此时 dir() 会列出当前范围内的变量、方法和定义的类型。

**help()**

> help()函数用来查看某个函数或者模块的帮助文档，它的用法为：
>
> `help(obj)`
>
> obj 表示要查看的对象。obj 可以不写，此时 help() 会进入帮助子程序。

### Pycharm、python控制器、jupyter对比

<img src="assets\image-20220906211804350.png" alt="image-20220906211804350" style="zoom:25%;" />

### 数据处理Dataset

