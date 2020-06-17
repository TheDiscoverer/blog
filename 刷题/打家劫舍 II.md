## 打家劫舍 II

- 题目链接：https://leetcode-cn.com/problems/house-robber-ii/
- Tag：动态规划

## 题目描述
你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋都围成一圈，这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

给定一个代表每个房屋存放金额的非负整数数组，计算你在不触动警报装置的情况下，能够偷窃到的最高金额。
```
示例 1:

输入: [2,3,2]
输出: 3
解释: 你不能先偷窃 1 号房屋（金额 = 2），然后偷窃 3 号房屋（金额 = 2）, 因为他们是相邻的。
```

## 解法
分两种情况，第一家抢劫和不抢劫两种。 状态转移方程即为 dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i]);

```
class Solution {
    public int rob(int[] nums) {
        if(nums.length == 0)
            return 0;
        if(nums.length == 1)
            return nums[0];
        if(nums.length == 2)
            return Math.max(nums[0], nums[1]);
        int[] dp = new int[nums.length];
        int rt = 0;
        dp[0] = nums[0];
        dp[1] = nums[0];
        for(int i = 2; i < nums.length - 1; i++) {
            dp[i] = Math.max(dp[i - 2] + nums[i], dp[i - 1]);
        }
        rt = dp[nums.length - 2];
        dp[0] = 0;
        dp[1] = nums[1];
        for(int i = 2; i < nums.length; i++) {
            dp[i] = Math.max(dp[i - 2] + nums[i], dp[i - 1]);
        }
        rt = Math.max(rt, dp[nums.length - 1]);
        return rt;
    }
}
```
其他人的写法，空间复杂度为o(1)
```
class Solution {
    public int rob(int[] nums) {
        if(nums.length == 0)
            return 0;
        if(nums.length == 1)
            return nums[0];
        return Math.max(myRob(Arrays.copyOfRange(nums, 0, nums.length - 1)),
                       myRob(Arrays.copyOfRange(nums, 1, nums.length)));
    }
    public int myRob(int[] nums) {
        int curr = 0, pre = 0, temp = 0;
        for(int num : nums) {
            temp = curr;
            curr = Math.max(curr, pre + num);
            pre = temp;
        }
        return curr;
    }
}
```