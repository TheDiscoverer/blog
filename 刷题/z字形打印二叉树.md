## z字形打印二叉树

- 题目链接：https://leetcode-cn.com/problems/binary-tree-zigzag-level-order-traversal/
- Tag：树

## 题目描述
给定一个二叉树，返回其节点值的锯齿形层次遍历。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。

## 解法
BFS遍历二叉树有两种办法，一种一层一层的遍历，第二种是每一层之间增加一个null节点，便于得知到了下一层，这样可以一起遍历，这里采用第二种方法比较方便，只是每次取元素的时候如果是奇数层采用尾插法，偶数层采用头插法。
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> rt = new LinkedList<>();
        LinkedList<TreeNode> q = new LinkedList<>();
        LinkedList<Integer> list = new LinkedList<>();
        boolean isOrderLeft = true;
        if(root == null)
            return rt;
        q.add(root);
        q.add(null);
        while(!q.isEmpty()) {
            TreeNode curr = q.removeFirst();
            if(curr != null) {
                if(isOrderLeft)  {
                    list.addLast(curr.val);
                }else {
                    list.addFirst(curr.val);
                }
                if(curr.left != null)
                    q.add(curr.left);
                if(curr.right != null) 
                    q.add(curr.right);
            }else{
                rt.add(list);
                list = new LinkedList<>();
                q.add(null);
                isOrderLeft = !isOrderLeft;
            }
        }
        return rt;
    }
}
```