## 搜索旋转排序数组 II

- 题目链接：https://leetcode-cn.com/problems/search-in-rotated-sorted-array-ii/
- Tag：二分查找

## 题目描述
假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,0,1,2,2,5,6] 可能变为 [2,5,6,0,0,1,2] )。

编写一个函数来判断给定的目标值是否存在于数组中。若存在返回 true，否则返回 false。

示例 1:

输入: nums = [2,5,6,0,0,1,2], target = 0
输出: true
示例 2:

输入: nums = [2,5,6,0,0,1,2], target = 3
输出: false

## 解法
1. 找到旋转点
	通过二分查找的方式寻找，首先两个指针left和right指向数组的左右位置，当mid大于left值，说明mid在旋转点的左边，left = mid，如果mid < right，说明在旋转点的右边，right = mid。但需要判断一种特殊情况，即arr[left] = arr[mid] == arr[right]，此时需要线性遍历数组。最有left 和right将会指向旋转点的左边和旋转点位置。
2. 判断target可能出现在旋转点的左边还是右边。
在存在重复的排序数组中二分查找一个数字，while的条件是用while(l <= r)，我看基本上都是用这种条件。但有些二分查找的题目要求找到重复中的第一个或者最后一个，这时候当arr[mid] = target 时需要判断才是不是符合要求的。
```
class Solution {
    public boolean search(int[] nums, int target) {
        if(nums == null || nums.length == 0)
            return false;
        int left = 0, right = nums.length - 1, mid;
        while(right - left > 1) {
            mid = (left + right) >> 1;
            if(nums[mid] == nums[left] && nums[mid] == nums[right]) {
                right = traverse(nums);
                break;
            }
            if(nums[mid] <= nums[right]) 
                right = mid;
            else if(nums[mid] >= nums[left])
                left = mid;
        }
        int m = right;
        if(target == nums[0] || target == nums[nums.length - 1])
            return true;
        else if(target < nums[nums.length - 1]) {
            return find(target, nums, m, nums.length - 1);
        }else if(target > nums[0]) {
            return find(target, nums, 0, m - 1);
        }else
            return false;
    }
    
    public int traverse(int[] nums) {
        int min = nums[nums.length - 1], minIndex = nums.length - 1;
        for(int i = nums.length - 2; i >= 0; i--) {
            if(nums[i] <= min) {
                minIndex = i;
                min = nums[i];
            }else if(nums[i] > min)
                break;
        }
        return minIndex;
    }
    
    public boolean find(int target, int[] nums, int l, int r) {
        int m;
        while(l <= r) {
            m = (l + r) >> 1;
            if(nums[m] == target) 
                return true;
            else if(nums[m] > target) {
                r = m - 1;
            }else
                l = m + 1;
        }
        return false;
    }
}
```