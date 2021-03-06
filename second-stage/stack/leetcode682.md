## 682. 棒球比赛

**描述**

> 你现在是一场采用特殊赛制棒球比赛的记录员。这场比赛由若干回合组成，过去几回合的得分可能会影响以后几回合的得分。

比赛开始时，记录是空白的。你会得到一个记录操作的字符串列表 ops，其中 ops[i] 是你需要记录的第 i 项操作，ops 遵循下述规则：

- 整数 x - 表示本回合新获得分数 x
- "+" - 表示本回合新获得的得分是前两次得分的总和。题目数据保证记录此操作时前面总是存在两个有效的分数。
- "D" - 表示本回合新获得的得分是前一次得分的两倍。题目数据保证记录此操作时前面总是存在一个有效的分数。
- "C" - 表示前一次得分无效，将其从记录中移除。题目数据保证记录此操作时前面总是存在一个有效的分数。

**实例**

```
示例 1:
  输入：ops = ["5","2","C","D","+"]
  输出：30
  解释：
  "5" - 记录加 5 ，记录现在是 [5]
  "2" - 记录加 2 ，记录现在是 [5, 2]
  "C" - 使前一次得分的记录无效并将其移除，记录现在是 [5].
  "D" - 记录加 2 * 5 = 10 ，记录现在是 [5, 10].
  "+" - 记录加 5 + 10 = 15 ，记录现在是 [5, 10, 15].
  所有得分的总和 5 + 10 + 15 = 30

示例 2:
  输入：ops = ["5","-2","4","C","D","9","+","+"]
  输出：27
  解释：
  "5" - 记录加 5 ，记录现在是 [5]
  "-2" - 记录加 -2 ，记录现在是 [5, -2]
  "4" - 记录加 4 ，记录现在是 [5, -2, 4]
  "C" - 使前一次得分的记录无效并将其移除，记录现在是 [5, -2]
  "D" - 记录加 2 * -2 = -4 ，记录现在是 [5, -2, -4]
  "9" - 记录加 9 ，记录现在是 [5, -2, -4, 9]
  "+" - 记录加 -4 + 9 = 5 ，记录现在是 [5, -2, -4, 9, 5]
  "+" - 记录加 9 + 5 = 14 ，记录现在是 [5, -2, -4, 9, 5, 14]
  所有得分的总和 5 + -2 + -4 + 9 + 5 + 14 = 27

```

**思路**

```
1、用栈模拟当前分数
2、根据规则对栈进行操作
```

**实现**

```js
/**
 * @param {string[]} ops
 * @return {number}
 */
var calPoints = function (ops) {
  if (!ops.length) return false;

  const stack = [];

  ops.forEach((e) => {
    switch (e) {
      case "C":
        {
          if (stack.length < 1) return false;
          stack.pop();
        }
        break;
      case "D":
        {
          if (stack.length < 1) return false;
          stack.push(+stack[stack.length - 1] * 2);
        }
        break;
      case "+":
        {
          if (stack.length < 2) return false;
          stack.push(+stack[stack.length - 1] + stack[stack.length - 2]);
        }
        break;
      default:
        {
          stack.push(+e);
        }
        break;
    }
  });

  return stack.reduce((a, b) => a + b);
};
```

**实现-复杂度分析**  
`时间复杂度`：O(n)，即 ops 的长度  
`空间复杂度`：O(n)，即 stack 的长度

**官方**

```java
// java
class Solution {
  public int calPoints(String[] ops) {
    Stack<Integer> stack = new Stack();

    for(String op : ops) {
      if (op.equals("+")) {
        int top = stack.pop();
        int newtop = top + stack.peek();
        stack.push(top);
        stack.push(newtop);
      } else if (op.equals("C")) {
        stack.pop();
      } else if (op.equals("D")) {
        stack.push(2 * stack.peek());
      } else {
        stack.push(Integer.valueOf(op));
      }
    }

    int ans = 0;
    for(int score : stack) ans += score;
    return ans;
  }
}

```

**官方-复杂度分析**  
`时间复杂度`：O(n)，其中 n 是 ops 的长度。我们解析给定数组中的每个元素，然后每个元素执行 O(1) 的工作。  
`空间复杂度`：O(n)，用于存储 stack 的空间。
