## 题目地址：[Add Two Numbers](https://leetcode.com/problems/two-sum/)
---
## 题目简介：
给两个链表，倒序的数字，对两个链表相加，得到的结果同样是倒序的链表。
>You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their >nodes contain a single digit. Add the two numbers and return it as a linked list.
>You may assume the two numbers do not contain any leading zero, except the number 0 itself.
 
>Example:  
>Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)  
>Output: 7 -> 0 -> 8  
>Explanation: 342 + 465 = 807.
---
## 题目解析：基础数学和链表的知识，注意区别"->"和"."的区别。  
>c++版：

```
class Solution {
public:  
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {  
        if (!l1)  
            return l2;
        else if (!l2)
            return l1;
        ListNode *ans = new ListNode(0);
        ListNode *res = ans;
        int overflow = 0;
        while(l1 || l2 || overflow)
        {
            int t1 = (l1 == NULL) ? 0 : l1 -> val;
            int t2 = (l2 == NULL) ? 0 : l2 -> val;
            int temp = t1 + t2 + overflow;
            cout << temp << endl;
            if (l1)
                l1 = l1 -> next;
            if (l2)
                l2 = l2 -> next;
            int ans_int = (temp >= 10) ? temp - 10 : temp;
            ans -> next = new ListNode(ans_int);
            ans = ans -> next;
            overflow = (temp >= 10)?1:0;
        }
        return res->next;
    }
};
```
>Python版：

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
 
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        if (l1 == None):
            return l2
        elif (l2 == None):
            return l1
        overflow = 0;
        ans = res = ListNode (0)
        while(l1 or l2 or overflow):
            t1 = t2 = 0
            if (l1):
                t1 = l1.val
                l1 = l1.next
            if (l2):
                t2 = l2.val
                l2 = l2.next
            temp = t1 + t2 + overflow
            if temp >= 10:
                overflow = 1
                temp -= 10
            else:
                overflow = 0
            ans.next = ListNode(temp);
            ans = ans.next;
        return res.next
```
