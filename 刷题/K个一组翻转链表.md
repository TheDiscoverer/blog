## K个一组翻转链表

- 题目链接：https://leetcode-cn.com/problems/reverse-nodes-in-k-group/
- Tag：链表

## 题目描述
给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。

k 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。

```
示例：

给你这个链表：1->2->3->4->5

当 k = 2 时，应当返回: 2->1->4->3->5

当 k = 3 时，应当返回: 3->2->1->4->5
```

## 解法
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    boolean flag = true;
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode newHead = new ListNode(-1), newTail = newHead;
        ListNode KNodeHead, kNodeTail;
        
        if(head == null)
            return head;
        
        while(head != null) {
            flag = true;
            KNodeHead = head;
            kNodeTail = getKNodeTail(head, k);
            head = kNodeTail.next;
            kNodeTail.next = null;
            if(!flag) {
                newTail.next = KNodeHead;
            }else{
                newTail.next = reverseKNode(KNodeHead);
            }
            newTail = KNodeHead;
        }
        
        return newHead.next;
    }
    
    private ListNode getKNodeTail(ListNode head , int k) {
        int i = 0;
        for(; i < k - 1 && head.next != null; i++) {
            head = head.next;
        }
        
        if(i < k - 1 && head.next == null) {
            this.flag = false;
        }
            
        return head;
    }
    
    private ListNode reverseKNode(ListNode head) {
        ListNode pre = null;
        ListNode curr = head, next;
        
        while(curr != null) {
            next = curr.next;
            curr.next = pre;
            pre = curr;
            curr = next;
        }
        return pre;
    }
    
}
```