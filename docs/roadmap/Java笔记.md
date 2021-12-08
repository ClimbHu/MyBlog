# Java笔记
> 我静静的看着你装逼

## 基础

### Java 语言概述

基础常识

软件：即一系列按照特定顺序组织的计算机数据和指令的集合。分为：系统软件 和 应用软件   
- 系统软件：windows , mac os , linux ,unix,android,ios,....  
- 应用软件：word ,ppt,画图板,...

人机交互方式： 图形化界面  vs  命令行方式
- 图形化界面（Graphical User Interface GUI）：这种交互方式简单直观易上手。
- 命令行方式（Command Line Interface CUI）：需要一个控制台，输入特定的指令，让计算机完成一些操作。较麻烦，需记住一些指令。

图形化界面发展：施乐（公司） — 苹果 — 微软应用

程序 = 算法 + 数据结构

常用 DOS 命令：

计算机语言的发展迭代史
- 第一代：机器语言
- 第二代：汇编语言
- 第三代：高级语言
	- 面向过程：C,Pascal、Fortran
	- 面向对象：Java,JS,Python,Scala,...
	- Pascal：主要用于编程教学
	- Fortran：公式翻译，广泛用于科学和数学应用
	- 易语言：以中文作为程序代码编程语言

流行编程语言排行: https://www.tiobe.com/tiobe-index/

TIOBE 是一个流行编程语言排行。每月更新。排名权重基于世界范围内工程师的数量，课程数量和第三方供应商数量。Google Bing Yahoo！Wikipedia Amazon YouTube 和百度这些主流的搜索引擎，也将作为排名权重的参考指标。
声明：TIOBE 排名既无关最好的的语言，也无关被书写了最多代码的编程语言。

Java 语言版本迭代概述

	* 1991年 Green 项目，开发语言最初命名为 Oak (橡树)
	* 1994年，开发组意识到 Oak 非常适合于互联网
	* 1996年，发布 JDK 1.0，约8.3万个网页应用Java技术来制作
	* 1997年，发布 JDK 1.1，JavaOne 会议召开，创当时全球同类会议规模之最
	* 1998年，发布 JDK 1.2，同年发布企业平台J2EE
	* 1999年，Java分成J2SE、J2EE和J2ME，JSP/Servlet技术诞生
	* 2004年，发布里程碑式版本：JDK 1.5，为突出此版本的重要性，更名为JDK 5.0
	* 2005年，J2SE -> JavaSE，J2EE -> JavaEE，J2ME -> JavaME
	* 2009年，Oracle公司收购SUN，交易价格74亿美元
	* 2011年，发布JDK 7.0
	* 2014年，发布JDK 8.0，是继JDK 5.0以来变化最大的版本
	* 2017年，发布JDK 9.0，最大限度实现模块化
	* 2018年3月，发布JDK 10.0，版本号也称为18.3
	* 2018年9月，发布JDK 11.0，版本号也称为18.9

Java 是 SUN (Stanford University Network，斯坦福大学网络公司 ) 1995年推出的一门高级编程语言。

Java语言应用的领域：

> Java Web开发：后台开发
> 
>  大数据开发：
>  
>  Android 应用程序开发：客户端开发

Java语言的特点
> 面向对象性：
 	两个要素：类、对象
 	三个特征：封装、继承、多态
>
> 健壮性：
 	① 去除了C语言中的指针 
 	② 自动的垃圾回收机制 
> 仍然会出现内存溢出、内存泄漏
> 
> 跨平台型：write once,run anywhere: 一次编译，到处运行
> 
> 功劳归功于：JVM


### 第一个 Java 程序

开发体验 —— HelloWorld

编写
创建一个 java 源文件：HelloWorld.java
class HelloChina{
     public static void main(String[] args){
           System.out.println("Hello,World!");
     }
}
编译：
javac HelloWorld.java
运行：
java HelloChina

常见问题的解决


总结第一个程序
    java 程序编写-编译-运行的过程
    编写：我们将编写的 java 代码保存在以 ".java" 结尾的源文件中
    编译：使用 javac.exe 命令编译我们的 java 源文件。格式：javac 源文件名.java
    运行：使用 java.exe 命令解释运行我们的字节码文件。 格式：java 类名
    在一个 java 源文件中可以声明多个 class。但是，只能最多有一个类声明为 public 的。
    而且要求声明为 public 的类的类名必须与源文件名相同。
    程序的入口是 main() 方法。格式是固定的。
    输出语句：
    System.out.println(): 先输出数据，然后换行
    System.out.print(): 只输出数据
    每一行执行语句都以";"结束。
    编译的过程：编译以后，会生成一个或多个字节码文件。字节码文件的文件名与 java 源文件中的类名相同。

Java 严格区分大小写，Windows 不区分大小写，不能同时创建 class 和 CLASS 文件。

### 开发环境搭建

开发环境的搭建（重点）

JDK、JRE、JVM 的关系 JDk，JRE，JVM 三者之间的关系，以及 JDK、JRE 包含的主要结构有哪些    	包含关系    
	JDK = JRE + Java的开发工具（javac.exe,java.exe,javadoc.exe等）    
	JRE = JVM + Java核心类库
JDK  的下载、安装
	下载：官网：www.oracle.com	github
	安装：傻瓜式安装：JDK 、JRE   
	注意问题：安装软件的路径中不能包含中文、空格。JDK 中目录解释：
    - bin：Java 开发工具包。包含 .javac、.java、.javadoc 等。
	2. db：Java 数据库。
	3. include：一些 C 语言的头文件。
	4. jre：Java 运行环境。
	5. lib：jar 包，不懂。
	6. src.zip：开源的代码，常见的类库。

path 环境变量的配置
	为什么配置 path 环境变量？
		path 环境变量：windows 操作系统执行命令时所要搜寻的路径
	为什么要配置 path ？
		希望 java 的开发工具（javac.exe,java.exe)在任何的文件路径下都可以执行成功	
	为了任何环境（盘符）下运行 Java 工具。    
		目的是为了在控制台的任何文件路径下，都可以调用 jdk 指定目录下的所有指令。
	

	如何配置？    
		JAVA_HOME = bin的上一层目录。    
		
	path = %JAVA_HOME%\bin 常用的命令行操作有哪些？（至少4个）    
		javac.exe 编译命令、java 运行class 字节码文件的命令、cd 进入下一层命令、cd..返回上一层、del 删除文件、rd 删除文件夹    
		md 新建文件夹、dir 列出当前目录下的文件与及文件夹、cd\ 或cd/ 退回到根目录、exit 退出dos 命令行    
	Delete 和 Backspace 删除字符


## 面向对象

## 数组

## 异常

## 集合

## IO

## 并发

## 多线程

## 泛型

## 反射

## 动态代理

## Java 8 新特性

## Java 9 & 10 & 11  新特性