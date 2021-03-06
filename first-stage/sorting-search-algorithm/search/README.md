## 搜索算法

### 顺序搜索

**顺序搜索的定义**

> 顺序或线性搜索是最基本的搜索算法。它的机制是，将每一个数据结构中的元素和我们要找的元素做比较。顺序搜索是最低效的一种搜索算法

**顺序搜索的实现**

**[`SequentialSearch Demo`](./sequential-search.js)**

### 二分搜索

**二分搜索的定义**

> 二分搜索算法的原理和猜数字游戏类似，就是说那个人说：“我正想着一个 1 ～ 100 的数”的游戏。我们每回应一个数，那个人就会说这个数是高了还是低了还是对了。

**二分搜索的实现**

**[`BinarySearch Demo`](./binary-search.js)**

### 内插搜索

**内插搜索的定义**

> 内插算法是改良版的二分搜索。二分搜索总是检查 mid 位置上的值，而内插搜索可能会根据要搜索的值检查数组中的不同地方。

**内插搜索的实现**

**[`InterpolationSearch Demo`](./interpolation-search.js)**

### 随机算法

**随机算法的定义**

> 这个算法由 Fisher 和 Yates 创造。
> 它的含义是迭代数组，从最后一位开始并将当前位置和一个随机位置进行交换。这个随机位 置比当前位置小。这样，这个算法可以保证随机过的位置不会再被随机一次（洗扑克牌的次数越 多，随机效果越差）。

**内插搜索的实现**

**[`FisherYates Demo`](./fisher-yates.js)**
