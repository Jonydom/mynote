# AHK+caplocks自定义组合按键

平常办公过程中，有很多操作很不方便，比如快速打开右下角闪动的微信、快速打开Chrome检索信息、快速打开资源管理器修改文件等等。为了更加高效地办公，我使用AHK（AutoHotKey）+ caplocks来自定义组合按键，实现按下指定按键，即可执行对应操作，打开指定程序。

## 一、AHK和caplocks环境安装

官方中文指导：[中文指导](https://wyagd001.github.io/zh-cn/docs/Tutorial.htm#s11)

AHK安装步骤：

1. 访问AutoHotKey主页：[主页](https://autohotkey.com/)
2. 点击下载
3. 一路默认安装，选择UNICODE版本

caplocks安装步骤：[github地址](https://github.com/PatrickShieh/CapsLockPlus)

## 二、组合按键

[capslock指南](https://www.autoahk.com/archives/9919)

![1](assets\1.png)

![2](assets\2.png)

![3](assets\3.png)

## 三、个性化修改

capslock已经实现了大多数常用办公功能，但是有些个性化的实现需要我们自己修改。主要修改的文件是`/CAPSLOCKPLUS-MASTER/lib/lib_keysFunction.ahk`和`lib_keysFunLogic.ahk`文件。

<img src="assets\image-20220710122957606.png" alt="image-20220710122957606" style="zoom:25%;" />

### Caplocks + w 打开右下角微信

修改`lib_keysFunction.ahk`文件

<img src="assets\image-20220710123249638.png" alt="image-20220710123249638" style="zoom:50%;" />

修改`lib_keysFuncLogic.ahk`文件

<img src="assets\image-20220710123443478.png" alt="image-20220710123443478" style="zoom:50%;" />

### Caplocks + e 打开右下角钉钉

修改`lib_keysFunction.ahk`文件

<img src="assets\image-20220710123313875.png" alt="image-20220710123313875" style="zoom:50%;" />

修改`lib_keysFuncLogic.ahk`文件

<img src="assets\image-20220710123452918.png" alt="image-20220710123452918" style="zoom:50%;" />

### Caplocks + r 打开资源管理器

修改`lib_keysFunction.ahk`文件

<img src="assets\image-20220710123331675.png" alt="image-20220710123331675" style="zoom:50%;" />

修改`lib_keysFuncLogic.ahk`文件

<img src="assets\image-20220710123519131.png" alt="image-20220710123519131" style="zoom:50%;" />

### Caplocks + g 打开Chrome浏览器

修改`lib_keysFunction.ahk`文件

<img src="assets\image-20220710123345050.png" alt="image-20220710123345050" style="zoom:50%;" />

修改`lib_keysFuncLogic.ahk`文件

<img src="assets\image-20220710123404301.png" alt="image-20220710123404301" style="zoom:50%;" />

