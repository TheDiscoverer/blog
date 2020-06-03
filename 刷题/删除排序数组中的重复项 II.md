## 删除排序数组中的重复项 II

- 题目链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array-ii/
- Tag：数组

## 题目描述

给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

示例 1:

给定 nums = [1,1,1,2,2,3],

函数应返回新长度 length = 5, 并且原数组的前五个元素被修改为 1, 1, 2, 2, 3 。你不需要考虑数组中超出新长度后面的元素。

## 解法
使用两个指针i,nextIndex，其中i是我们当前要需要扫描并且填充的位置，nextIndex是将该元素位置填充到i位置。
起初nextIndex == i，将nextIndex 元素赋值到i位置中。当nums[i] == nums[i - 1] && nums[i] == nums[i - 2]时，将nextIndex位置放置到 i 位置，然后nextIndex++，然后继续判断。然后 i++。

```
class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums == null)
            return -1;
        if(nums.length <= 2)
            return nums.length;
        int nextIndex = 2;
        for(int i = 2; i < nums.length; i++) {
        	//注意这里的nextIndex需要判断是否越界。
            if(nextIndex >= nums.length)
                return i;
            nums[i] = nums[nextIndex];
            nextIndex++;
            while(nums[i] == nums[i - 1] && nums[i] == nums[i - 2]) {
                if(nextIndex >= nums.length)
                    return i;
                else {
                    nums[i] = nums[nextIndex];
                    nextIndex++;
                }
            }
            
        }
        return nums.length;
    }
}
```