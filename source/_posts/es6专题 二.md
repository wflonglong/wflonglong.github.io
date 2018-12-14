---
layout: ES6专题
title: ES6专题 二
date: 2018-11-26 20:52:55
tags: 前端
---
Promise 模块化 对象与Class

## Promise
有三种状态，pending(进行中)、fulfilled(已完成)、 rejected(已失败)。
状态的改变只能是从pending --> fulfilled或者 pending --> rejected。

### Promise.all
```javascript
// p1 p2 p3 是3个Promise实例
let p = Promise.all([p1, p2, p3]).then(results => {
    // 当三个都为已完成状态时执行
}).catch(errors => {
    // 三个里只要有一个已失败状态时执行
});
```
### Promise.race
跟Promise.all类似，只要有一个为已完成状态，整个都是已完成。

## 模块化
1. 每一个文件都是单独的模块。通过ES6 import指令，可以在当前模块引入其它模块,想换个名字用as。
2. ES6 import命令引入的变量都是只读的，如果对其重新赋值，会报错(对象可以改变属性)。
3. ES6 import引入的是静态加载，编译时输出接口（CommonJS 模块是运行时加载）。
4. ES6 输出的是值的引用，可以取到模块内部实时的值（CommonJS 输出的是值的拷贝，不会动态更新）。
5. 支持引入一个模块的部分接口

```javascript
// ES6
import App from './App';
import { OnInit, OnDestroy } from '@angular/core';
import * as moment from 'moment';
// 引入的模块都会自动执行一次，如果只希望引入的模块只执行，不在当前模块使用，可简写
import './style.css';

// CommonJS模块
let { stat, exists, readFile } = require('fs');
```
使用export提供对外接口

## 对象与Class
ES6针对对象增加了一些简化的写法。
```javascript
// 属性和变量同名时
let name = 'jerry';
const people = {name};
// 等价于ES5
var people = {
    name: name
}
```
Class以及继承
```javascript
class City {
  constructor(city) {
     this.city = city;
  }
  sayHello() {
    return `hello,欢迎来到${ this. city}。 `;
  }
}
class People extends City {
    constructor(city, name, age) {
        super(city);
        this.name = name;
        this.age = age;
    }
}

```

后续要补充的：
ES6的Promise与JQuery的Promise
ES6模块化 和 AMD CMD
事件循环机制
执行上下文等

