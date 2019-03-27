---
title: 基于RN的安卓权限配置
date: 2019-03-25 12:26:09
tags: React
---
## 1.文档目的
基于React Native的权限配置,在开发安卓app的过程中需要访问安卓手机硬件服务的时候,都会用到权限,比如拍照,定位,手机通讯录等,这里只记录添加安卓权限的例子,ios暂不考虑

## 2.内容梳理
权限配置文件android/app/src/main/AndroidManifest.xml,添加对应权限如下:
```
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```
那么在具体逻辑中需要用到该权限时,手机就会自动询问用户是否允许开启该权限,具体逻辑如下:
```
 _getCurrentLocation = async () => {
    navigator.geolocation.getCurrentPosition(location => {
      console.log(location)
    })
  }
```
