---
layout: ES6专题
title: ES6专题 四
date: 2018-11-28 14:46:41
tags: 前端
---
ES2016新特性  ES2017新特性
## ES2016新特性
1.[Array.prototype.includes](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
2.[Exponentiation Operator(求冥运算)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#幂_(**))
 ### Array.prototype.includes
查找一个值在不在数组中，在返回true，否则返回false。
```javascript
// 用法：
// arr.includes(searchElement)
// arr.includes(searchElement, fromIndex)
// searchElement 需要查找的元素值。
// fromIndex可以省略；
// 如果为负值，跟indexOf类似，从倒数第fromIndex个(array.length - fromIndex)开始查找；
// 如果超出数组的长度，不查找，返回false
let arr1 = ['a', 'b', 'c'];
arr1.includes('b', 1)      // true
arr1.includes('b', 2)      // false
let arr2 = [1, 2, NaN];
arr2.indexOf(NaN)        //-1
arr2.includes(NaN)       //true
```
includes 和indexOf 都是===比较的。
arr.includes(searchElement, fromIndex)基本上和arr.indexOf(searchElement, fromIndex) !== -1一样，区别在于对NaN的处理。
js里 NaN === NaN 为false。
### Exponentiation Operator(求冥运算)
```javascript
2 ** 3  // 8
// 效果同
Math.pow(2, 3) // 8
```

## ES2017新特性
1.异步函数（Async Functions）
2.共享内存和原子
3.Object.values/Object.entries
4.String padding(字符串填充)
5.Object.getOwnPropertyDescriptors
6.函数参数列表和调用中的尾逗号（Trailing commas）
