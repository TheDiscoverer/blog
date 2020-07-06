## 求众数II

- 题目链接：https://leetcode-cn.com/problems/majority-element-ii/
- Tag：摩尔投票法

## 题目描述

给定一个大小为 n 的数组，找出其中所有出现超过 ⌊ n/3 ⌋ 次的元素。

说明: 要求算法的时间复杂度为 O(n)，空间复杂度为 O(1)。
```
示例 1:

输入: [3,2,3]
输出: [3]
示例 2:

输入: [1,1,1,3,3,2,2,2]
输出: [1,2]

```

## 解法
和基础的摩尔投票问题一样，这里面应为要超过⌊ n/3 ⌋，所以这样的元素最多2个，因此我们设两个候选者。
- 当前票与一个候选者相同时，则票数+1
- 如果有一个候选者不存在（票数为0），则设置当前为候选者，票数+1。
- 如果与两个候选者都不相同时，则票数都-1
```
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> list = new ArrayList<>();
        if(nums.length == 0)
            return list;
        int n1 = nums[0], n2 = nums[0], c1 = 0, c2 = 0;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] == n1) {
                c1++;
            }else if(nums[i] == n2) {
                c2++;
            }else if(c1 == 0) {
                n1 = nums[i];
                c1++;
            }else if(c2 == 0) {
                n2 = nums[i];
                c2++;
            }else{
                c1--;
                c2--;
            }
        }
        c1 = 0;
        c2 = 0;
        for(int i = 0; i < nums.length; i++) {
            if(n1 == nums[i])   c1++;
            else if(n2 == nums[i])   c2++;
        }
        if(c1 > nums.length / 3)
            list.add(n1);
        if(c2 > nums.length / 3)
            list.add(n2);
        return list;
    }
}

```