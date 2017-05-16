---
title: React Native 从入门到踩坑
date: 2017-03-13 03:50:12
tags: React Native
categories: React Native
---
### Get started.
http://reactnative.cn/docs/0.42/getting-started.html#content

### Forum
http://bbs.reactnative.cn/category/4/求助专区
### Q: gradle download slow.
A: copy and download link like:
https://services.gradle.org/distributions/gradle-2.14.1-all.zip
put zip in`C:\Users\Administrator\.gradle\wrapper\dists\gradle-2.14.1-all\8bnwg5hd3w55iofp58khbp6yv`
B:freeGate http://www.cnblogs.com/zhang-cb/p/6065118.html
C: `app\gradle.properties`add
```java
systemProp.http.proxyHost=android-mirror.bugly.qq.com
systemProp.http.proxyPort=8080
org.gradle.jvmargs=-Xmx2048m -XX\:MaxPermSize\=512m -XX\:+HeapDumpOnOutOfMemoryError -Dfile.encoding\=UTF-8
org.gradle.parallel=true
target-sdk=23
```
read more: http://hucaihua.cn/2015/06/06/android_studio_problem/

### Q: sdk not defined
sys env var add`%ANDROID_HOME%`
path add`%ANDROID_HOME%;%ANDROID_HOME%\platform-tools;
`

### Q: copy in cmd
标记 选中 回车

### Q: Could not create ADB Bridge
settings-ADB-Use custom SDK tools.
Restart genymotion
read more: http://stackoverflow.com/questions/35959350/react-native-android-genymotion-adb-server-didnt-ack

### Q: adb wifi
1 usb connect, enable USB Debugging
2 cmd `adb tcpip 5555`
3 `adb connect 192.168.1.***`
back to usb mode: `adb usb`
show devices: `adb devices`
stop adb wifi:`adb tcpip -1`
adb wifi 不稳定


### Q: failed to install all/ Unable to upload some APKs (真机测试)
`android/build.gradle`change version to `1.2.3`
change `ProjectDir\android\gradle\wrapper\gradle-wrapper.properties` 
url to `gradle-2.2-all.zip`
cmd `adb reverse tcp:8081 tcp:8081`
read more: http://blog.csdn.net/yk377657321/article/details/53036788

### Q:开启Gradle Daemon
dir `.gradle` 
creat file `gradle.properties`
add`org.gradle.daemon=true `

#### Q: 官网找不到Genymotion下载，提示收费。
先登录，点下载，滑到下面就有了。

### Q: Genymotion: Unable to create Virtual Device: Connection timeout.
A: Check the /home/user/.Genymobile/Genymotion/genymotion.log file and at last 10 lines of the file you will get somthing like this:
http://dl.genymotion.com/dists/6.0.0/ova/genymotion_vbox86p_6.0_160825_141918.ova
download and put this image file to /home/user/.Genymobile/Genymotion/ova/ and restart Genymotion and add this device.
参考链接： http://stackoverflow.com/questions/19700646/unable-to-create-genymotion-virtual-devicesconnection-timeout



### Q:error:device offline
重启模拟器，实在不行就：
`adb kill-server`
adb start-server
adb remount`

### Q:真机测试始终白屏
手机设置，项目APP开启`桌面悬浮窗`权限

### Q:真机摇一摇没反应
手机设置，项目APP开启`桌面悬浮窗`权限
