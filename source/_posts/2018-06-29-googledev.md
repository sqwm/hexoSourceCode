---
title: 开发者工具
date: 2018-06-29 20:49:28
tags: tools
---
## 1.Elements
ctrl+shift+c		选取dom元素
ESC				在Elements面板可以用打开Console
在Elements元素面板中可以通过键盘方向键折叠和向上向下快速选择节点,
同时面包屑导航会给出层级结构,
按住并拖动节点可以移动节点位置,
查看元素事件侦听器,选中对应元素,打开Elements->Event Listeners,进一步打开对应选择器后,在handler上单击右键选择show function definition,可以查看具体方法定义,
单击节点,右键Break on可以为节点添加Dom事件监听,在Elements->DOM Breakpoints面板可以查看详情,
鼠标悬停在Elements->Styles面板对应css名称上可以查看受影响的Dom,
在对应css右下角有小图标可以调整颜色和阴影,
编辑数字和css属性值时,可以使用键盘箭头增大缩小,也可以使用鼠标滚轮,
Ctrl+点击任何css属性可以直接跳转至对应文件相应行
## 2.Console
提供了一个命令行接口，用来与网页代码互动。
F12				打开DevTools
ctrl+shift+J		打开控制台并定位光标
ctrl+L			清空控制台
console.log('aaa');
console.info('aaa');
console.error('aaa');
console.warn('aaa');
分组日志
console.group('aaa');
console.log('我是aaa小组的日志');
console.groupEnd();
断言日志
console.assert(false,'当第一个参数为false时输出该条消息');
统计执行次数日志
function myFun(){
	console.count('myFun被执行的次数');
}
myFun();
myFun();
输出对象的属性和方法
console.dir(document.body);
统计代码执行时间
console.time("Array initialize");
var array=new Array(1000000);
for(var i=array.length - 1;i>=0;i--){
	array[i] = new Object();
};
console.timeEnd("Array initialize");
查看代码执行对cpu的使用情况
console.profile("Array initialize");
var array=new Array(1000000);
for(var i=array.length - 1;i>=0;i--){
	array[i] = new Object();
};
console.profileEnd("Array initialize");
执行完成后在Profiles面板里面查看就可以看到cpu相关使用信息
复制选中的DOM结构至剪切板
copy(document.body);
输出对象的键或值对
var myObj = {name:'xiaoming',sex:'female'};
keys(myObj);
values(myObj);
用表格样式输出json格式数组
var myArray = [{"name":"xiaoming"},{"sex":"12"}];
console.table(myArray);

console.log('%c This text is styled!',
  'color: red; background: yellow; font-size: 24px;'
)

var number = 11 * 9;
var color = 'red';
console.log('%d %s balloons', number, color);

%s 字符串
%d 整数
%i 整数
%f 浮点数
%o 对象的链接
%c CSS格式字符串

debugger
