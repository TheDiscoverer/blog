## Pow(x,n)

- 题目链接：https://leetcode-cn.com/problems/powx-n/
- Tag：

## 题目描述
实现 pow(x, n) ，即计算 x 的 n 次幂函数。
```
示例 1:

输入: 2.00000, 10
输出: 1024.00000
示例 2:

输入: 2.10000, 3
输出: 9.26100
示例 3:

输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25
```

## 解法
需要注意一下n == Integer.MIN_VALUE的情况，所以需要向上转型

```
class Solution {
    public double myPow(double x, int n) {
        if(n == 0)
             return 1;
        double res;
        long N = n;
        if(n < 0) {
            res = 1 / getPow(x, -N);
        }else{
            res = getPow(x, N);
        }
        return res;
    }
    
    public double getPow(double x, long n) {
        if( n == 1)
            return x;
        double res = 1;
        if(n > 1) {
            res = getPow(x * x, n / 2);
            if(n % 2 == 1) {
                res = res * x;
            }
        }
        return res;
    }
}
```