---
title: ES6专题（一）
date: 2018-11-08 19:55:13
tags: 前端
---
之前一直在用ES6，一些常用的还是能说出一些，但是不全面，也不具体。现在打算花一段时间好好理一下ES6相关的东西。

## ES6的新特性

### let
let之前用的比较多，很多时候在{}内用let声明一个变量，只是在{}内使用，可以避免全局变量污染等。一直不是很明白let和var之间的区别。

#### 作用范围不同
js的作用域有： 全局作用域、函数作用域、块作用域（ES6引入）。
var定义的变量, 作用范围比较大，作用域是整个封闭函数，不可以跨函数作用域访问；
let定义的变量，作用范围比较小，属于块级作用域，即{}内，不可以跨块作用域访问。
```javascript
{
    var a = 1;
    console.log(a); // 1
}
console.log(a); // 1


(function B(){
    var b = 1;
    console.log(b); // 1
})()
console.log(b); // b is not defined    不可以跨函数作用域访问


{
    let c = 1;
    console.log(c); // 1
}
console.log(c); // 报错   c is not defined
```

当var和let同时出现的时候，有可能会相互影响。
```javascript
var a = 1;
{
  console.log(a);   // 1    
                    // {}作用域内没有a，会往外层作用域里找
                    // 此时外层作用域里a = 1;所以打印出1。
}

var b = 1;
{
  console.log(b);   // 报错 b is not defined
  let b = 2;
}
```

#### 声明提升
var 会声明提升，let不会提升。
```javascript
console.log(a); // a is is not defined
console.log(b); // undefined   b声明提升 不会报错
var b = 1;
console.log(c); // c is is not defined  let不会提升，且会报错
let c = 1;
```

#### let不能重复定义
```javascript
var a = 1;
var a = 2;
console.log(a); // 2    var 重复定义的话，后面的会覆盖前面的，并不会报错

let b = 1;
let b = 2;  // Identifier 'b' has already been declared 
            // let重复定义的话会报错
```

#### 关于闭包
关于闭包，面试的时候经常被问到。
......
闭包暂时没想好，后期再往上填吧。
### const
const 和let差不多，不允许重复赋值。
给const声明的变量重新赋值的时候会报错。
```javascript
const a = 1;
const a = 2;    // Identifier 'a' has already been declared

const b = {};
const b = {'a': 1};    // Identifier 'b' has already been declared

const c = {};
c.name = 'tom';
c.job = 'fe';
console.log(c); // {name: 'tom', job: 'fe'}
```
const声明的引用型变量，可以改变其值，只要不更改该变量在内存中的地址。

### 箭头函数
一般是这样写。
```javascript
(x, y) => {
    return x + y;
}
// 类似于
function (x, y) {
    return x + y;
}
```
用起来挺好用，比之前的function定义简便了许多。但是箭头函数还可以更简洁。
1、 当参数是一个的时候，可以不用()，当参数不是一个，就必须加()。
```javascript
// 一个参数
x => {
    return x * x;
}
// 没有参数
() => {
    
}
```
2、 当函数体内只有一条语句时，可以省略return 和{}， 当返回对象时要()包裹。
```javascript
(x, y) => x * x + y * y;

// 类似于
function (x, y) {
    return x * x + y * y;
}

(x, y) => {
    return {
        a: x,
        b: y
    }
}
// 简写为
(x, y) => ({a: x, b: y});
```
#### 箭头函数中this的指向
这个跟普通的函数不一样。普通函数谁调用我，this就指向谁。箭头函数内的this，我觉得应该是和箭头函数外部的this指向一致。
### 模板字符串



### 解析结构



### 展开运算符...



### Promise



### 对象与Class


### 模块化



