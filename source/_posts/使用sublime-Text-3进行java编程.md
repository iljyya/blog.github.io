---
title: 使用sublime-Text-3进行java编程
date: 2016-05-05 09:50:12
tags: java
categories: java
---

### 实现sublime Text 3对Java编译执行
直接在安装路径下找到*\Packages\Java.sublime-package文件，用解压缩软件打开，找到JavaC.sublime-build文件，将shell_cmd中的javac改成javaRun，保存后将原压缩文件中的文件替换，如果你的sublime text 3已经打开，会报错，关闭后再次覆盖。代码如下：

	{  
	    "shell_cmd": "javaRun \"$file\"",  
	    "file_regex": "^(...*?):([0-9]*):?([0-9]*)",  
	    "selector": "source.java",  
	    "encoding":"cp936"  
	}  
<!--more-->
然后在jdk安装路径下的bin目录中新建一个javaRun.bat批处理文件，内容如下：

	@ECHO OFF  
	cd %~dp1  
	ECHO Compiling %~nx1.......  
	IF EXIST %~n1.class (  
	DEL %~n1.class  
	)  
	javac  %~nx1  
	IF EXIST %~n1.class (  
	ECHO -----------OUTPUT-----------  
	java %~n1  
	)  

之后就可以使用ctrl+B

### 若显示编译显示[Decode error - output not utf-8]
SublimeText3\Packages\Java.sublime-package\JavaC.sublime-build\
添加	 "encoding":"cp936"

### 编译显示： 编码GBK的不可映射字符【注：需要在前面的基础下】
将上述javaRun.bat修改为：

	[plain] view plain copy 在CODE上查看代码片派生到我的代码片
	@ECHO OFF  
	cd %~dp1  
	ECHO Compiling %~nx1.......  
	IF EXIST %~n1.class (  
	DEL %~n1.class  
	)  
	javac -encoding UTF-8 %~nx1  
	IF EXIST %~n1.class (  
	ECHO -----------OUTPUT-----------  
	java %~n1  
	)  

  
[原文](http://blog.csdn.net/wolinxuebin/article/details/41049551)