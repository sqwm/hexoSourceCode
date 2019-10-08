---
title: json
date: 2019-04-11 12:14:03
tags: JS
---
## 1.文档目的
汇总前端JSON数据模拟技术,本文介绍三种技术:**json server, Easy mock, github api v3**.
json server: 该方式采用本地编写JSON文件,并通过本地web服务器请求的方式来模拟请求
Easy Mock: 在线json模拟数据生成管理平台
github api v3:获取并操作github账号下个人相关信息的接口服务
实际上获取网络接口和网络图片资源的方式比较灵活,比如随便在网络上打开开发模式都可以看到get请求,而且get接口链接直接在浏览器中打开就可以获得数据,图片资源更简单,百度搜索的图片,单击右键就可以获得图片链接,直接在浏览器中打开图片链接就可以看到图片资源.
参考网址: [json-server的使用](https://blog.csdn.net/weixin_40817115/article/details/81237128),[Easy Mock官网](http://easymock.xys12345.cn/login),[github api讲解](https://segmentfault.com/a/1190000015144126?utm_source=tag-newest#articleHeader0),[github api官方文档](https://developer.github.com/)

## 2.实践过程
### 2.1 json server
安装依赖
```
npm install -g json-server
```
查看版本
```
json-server -v
```
创建db.json
```
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```
启动服务
```
json-server db.json
```
在postman或浏览器中访问接口,比如:
```
http://localhost:3000
```
### 2.2 East Mock
只需要打开[East Mock官网](http://easymock.xys12345.cn/login),登录账号并编辑JSON数据,然后用浏览器,postman,axios等请求即可

### 2.3 github api
该方式请求的接口由github官方提供服务,数据是个人行为在github平台上产生的真实数据,下面仅列出实用接口,便于调用
**用户信息[详情信息]**
```
https://api.github.com/users/ruanyf
```
**列表信息[分页/不分页]** 
```
https://api.github.com/users/ruanyf/followers?page=1&per_page=10
```
**占位图**
```
http://temp.im/288x288
```