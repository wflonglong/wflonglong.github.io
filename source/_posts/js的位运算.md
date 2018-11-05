---
title: js的位运算
date: 2018-11-04 13:38:20
tags:
---
大学里学的位运算，工作中一直没有用到过，没想到最近项目中需要用位运算。

### 按位与（&）
和&& 运算符一样，同时为真的时候才为真。&是同时为1的时候才为1。

```
 0 & 0 = 0；
 1 & 0 = 0；
 1 & 1 = 1；
 true & 1 = 1;
 2 & 3      0010
          & 0011
          ------
            0010  2
```
### 按位或（|）
| 和 || 类似，只要有一个为真（1)，结果为真(1)。
```
1 | 0 = 1;
```
### 按位非（~）
按位取反 
> 0 -> 1  
> 1-> 0

```
var a = 15; // 00001111
var b = ~a; // 11110000     -16
//负数二进制转化为十进制，最高位符号位不变，其余位置取反，最后加1
11110000  -> 1 0001111 -> 1 0010000 -> -16

```

### 按位异或（^）
按位异或 只有一个为1的时候才为1，其余都为0

### 有符号左移 (<<) 和  有符号右移（>>>）
左移n位可以理解为乘以2的n次方，
右移n位可以理解为除以2的n次方
```
3左移3位 = 3 * 8 = 24
        0011 << 3
     0011000
      = 24
25右移2位 = 25 / 4 = 6.25
    0011001 >> 2
        110.01
        = 6.25
```
### 项目中用到的方法

```javascript
    /**
     * 获取int数字某一位的比特值
     * @param number int数字
     * @param index 0-31
     * @returns {number} 0 or 1
     */
    function getBitByIndex(number, index) {
        try {
            return number >> index & 1;
        } catch (error) {
            throw error;
        }
    }

    /**
     * 设置数字某一位的比特值
     * @param number
     * @param index
     * @param value 0 or 1
     */
    function setBitByIndex(number, index, value) {
        try {
            if (value) {
                return number | 1 << index;
            } else {
                return number & ~(1 << index);
            }
        } catch (error) {
            throw error;
        }
    }
    /**
     * 将int数字某一位的比特值设置为1
     * @param number
     * @param index
     * @returns {number}
     */
    function setBitOfIndex(number, index) {
        try {
            return number | 1 << index;
        } catch (error) {
            throw error;
        }
    }

    /**
     * 将int数字某一位的比特值设置为0
     * @param number
     * @param index
     * @returns {number}
     */
    function unsetBitOfIndex(number, index) {
        try {
            return number & ~(1 << index);
        } catch (error) {
            throw error;
        }
    }
```