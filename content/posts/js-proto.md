---
title: "JavaScript 原型链"
date: 2019-01-17T00:53:15+08:00
tags: ["JavaScript"]
draft: true
---

关于 JavaScript 原型链的零碎笔记。

<!--more-->

1. 只有函数才有 `prototype` 属性
2. 每一个 JavaScript 对象都有 `__proto__` 属性（`null` 除外，虽然 `null` 也是对象），每个原型都有一个 `constructor` 属性指向关联的构造函数。
```Javascript
function Person(){};
var person1 = new Person();
person1.__proto__ === Person.prototype; //true
Person === Person.prototype.constructor; //true
Object.getPrototypeOf(person1) === Person.prototype; //true, person1这个对象的原型是 Person.prototype。
```
3. `Object.prototype` 的原型是 `null`
4. `__proto__` 是指向其 继承的类型 的 原型对象 的指针，通常也写作`[[Prototype]]`，实现继承；
`prototype` 是指向其 类型 的 原型对象 的指针，原型对象中 `constructor` 指向它的构造函数(`Constructor`)，用以继承
5. “原型”是概念，是模式，“原型对象”是实现
6. `new` 的本质：
```
var foo = new Object();
foo.__proto__ = Foo.prototype;
Foo.call(foo);
```


