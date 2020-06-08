## 和为s的两个数字

- 题目链接：https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/
- Tag：双指针

## 题目描述
输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。



## 解法
双指针。和三数之和，四数之和类似，将最后的两层遍历采用双指针方法，复杂度从o(n2)降到o(n)
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] rt = new int[2];
        if(nums == null || nums.length < 2) 
            return rt;
        int s = 0, e = nums.length - 1, sum;
        while(s < e) {
            sum = nums[s] + nums[e];
            if(sum < target)
                s++;
            else if(sum > target)
                e--;
            else
                break;
        }
        rt[0] = nums[s];
        rt[1] = nums[e];
        return rt;
    }
}
```