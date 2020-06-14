## 和可被 K 整除的子数组

- 题目链接：https://leetcode-cn.com/problems/subarray-sums-divisible-by-k/
- Tag：子数组

## 题目描述
给定一个整数数组 A，返回其中元素之和可被 K 整除的（连续、非空）子数组的数目。
```
示例：

输入：A = [4,5,0,-2,-3,1], K = 5
输出：7
解释：
有 7 个子数组满足其元素之和可被 K = 5 整除：
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
```
## 解法
主要使用了哈希表，前缀和和同余定理

假如sum[i] = A[0,...,i]，我们为了求出以i为结尾的满足要求子数组，则我们必须找到j使得sum[i] - sum[j] = A[j+1,...,i] % K = 0, 根据同余定理知 sum[i] % k == sum[j] % k，因此需要找到i之前前缀和满足模k为sum[i] % k的子数组。因此每次遍历i时，都可以用哈希表记录下模k为sum[i] % k的子数组个数，这样能够以o1复杂度找到sum[j]。

需要注意的是负数取模可能小于0，因此我们都统一转换为正数。（而python就是大于0）

```
class Solution {
    public int subarraysDivByK(int[] A, int K) {
        Map<Integer, Integer> map = new HashMap<>();
        int rt = 0, sum = 0, mod;
        map.put(0, 1);
        for(int i = 0; i < A.length; i++) {
            sum += A[i];
            mod = (sum % K + K) % K;
            int t = map.getOrDefault(mod, 0);
            rt += t;
            map.put(mod,t + 1);
        }
        return rt;
    }
}
```