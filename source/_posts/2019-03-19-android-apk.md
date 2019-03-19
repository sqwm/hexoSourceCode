---
title: 基于React Native的android打包
date: 2019-03-19 12:39:12
tags: tools
---
## 1.文档目的
打包生成apk安装包配置历来比较复杂,这里简单记录入门配置,方便查看.
打包IOS，需要有打包证书支持,这里先不做探究.
打安卓包，默认初始化的RN项目，不修改任何配置的情况下，首次打包会下载很多依赖，而且会提示成功，但是并不会打包出apk安装包。经过以下配置之后，可以打包成功，并运行成功。

## 2.内容梳理
步骤一:配置android/app/build.gradle文件,如图一所示
{% asset_img image001.png this is first image %}
<center>**图（1）**</center>
```
 signingConfigs {
        release {
            storeFile file(MYAPP_RELEASE_STORE_FILE)
            storePassword MYAPP_RELEASE_STORE_PASSWORD
            keyAlias MYAPP_RELEASE_KEY_ALIAS
            keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
 }

signingConfig signingConfigs.release
```
步骤二:配置android/gradle.properties文件,如图二所示
{% asset_img image002.png this is first image %}
<center>**图（2）**</center>
```
MYAPP_RELEASE_STORE_FILE=my-release-key.keystore

MYAPP_RELEASE_KEY_ALIAS=my-key-alias

MYAPP_RELEASE_STORE_PASSWORD=123456789

MYAPP_RELEASE_KEY_PASSWORD=123456789
```
步骤三:在android/app/文件夹下添加key文件
[my-release-key.keystore 提取码: ncpe](https://pan.baidu.com/s/1CLeFVOgJJfrXUh6Ydo05yA)
