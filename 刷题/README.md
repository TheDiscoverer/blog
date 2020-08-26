## 栈
经常考察
1. 单调栈
2. 利用栈实现队列
3. 计算包括逆波兰表达式计算和普通计算，前者需要一个栈，后者两个栈。

- [递归函数和栈逆序一个栈](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E7%94%A8%E9%80%92%E5%BD%92%E5%87%BD%E6%95%B0%E5%92%8C%E6%A0%88%E9%80%86%E5%BA%8F%E4%B8%80%E4%B8%AA%E6%A0%88.md)
应该只能强行记住这个解法了，func利用逆转栈，其中需要getAndRemove()来获取栈底元素。

- [基本计算器II](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E5%9F%BA%E6%9C%AC%E8%AE%A1%E7%AE%97%E5%99%A8II.md)

- [柱状图中最大的矩形](https://github.com/TheDiscoverer/blog/blob/master/刷题/柱状图中最大的矩形.md)
先使用暴力方法，找到每个矩形左边和右边最近较小的矩形。然后使用单调栈的方法，在遍历数组元素时存储每个矩形左边的最近较小矩形。

- [逆波兰表达式求值](https://github.com/TheDiscoverer/blog/blob/master/刷题/逆波兰表达式求值.md)

## 动态规划
对于动态规划类型的题，大致分为两种。
1、将一个大问题转化成多个完全相同的子问题解决。子问题dp[i] 根据dp[0,...,i - 1]求出来，比如最低票价，三角形的最小路径和，硬币问题。这里状态转移方向分两种，正方向和逆方向，经常会有些状态转移是逆方向。
- 正方向：dp[i]根据dp[0],...,dp[i - 1]求得。
- 逆方向：dp[i]根据dp[i + 1],...,dp[n]计算求得。比如最低票价，新21点等。

2、状态转化问题，例如买卖股票问题，打家劫舍。每天都会有多种状态，根据前一天的状态转化过来。买卖股票每天有多种状态，持有股票，卖出股票，不持有股票。打家劫舍中，对于第i家可以抢劫也可以不抢劫，抢劫的话前一家不能抢劫。

- [未排序数组中累加和为给定值的最长子数组系列问题补2](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E6%9C%AA%E6%8E%92%E5%BA%8F%E6%95%B0%E7%BB%84%E4%B8%AD%E7%B4%AF%E5%8A%A0%E5%92%8C%E4%B8%BA%E7%BB%99%E5%AE%9A%E5%80%BC%E7%9A%84%E6%9C%80%E9%95%BF%E5%AD%90%E6%95%B0%E7%BB%84%E7%B3%BB%E5%88%97%E9%97%AE%E9%A2%98%E8%A1%A52.md)

- [未排序数组中累加和为给定值的最长子数组系列问题](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E6%9C%AA%E6%8E%92%E5%BA%8F%E6%95%B0%E7%BB%84%E4%B8%AD%E7%B4%AF%E5%8A%A0%E5%92%8C%E4%B8%BA%E7%BB%99%E5%AE%9A%E5%80%BC%E7%9A%84%E6%9C%80%E9%95%BF%E5%AD%90%E6%95%B0%E7%BB%84%E9%95%BF%E5%BA%A6.md)

- [换钱的最少货币数](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E6%8D%A2%E9%92%B1%E7%9A%84%E6%9C%80%E5%B0%91%E8%B4%A7%E5%B8%81%E6%95%B0.md)

- [未排序数组中累加和小于或等于给定值的最长子数组长度](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E6%9C%AA%E6%8E%92%E5%BA%8F%E6%95%B0%E7%BB%84%E4%B8%AD%E7%B4%AF%E5%8A%A0%E5%92%8C%E5%B0%8F%E4%BA%8E%E6%88%96%E7%AD%89%E4%BA%8E%E7%BB%99%E5%AE%9A%E5%80%BC%E7%9A%84%E6%9C%80%E9%95%BF%E5%AD%90%E6%95%B0%E7%BB%84%E9%95%BF%E5%BA%A6.md)

- [不同路径 II](https://github.com/TheDiscoverer/blog/blob/master/刷题/不同路径%20II.md)

- [三角形最小路径和](https://github.com/TheDiscoverer/blog/blob/master/刷题/三角形最小路径和.md)

- [最低票价](https://github.com/TheDiscoverer/blog/blob/master/刷题/最低票价.md)

- [打家劫舍 II](https://github.com/TheDiscoverer/blog/blob/master/刷题/打家劫舍%20II.md)

- [单词拆分](https://github.com/TheDiscoverer/blog/blob/master/刷题/单词拆分.md)

- [整数拆分](https://github.com/TheDiscoverer/blog/blob/master/刷题/整数拆分.md)

- [硬币](https://github.com/TheDiscoverer/blog/blob/master/刷题/硬币.md)

- [摆动序列](https://github.com/TheDiscoverer/blog/blob/master/刷题/摆动序列.md)

- [最佳买卖股票时机含冷冻期](https://github.com/TheDiscoverer/blog/blob/master/刷题/最佳买卖股票时机含冷冻期.md)

- [连续子数组](https://github.com/TheDiscoverer/blog/blob/master/刷题/连续的子数组和.md)

- [丑数](https://github.com/TheDiscoverer/blog/blob/master/刷题/丑数.md)

- [新21点](https://github.com/TheDiscoverer/blog/blob/master/刷题/新21点.md)

- [等差数列划分](https://github.com/TheDiscoverer/blog/blob/master/刷题/等差数列划分.md)

两者区别在于子数组要求连续，而子序列不要求，导致动态方程组不一样
- [最长重复子数组](https://github.com/TheDiscoverer/blog/blob/master/刷题/最长重复子数组.md)

- [最长公共子序列](https://github.com/TheDiscoverer/blog/blob/master/刷题/最长公共子序列.md)

- [统计全为1的正方形子矩阵](https://github.com/TheDiscoverer/blog/blob/master/刷题/统计全为1的正方形子矩阵.md)

- [统计作战单位数](https://github.com/TheDiscoverer/blog/blob/master/刷题/统计作战单位数.md)

## 链表

- [未排序正数数组中累加和为给定值的最长子数组的长度](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E6%9C%AA%E6%8E%92%E5%BA%8F%E6%AD%A3%E6%95%B0%E6%95%B0%E7%BB%84%E4%B8%AD%E7%B4%AF%E5%8A%A0%E5%92%8C%E4%B8%BA%E7%BB%99%E5%AE%9A%E5%80%BC%E7%9A%84%E6%9C%80%E9%95%BF%E5%AD%90%E6%95%B0%E7%BB%84%E7%9A%84%E9%95%BF%E5%BA%A6.md)

- [旋转链表](https://github.com/TheDiscoverer/blog/blob/master/刷题/旋转链表.md)

- [复杂链表的赋值](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E5%A4%8D%E6%9D%82%E9%93%BE%E8%A1%A8%E7%9A%84%E5%A4%8D%E5%88%B6.md)


## 树
- [判断是否为平衡二叉树](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E5%B9%B3%E8%A1%A1%E4%BA%8C%E5%8F%89%E6%A0%91.md)

- [二叉搜索树的范围和 - S](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E7%9A%84%E8%8C%83%E5%9B%B4%E5%92%8C.md)

- [填充每个节点的下一个右侧节点指针 II - M](https://github.com/TheDiscoverer/blog/blob/master/刷题/填充每个节点的下一个右侧节点指针II.md)

- [最近公共祖先](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E6%9C%80%E8%BF%91%E5%85%AC%E5%85%B1%E7%A5%96%E5%85%88.md)

- [二叉树的最近公共祖先](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E8%BF%91%E5%85%AC%E5%85%B1%E7%A5%96%E5%85%88.md)

- [二叉搜索树的公共祖先](https://github.com/TheDiscoverer/blog/blob/master/刷题/二叉搜索树的最近公共祖先.md)

- [二叉树的右视图](https://github.com/TheDiscoverer/blog/blob/master/刷题/二叉树的右视图.md)

- [z字形打印二叉树](https://github.com/TheDiscoverer/blog/blob/master/刷题/z字形打印二叉树.md)

- [二叉树的最大路径和](https://github.com/TheDiscoverer/blog/blob/master/刷题/二叉树中的最大路径和.md)

- [二叉树的深度](https://github.com/TheDiscoverer/blog/blob/master/刷题/二叉树的深度.md)

- [从中序与后序遍历序列构造二叉树](https://github.com/TheDiscoverer/blog/blob/master/刷题/从中序与后序遍历序列构造二叉树.md)

- [填充每个节点的下一个右侧节点指针](https://github.com/TheDiscoverer/blog/blob/master/刷题/填充每个节点的下一个右侧节点指针.md)

- [二叉搜索树迭代器](https://github.com/TheDiscoverer/blog/blob/master/刷题/二叉搜索树迭代器.md)

## 数组

基于数组的题，往往需要用到排序，双指针（两头往内扩展，从左往右扩展），前缀和，动态规划，二分查找，哈希表等。

1. 双指针，用在关于求和里面比较多。四数之和（在最后两层遍历的时候才用双指针，一个前一个后），和为s的两个数字（双指针一前一后），删除排序数字中的重复项（前一个指向可以被覆盖的位置，后一个指向去覆盖的值），长度最小的子数组（双指针，两个都在前面）。
2. 暴力搜索。组合总和III。
3. 动态规划。最佳旅行观光（找状态转移方程，前面的依赖于后面的），和可被 K 整除的子数组（前缀和，map存储之前的信息）
4. 排序。使数组唯一的最小增量（使用到了排序，但是还是用了些trick，以前也见过）
5. 很直接的办法。螺旋矩阵，旋转矩阵
6. 原地算法。生命游戏，矩阵置零，可以利用数组中的值设为标识位。
7. 二分查找

- [生命游戏](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E7%94%9F%E5%91%BD%E6%B8%B8%E6%88%8F.md)

- [矩阵置零](https://github.com/TheDiscoverer/blog/blob/master/刷题/矩阵置零.md)

- [旋转矩阵](https://github.com/TheDiscoverer/blog/blob/master/刷题/旋转矩阵.md)

- [使数组唯一的最小增量](https://github.com/TheDiscoverer/blog/blob/master/刷题/使数组唯一的最小增量.md)

- [删除排序数组中的重复项 II](https://github.com/TheDiscoverer/blog/blob/master/刷题/删除排序数组中的重复项%20II.md)

- [螺旋矩阵](https://github.com/TheDiscoverer/blog/blob/master/刷题/螺旋矩阵.md)

- [四数之和](https://github.com/TheDiscoverer/blog/blob/master/刷题/四数之和.md)

- [和为s的两个数字](https://github.com/TheDiscoverer/blog/blob/master/刷题/和为s的两个数字.md)

- [最佳观光组合](https://github.com/TheDiscoverer/blog/blob/master/刷题/最佳观光组合.md)

- [组合总和III](https://github.com/TheDiscoverer/blog/blob/master/刷题/组合总和III.md)

- [求众数 II](https://github.com/TheDiscoverer/blog/blob/master/刷题/求众数II.md)

- [数组中重复的数据](https://github.com/TheDiscoverer/blog/blob/master/刷题/数组中重复的数据.md)

- [盛最多水的容器](https://github.com/TheDiscoverer/blog/blob/master/刷题/盛最多水的容器.md)

- [跳跃游戏](https://github.com/TheDiscoverer/blog/blob/master/刷题/跳跃游戏.md)

- [合并区间](https://github.com/TheDiscoverer/blog/blob/master/刷题/合并区间.md)

- [合并排序的数组](https://github.com/TheDiscoverer/blog/blob/master/刷题/合并排序的数组.md)

- [最大交换](https://github.com/TheDiscoverer/blog/blob/master/刷题/最大交换.md)

- [汇总区间](https://github.com/TheDiscoverer/blog/blob/master/刷题/汇总区间.md)

- [缺失的第一个正数](https://github.com/TheDiscoverer/blog/blob/master/刷题/缺失的第一个正数.md)

- [插入区间](https://github.com/TheDiscoverer/blog/blob/master/刷题/插入区间.md)

- [航班预订统计](https://github.com/TheDiscoverer/blog/blob/master/刷题/航班预订统计.md)

### 子数组问题

- [长度最小的子数组](https://github.com/TheDiscoverer/blog/blob/master/刷题/长度最小的子数组.md)

- [和可被 K 整除的子数组](https://github.com/TheDiscoverer/blog/blob/master/刷题/和可被%20K%20整除的子数组.md)

- [绝对差不超过限制的最长连续子数组](https://github.com/TheDiscoverer/blog/blob/master/刷题/绝对差不超过限制的最长连续子数组.md)

- [尽可能使字符串相等](https://github.com/TheDiscoverer/blog/blob/master/刷题/尽可能使字符串相等.md)

### 二分查找
二分查找，经常用在有序数组中，比如求第一次出现x时的下标，最后一次出现时的下标，大于等于的最小值，小于等于的最大值等等。一般while中为<=符号。比如在求第一次出现x时的下标，当出现x时候，我们可以独立判断一下是不是第一次出现，其余类似。

- [搜索旋转排序数组II](https://github.com/TheDiscoverer/blog/blob/master/刷题/搜索旋转排序数组II.md)

- [最长上升子序列](https://github.com/TheDiscoverer/blog/blob/master/刷题/最长上升子序列.md)

## 堆

- [数据流中的中位数](https://github.com/TheDiscoverer/blog/blob/master/%E5%88%B7%E9%A2%98/%E6%95%B0%E6%8D%AE%E6%B5%81%E7%9A%84%E4%B8%AD%E4%BD%8D%E6%95%B0.md)

## 字符串

- [z字形变换](https://github.com/TheDiscoverer/blog/blob/master/刷题/z字形变换.md)

- [罗马数组转整数](https://github.com/TheDiscoverer/blog/blob/master/刷题/罗马数字转整数.md)

- [整数转罗马数字](https://github.com/TheDiscoverer/blog/blob/master/刷题/整数转罗马数字.md)

- [复原IP地址](https://github.com/TheDiscoverer/blog/blob/master/刷题/复原IP地址.md)

- [最长回文子序列](https://github.com/TheDiscoverer/blog/blob/master/刷题/最长回文子序列.md)	*动态规划*

- [表示数值的字符串](https://github.com/TheDiscoverer/blog/blob/master/刷题/表示数值的字符串.md) 	*自动机*
			  
- [正则表达式](https://github.com/TheDiscoverer/blog/blob/master/刷题/正则表达式匹配.md)

- [二进制求和](https://github.com/TheDiscoverer/blog/blob/master/刷题/二进制求和.md)

- [一次编辑](https://github.com/TheDiscoverer/blog/blob/master/刷题/一次编辑.md)

- [字符串相乘](https://github.com/TheDiscoverer/blog/blob/master/刷题/字符串相乘.md)

- [每个元音包含偶数次的最长子字符串](https://github.com/TheDiscoverer/blog/blob/master/刷题/每个元音包含偶数次的最长子字符串.md)

- [单词距离](https://github.com/TheDiscoverer/blog/blob/master/刷题/单词距离.md)

## 找规律

- [圆圈中最后剩下的数字](https://github.com/TheDiscoverer/blog/blob/master/刷题/圆圈中最后剩下的数字.md)

- [子集II](https://github.com/TheDiscoverer/blog/blob/master/刷题/子集%20II.md)

- [Pow(x,n)](https://github.com/TheDiscoverer/blog/blob/master/刷题/Pow.md)

## 搜索

### DFS

- [括号](https://github.com/TheDiscoverer/blog/blob/master/刷题/括号.md)

### BFS

 - [01矩阵](https://github.com/TheDiscoverer/blog/blob/master/刷题/01矩阵.md)
 