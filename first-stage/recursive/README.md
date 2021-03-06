## 递归

### 递归

**递归的定义**

> `要理解递归，首先要理解递归。` 递归是一种解决问题的方法，它从解决问题的各个小部分开始，直到解决最初的大问题。递归通常涉及函数调用本身。

如：

```js
// 直接或间接调用本身都是递归函数
function recursiveFn(args) {
  if (args === true) {
    // 基线条件（停止点）
    return false;
  }
  recursiveFn(args);
}
```

- 每个递归函数都必须有基线条件，即一个不再递归调用的条件（停止点），以防无限递归。

### 著名递归算法

**计算一个数的阶乘**

> 数 n 的阶乘，定义为 n！，表示从 1 到 n 的整数的乘积。
> 例如：5 的阶乘表示 5！，和 5 x 4 x 3 x 2 x 1 相等，结果是 120

**数的阶乘实现**

**[`Factorial Demo`](./factorial.js)**

**斐波那契数列**

> 斐波那契数列是另一种可以用递归解决的问题。它是由 0、1、1、2、3、5、8、13、21、34 等数组组成的序列。数 2 由 1+1 得到、数 3 是由 1+2 得到、数 5 是由 2+3 得到，以此类推（这个数列从第 3 项开始，每一项都等于前两项之和。在数学上，斐波纳契数列以如下被以递归的方法定义：F(1)=1，F(2)=1, F(n)=F(n-1)+F(n-2)（n>=3，n∈N\*））

> 斐波那契数列的定义如下：
> 1、位置 0 的斐波那契数是 0
> 2、1 和 2 的斐波那契数是 1
> 3、n（此处 n > 2）的斐波那契数是（n - 1）的斐波那契数加上（n - 2）的斐波那契数

**斐波那契数的实现**

**[`Fibonacci Demo`](./fibonacci.js)**
