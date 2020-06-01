## 填充每个节点的下一个右侧节点指针 II

- 题目链接：https://leetcode-cn.com/problems/populating-next-right-pointers-in-each-node-ii/
- Tag：树

## 题目描述
给定一个二叉树
```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```
填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。初始状态下，所有 next 指针都被设置为 NULL。

## 解法
1、可以使用BFS来一层一层遍历，但时间复杂度为On

2、依靠每个节点的next指针来对一层进行遍历

```
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
        Node head = root;
        if(head == null)
            return head;
        root.next = null;
        while(head != null) {
            Node nextHead = constructNext(head);
            head = nextHead;
        }
        return root;
    }
    //完成对下一层节点next指针的构建
    public Node constructNext(Node head) {
        Node node1 = head, secHead = new Node(-1);
        Node node2 = secHead;
        boolean isLeft = true;
        while(node1 != null) {
           // System.out.println(node1.val);
           ／/标记下一次遍历的左子节点还是右子节点
            if(isLeft) {
                if(node1.left != null) {
                    node2.next = node1.left;
                    node2 =  node2.next;
                    isLeft = false;
                }else{
                    isLeft = false;
                }
            }else{
               
                if(node1.right != null) {
                    node2.next = node1.right;
                    isLeft = true;
                    node2 = node2.next;
                    node1 = node1.next;
                }else{
                    node1 = node1.next;
                    isLeft = true;
                }
            }
        }
        return secHead.next;
    }
}
```