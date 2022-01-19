# java学习笔记

[toc]

参考链接：[廖雪峰java学习](https://www.liaoxuefeng.com/wiki/1252599548343744/1255876875896416#0)

## 一、初识java

java语言是一种编译型-解释型语言，同时具备编译特性和解释特性。（**确切地说，java就是解释型语言，其所谓的编译过程只是将.java文件编程成平台无关的字节码.class文件，并不是像C一样编译成可执行的机器语言**）

java文件的执行过程：**【.java源文件】**经过**【javac命令】**编译成**【.class字节码文件】**，编译的内容用**【类加载器(class loader)】**加载到**【JVM】**里执行，这时**【执行引擎(execution engine)】**把这些文件解析成**【机器码】**，存放再JVM的**【运行数据区】**后，执行程序。

![img](https://upload-images.jianshu.io/upload_images/10948402-d0205ed9de199867)

参考链接：[解释型语言和编译型语言的区别](https://blog.csdn.net/zhu_xun/article/details/16921413)

### 1.1 JDK

JDK：Java Development Kit（java开发工具包） JDK包含了JRE

配置好环境变量后，在`JAVA_HOME`的`bin`目录下找到很多可执行文件：

- java：这个可执行程序其实就是JVM，运行Java程序，就是启动JVM，然后让JVM执行指定编译后的代码；
- javac：这是Java的编译器，它用于把Java源码文件（以`.java`后缀结尾）编译为Java字节码文件（以`.class`后缀结尾）;
- jar：用于把一组`.class`文件打包成一个`.jar`文件，便于发布；
- javadoc：用于从Java源码中自动提取注释并生成文档；
- jdb：Java调试器，用于开发阶段的运行调试。

### 1.2 运行第一个java程序

创建文件`Hello.java`

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}
```

🔴注意：文件名`Hello.java`和类名`Hello`要对应

第一步，执行命令`javac Hello.java`得到`Hello.class`文件

第二步，运行`Hello.class`，使用命令`java Hello`



## 二、java基础

### 2.1 数据类型

基本数据类型是CPU可以直接进行运算的类型。Java中的基本数据类型如下：



🔴注意：一个Java源文件可以包含多个类的定义，但只能定义一个public类，且public类名必须与文件名一致。如果要定义多个public类，必须拆到多个Java源文件中。