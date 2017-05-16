---
title: java开发微信公众平台 从入门到踩坑
date: 2016-03-22 03:50:12
tags: tomcat
categories: tomcat
---
### 找教程

![](http://upload-images.jianshu.io/upload_images/49483-a1f2ca0bfa8b8894.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### eclipse
发现需要服务器地址，想到要eclipse的tomcat的服务器，得先下载个eclipse，老规矩，搜

![](http://upload-images.jianshu.io/upload_images/49483-03091f4babce75ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
下载安装 eclipse-javaEE
### tomcat
安装完eclipse发现需要装tomcat，搜

![](http://upload-images.jianshu.io/upload_images/49483-2301ea2525d462c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
装了个tomcat7，看教程打个hello world，run server 挺顺利。

### tomcat端口改成80
看微信文档，需要80端口，tomcat默认是8080，搜

![](http://upload-images.jianshu.io/upload_images/49483-0d0959b3d67269d8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/49483-442269aa3c97718d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在 tomcat-dir\conf\server.mxl  http port 改成 80，run server，还是8080！
不能慌，接着往下看，发现无名大侠的奇效偏方。

![](http://upload-images.jianshu.io/upload_images/49483-724e26d5e03af7f6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
