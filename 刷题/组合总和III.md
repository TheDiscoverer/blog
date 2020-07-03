## 组合总和III

- 题目链接：https://leetcode-cn.com/problems/combination-sum-iii/
- Tag：回溯

## 题目描述
找出所有相加之和为 n 的 k 个数的组合。组合中只允许含有 1 - 9 的正整数，并且每种组合中不存在重复的数字。

说明：

所有数字都是正整数。
解集不能包含重复的组合。

示例 1:

输入: k = 3, n = 7
输出: [[1,2,4]]
示例 2:

输入: k = 3, n = 9
输出: [[1,2,6], [1,3,5], [2,3,4]]

## 解法
回溯法，遍历所有可能情况。
dfs(int index, int sum, int lastValue, int target)表示计算arr中index位置可以出现的数字。

不过为了进行剪枝，我们首先行判断
- sum是否大于target，如果是则直接剔除掉
- index == 最后的位置 + 1，这时候表示选择已经结束，判断sum == target ，最后return
- 接下来遍历index位置可能出现的所有数字，然后递归进入index + 1 状态。在这里遍历index位置可能数字可以限定下范围。
```
class Solution {
    int[] arr;
    List<List<Integer>> rt;
    public List<List<Integer>> combinationSum3(int k, int n) {
        arr = new int[k];
        rt = new ArrayList<>();
        dfs(0, 0, 0, n);
        return rt;
    }
    
    public void dfs(int index, int sum, int lastValue, int target) {
        if(sum > target)
            return;
        if(index == arr.length) {
            if(target == sum) {
                rt.add(ArrayToList(arr));
           }
            return;
        }
        for(int i = lastValue + 1; i < 10 - (arr.length - index) + 1; i++) {
            arr[index] = i;
            dfs(index + 1, sum + i, i, target);
        }
    }
    
    public List<Integer> ArrayToList(int[] arr) {
        List<Integer> temp = new ArrayList<>();
        for(int item : arr)
            temp.add(item);
        return temp;
    }
}
```