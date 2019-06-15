---
title: prototype原型链与构造函数法模拟类
date: 2019-06-15 12:06:28
tags: JS
---
## 1.概念
原型链：如果在第一个对象上没有找到需要的属性或方法，引擎就会继续在prototype关联的对象上继续查找。

## 2.理论探究
{% asset_img image001.jpg this is first image %}
<center>**图（1）**</center>
1.在JS里，万物皆对象。方法（Function）是对象，方法的原型(Function.prototype)是对象。因此，它们都会具有对象共有的特点。即：对象具有属性__proto__，可称为隐式原型，一个对象的隐式原型指向构造该对象的构造函数(简单理解为“父类”)的原型prototype，这也保证了实例能够访问在构造函数原型(简单理解为“父类”)中定义的属性和方法。
2.方法(Function)这个特殊的对象，除了和其他对象一样有上述_proto_属性之外，还有自己特有的属性——原型属性（prototype），这个属性是一个指针，指向一个对象，这个对象的用途就是包含所有实例共享的属性和方法（我们把这个对象叫做原型对象prototype）。原型对象也有一个属性，叫做constructor，这个属性包含了一个指针，指回原构造函数。
小结：
对象有属性__proto__,指向该对象的构造函数(简单理解为“父类”)的原型对象prototype。
方法除了有属性__proto__,还有属性prototype，prototype指向该方法的原型对象(所有实例共享的属性和方法)
3.模拟类：首先要明确面向对象语言中，对象实例化和继承都是通过“复制”实现的，即各个实例之间没有关联关系。
但是js中（var a= new Foo()）new[带new的函数调用被称为“构造函数调用”]一个新对象实际发生的却是将新对象a的_proto_属性指向Foo.prototype（同时：a.constructor === Foo === Foo.prototype.constructor）,即各个实例共享了属性和方法，相互之间建立了关联关系。
4.模拟继承（也叫“原型继承”）：实质是创建两个对象（父子）之间的关联关系，使得一个对象（子）可以通过委托访问另一个对象（父）的属性和函数，核心是apply()方法的应用
小结：
对象有属性constructor,指向的是对象关联的函数（Foo父类）[实质上是a.constructor === Foo.prototype.constructor]
new实例化的实质："构造函数"会被调用，而绑定在prototype属性上的公共属性和方法会和实例的_proto_属性建立关联关系

实例：构造函数法模拟继承分析
```
  // 父类
    function Animal(species){
       //实例化对象的过程中会通过new调用该“构造函数”执行，即初始化
       //即：每个实例都会产生属于自己的species属性
　　　　this.species = species;
　　}
    // 子类:注意将父类需要的属性放前面，方便arguments正确对应
　　function Cat(species,name){
        Animal.apply(this, arguments); //通过apply方法将父类绑定到自身环境
　　　　this.name = name;
　　}
  // 公共的不变的属性和方法直接绑定至prototype
    // 即：prototype不属于构造函数，不会在new是被调用，而会被各个实例所共享
    Cat.prototype.sound = "喵喵喵...";
    Cat.prototype.eat = function(){console.log('猫爱吃鱼')};

    //new调用实质：cat1.constructor = Cat.prototype.constructor，则产生不同的species实例变量
    //同时：cat1._proto_ = Cat.prototype,保证了所有实例可以调用共享的绑定在prototype上的属性和方法
　　var cat1 = new Cat("动物","大毛"); 
    //调用
    console.log(cat1.species, '---我是继承父类的属性')
    console.log(cat1.sound, '---我是绑定在子类prototype上的公用属性')
```
