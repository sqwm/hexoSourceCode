---
title: coding-quality
date: 2018-12-19 06:43:00
tags: JS
---
## 1.文档目的
一直想写一篇关于编码习惯和编码质量的博文，却一直没有动手，今天终于开启了这个课题的探究，可能这种情怀就像是一个有洁癖的人对于卫生环境的追求一样，作为一个编码人员也会对自己编写的代码有一种追求质量的情怀。可能这种追求并不是一两天或者几句话能说明白的事情，所有我会持续探究并完善这篇博文，希望可以有所帮助
参考网址：
[雅虎军规35条](https://www.jianshu.com/p/4cbcd202a591)、
[Github编码规范](http://alloyteam.github.io/CodeGuide/)、
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
## 4.代码开发和维护
好的代码设计架构，是易于维护的（易于修改，易于扩展），
首次开发新功能时就应该注重设计原则并写出高质量代码，及时做好注释必不可少

代码维护原则：
老业务不合理[在确保该代码模块在其他模块不受影响下，可以直接修改原代码，否则应按新需求原则进行]
新需求[尽量不要改动原代码，做好注释]
（1）尽量通过继承，适配器，桥接等模式，装饰者模式，外观模式，代理模式，组合模式，代码复用模式等方式扩展新需求
（2）必须在源代码上修改：做好代码隔离if等

注:实现一个逻辑的时候，尽量思考把内容写到公共配置中去，要便于维护，要便于扩展，要独立不依赖.当意识到两个地方及以上的地方都要用到同样的代码的时候，就要考虑是否需要提取出来了.
实现设计一个逻辑的时候，先别急着写，要设计，要思考怎样尽可能的封装组件
在写Dom的时候尽可能避免无意义陈列，如“我的”模块，而用for循环出来会更好，类比其他所有的dom,避免无意义陈列很重要,不要看得大面积Dom代码，而是封装组合，可能更合适(jsx思想)

## 5.实用命名举例
变量命名：推荐使用与业务逻辑不相关的通用命名法
布尔类型
场景一：表示可见性、进行中的状态
```
{
  isShow: '是否显示',
  isVisible: '是否可见',
  isLoading: '是否处于加载中'
}
```
场景二：属性状态类
```
{
  disabled: '是否禁用',
  editable: '是否可编辑',
  clearable: '是否可清除',
  readonly: '只读',
  checked: '是否选中',
  clickable: '是否可点击'
}
```
场景三：配置类、选项类
```
{
  withTab: '是否带选项卡',
  enableFilter: '开启过滤',
  allownCustomScale: '允许自定义缩放',
  shouldClear: '是否清除',
  canSelectItem: '是否能选中元素',
  checkJs: '检查Js',
}
```
函数类型
场景一：事件处理函数
```
{
  onXxClick // 原生事件
  onSubmit // 提交
  handleXx // 自定义事件
  closedEvent // 关闭事件
  selectAll // 选则所有
}
```
场景二：异步(围绕增删改查)
```
{
  fetchToken // 直接取自异步
  getUsers // 可能处理加工后
  createAccount // 创建新对象
  addUsr // 向已有列表中新增
  deleteUser // 删除数据
  removeTag: // 移除某事物，而并不一定会删除
  updateUsrInfo // 更新
  res // 异步返回值
}
```
场景三：路由跳转
```
{
  goXx // 跳转
  switchTab // tab切换
}
```
场景四：框架相关
```
{
  timeFilter // 过滤器
  storeCtrl // 控制器
  userFactory // 工程方法
  getXxByYy // 获取Dom节点
  formatXx // 格式化数据
  toggleXx // 切换
  sliceXx // 截取
  sortByXx // 排序
}
```
场景五：业务相关
```
{
  users // 用户列表
  xxList // XX列表
  item/option/key/index // 单项
  i/j/k/m/n/x/y/z // 循环相关
  id // 唯一标识
  key // 唯一标识
  index // 下标
  children // 子节点
  name // 名称
  title // 标题
  desc // 描述
  label // 显示名称
  value // 对应值
  tempData // 临时数据
  oldVal/newVal // 新旧
  from/to // 从...到...
  prev/cur/next // 上一个当前和下一个
  str // 字符串
  n // 次数
  reg // 正则
  count // 数量
  src // 源头
  func // 函数
  size // 大小
  start/end 开始结束
  startDate //开始日期
  endDate //结束日期
  startTime //开时时间
  endTime //结束时间
}
```
场景六：选中项
```
{
  activeTab //当前选中选项卡
  currentPage // 当前页
  selectedData // 选中项
}
```
场景七：常量状态
```
{
  LOAD_SUCCESS
  LOAD_FAIL
}
```
