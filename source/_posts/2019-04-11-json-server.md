---
title: json-server
date: 2019-04-11 12:14:03
tags: json-server
---
## 1.文档目的
经过实践,该方式采用本地编写JSON文件,并通过本地web服务器请求的方式来模拟请求,是一种不错的选择.另外在线版[Easy Mock](http://easymock.xys12345.cn/login)也是不错的选择.
参考网址: [json-server的使用](https://blog.csdn.net/weixin_40817115/article/details/81237128)

## 2.实践过程
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
