---
title: echarts重新加载数据没有绘出图
date: 2019-03-19 15:02:26
tags: echarts
---
最近接手了一个老项目，AngularJS的，有点小郁闷！从Angular7一下子跌到Angular 1！有点不习惯，稍微抱怨一下。

刚接手就发现一个坑，之前用Echarts还没碰到过。

改变搜索条件，重新加载数据，Echarts却不出现，也不报错！

后来查了一下，Echarts渲染的时候会在div容器上生成一个_echarts_instance_属性，如果_echarts_instance_的值没有变化，但是div容器内部的结构发生改变，则会导致不能绘出图；如果_echarts_instance_的值发生改变，则Echarts会重新绘图。

解决改变数据不能绘出图：
1、 不改变div内部的结构
2、 触发_echarts_instance_的值的改变
```javascript
document.getElementById('Echarts容器的ID').setAttribute('_echarts_instance_', '');
// 或者
document.getElementById('Echarts容器的ID').removeAttribute('_echarts_instance_');
```

查看了一下原来的代码逻辑，发现在获取数据之后，破坏了div的的结构，导致改变数据后没有绘出图。
```javascript
// $('#echarts-box').html('');  // 破坏echarts结构，导致重新加载数据没有绘出图
// $('#echarts-box').removeAttr('_echarts_instance_');  // 解决重新加载数据没有绘出图
// $('#echarts-box').attr('_echarts_instance_', '');  // 解决重新加载数据没有绘出图
```
