## 子集 II

- 题目链接：https://leetcode-cn.com/problems/subsets-ii/submissions/
- Tag：找规律

## 题目描述
给定一个可能包含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。

说明：解集不能包含重复的子集。

示例:
```
输入: [1,2,2]
输出:
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
```

## 解法
这一题可以找规律发现存在重复子集的问题。
```
[]
[],[1]  在上一层添加1
[],[1],[2],[1,2]	在上一层添加2
[],[1],[2],[1,2],[2],[1,2],[2,2],[1,2,2]
```
在三层上一层添加2时，就出现重复问题，问题出在上一层[],[1]，因为我们对这两个集合添加了两次2，一次当发现重复时候需要记录下上次产生的新的子集，对新的子集添加2
```
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>> rt = new ArrayList<>();
        Arrays.sort(nums);
        int start = 0;
        int j = 0, size;
        rt.add(new ArrayList<>());
        for(int i = 0; i < nums.length; i++) {
            if(i > 0 && nums[i] == nums[i - 1]) 
                j = start;
            else
                j = 0;
            size = rt.size();
            start = size;
            for(; j < size; j++) {
                List<Integer> temp = new ArrayList<>(rt.get(j));
                temp.add(nums[i]);
                rt.add(temp);
            }
        }
        return rt;
    }
}
```