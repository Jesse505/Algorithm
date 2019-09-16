## 合并两个排序的链表

### 题目描述
输入两个递增的链表，输出两个链表合成后的链表，合成后的链表仍然是递增的。

### 解法
#### 解法一：迭代
同时遍历两链表进行 `merge`。

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
     * 合并两个排序链表
     * @param list1 链表1
     * @param list2 链表2
     * @return 合并后的单调不递减链表
     */
    public ListNode Merge(ListNode list1, ListNode list2) {
				//新建一个临时的结点
        ListNode dummy = new ListNode(-1);
        ListNode cur = dummy;
        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                cur.next = list1;
              	list1 = list1.next;
            } else {
                cur.next = list2;
                list2 = list2.next;
            }
          	//迭代下一个
            cur = cur.next;
        }
      	//拼接剩余的链表
        cur.next = list1 != null ? list1 : list2;
        return dummy.next;
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
    /**
     * 合并两个排序链表
     * @param list1 链表1
     * @param list2 链表2
     * @return 合并后的单调不递减链表
     */
    public ListNode Merge(ListNode list1, ListNode list2) {
        if (list1 == null || list2 == null) {
            return list1 != null ? list1 : list2 ;
        }

        if (list1.val < list2.val) {
            list1.next = Merge(list1.next, list2);
            return list1;
        } else {
          	list2.next = Merge(list1, list2.next);
        		return list2;
        }
    }
}
```

### 测试用例
1. 功能测试（输入的两个链表有多个节点；节点的值互不相同或者存在值相等的多个节点）；
2. 特殊输入测试（两个链表的一个或者两个头节点为空指针；两个链表中只有一个节点）。