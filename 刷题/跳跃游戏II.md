## 跳跃游戏II

- 题目链接：
- Tag：

## 题目描述
给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

你的目标是使用最少的跳跃次数到达数组的最后一个位置。
```
示例:

输入: [2,3,1,1,4]
输出: 2
解释: 跳到最后一个位置的最小跳跃数是 2。
     从下标为 0 跳到下标为 1 的位置，跳 1 步，然后跳 3 步到达数组的最后一个位置。
说明:

假设你总是可以到达数组的最后一个位置。
```

## 解法
o(n),每次到达边界，就step++
```
class Solution {
    public int jump(int[] nums) {
        if(nums == null || nums.length == 0 || nums.length == 1)
            return 0;
        int end = 0, step = 0, pos = 0;
        for(int i = 0; i < nums.length - 1; i++) {
            pos = Math.max(pos, i + nums[i]);
            if(i == end) {
                end = pos;
                step++;
            }
        }
        return step;
    }
}
```
o(n2)
```
class Solution {
    public int jump(int[] nums) {
        if(nums == null || nums.length == 0 || nums.length == 1)
            return 0;
        int dp[] = new int[nums.length];
        for(int i = 1; i < nums.length; i++)
            dp[i] = Integer.MAX_VALUE;
        for(int i = 0; i < nums.length; i++) {
            for(int k = 1; k <= nums[i] && k + i < nums.length; k++) {
                dp[k + i] = Math.min(dp[k + i], dp[i] + 1);
            }
        }
        return dp[nums.length - 1];
    }
}
```