#### 链表中倒数第k个结点

#### 题目
>  输入一个链表，输出该链表中倒数第k个结点。

#### 思路
 - 快慢指针，让快指针先行`k`步
 - 在快指针先行k步的过程中，若发现链表长度小于`k`，则返回`null`

#### 代码

```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
        ListNode fast = head;
        ListNode slow = head;
        
        for (int i = 0; i < k ; i++) {
            if (fast == null)
                return null;
            fast = fast.next;
        }
        
        while(fast != null) {
            fast = fast.next;
            slow = slow.next;
        }
        
        return slow;
    }
}
```