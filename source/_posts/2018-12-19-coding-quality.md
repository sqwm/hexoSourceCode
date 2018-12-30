---
title: coding-quality
date: 2018-12-19 06:43:00
tags: tools
---
## 1.文档目的
一直想写一篇关于编码习惯和编码质量的博文，却一直没有动手，今天终于开启了这个课题的探究，可能这种情怀就像是一个有洁癖的人对于卫生环境的追求一样，作为一个编码人员也会对自己编写的代码有一种追求质量的情怀。可能这种追求并不是一两天或者几句话能说明白的事情，所有我会持续探究并完善这篇博文，希望可以有所帮助
参考网址：
[雅虎军规35条](https://www.jianshu.com/p/4cbcd202a591)、
[JavaScript 编码规范](https://github.com/yuche/javascript)、
[eslint规则](http://eslint.cn/docs/rules/)、
[js编码风格（阮一峰）](http://www.ruanyifeng.com/blog/2012/04/javascript_programming_style.html)
[ES6编程风格](http://es6.ruanyifeng.com/#docs/style)
## 2.心得
编程讲究章法，要心中有想法，才能动手编码，正所谓"三思而后行"，而对于编程习惯，还是要尽可能准守一些普遍认同的规则好，而不必过于吹毛求疵，因为可能很多人有不同的观点，特别是看了阮一峰老师关于“js编码风格”一文，以及下方的评论时，感触很大，故此事不可过于偏执。另外需要特别提醒的一点是现在都用es6的编程风格了，但是上线之前都应该将代码统一处理成es5
基于node开发环境转换：[Babel](https://www.jianshu.com/p/647950617a6d)
在线转换：[Babel](https://babeljs.io/repl)、[Traceur](https://google.github.io/traceur-compiler/demo/repl.html#let%20a%20%3D%20%22colbert%22)
1、前端的发展讲究"工程化"，"模块化"和"组件化"，那么我们在编码之前，清晰地了解需求之后，就要从这三个维度去考虑实现方案，
工程化：用做工程的思维看待和开发自己的项目，而不再是直接撸起袖子一个页面一个页面开写，比如规划各种规范、技术选型、项目构建优化等等
模块化：强调功能的分离同时可以复用，比如ES6 Module,less mixin等，要写一个实现A功能的JS代码，这个功能在项目其他位置也需要用到，那么我们就可以把这个功能看成一个模块采用一定的方式进行模块化编写
组件化：强调视图的复用同时需用分离，比如vue公共组件的实现，页面只不过是组件的容器，负责组合组件形成功能完整的界面
2、细节决定了编码的质量，而强有力且公认的编码习惯则决定了代码的可读性，常见的编码习惯涉及到文件命名，变量命名，标点符号，注释，代码算法结构等
## 3.编程命名规则介绍
驼峰命名法：如exampleName
帕斯卡命名法：如ExampleName
下划线命名法：如example_name
中划线命名法：如example-name
匈牙利命名法(体现类型)：如g_example_name或aExampleNames
## 3.整理实用条款
1、工程化，模块化，组件化的思想
2、项目命名使用中划线命名法,比如twitter-bootstrap
3、项目中文件夹命名使用中划线命名法：比如global-api
3、项目中文件名称命名（除特殊约定外：比如README.md）使用中划线：error-info.js
3.1、如果你的文件只输出一个类，那你的文件名必须和类名完全保持一致，比如：import CheckBox from './CheckBox'
4、类名用帕斯卡命名法：比如AdminUser{}
5、对象、函数、实例、普通变量应该使用驼峰命名法：比如getInit()
6、变量命名原则：尽可能短且体现值得类型，即普通变量更适合用匈牙利命名法
7、常量命名原则：全部大写且用下划线连接，如USER_TYPE
