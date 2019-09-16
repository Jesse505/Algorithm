## 反转链表

### 题目描述
输入一个链表，反转链表后，输出新链表的表头。

### 解法
#### 解法一
利用头插法解决。

```java

/**
 * @author bingo
 * @since 2018/11/22
 */

/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    /**
     * 反转链表
     * @param head 链表头部
     * @return 反转后的链表
     */
    public ListNode ReverseList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
      
        ListNode pre = null;
        ListNode next = null;
        while (head != null) {
          	//记录下一个结点
          	next = head.next;
          	//将当前结点的指针指向前面一个结点
            head.next = pre;
          	//当前结点变成了先前的结点
          	pre = head;
          	//下一个结点变成了需要反转的结点
          	head = next;
        }

        return pre;
    }
}
```

#### 解法二：递归

```java
/**
 * @author bingo
 * @since 2018/11/22
 */


/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode ReverseList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        
        ListNode next = ReverseList(head.next);
        ListNode cur = next;
        while (cur.next != null) {
            cur = cur.next;
        }
        cur.next = head;
        head.next = null;
        return next;
    }
}
```

### 测试用例
1. 功能测试（链表中有多个结点/只有一个节点）；
2. 特殊输入测试（链表头节点为空指针）。