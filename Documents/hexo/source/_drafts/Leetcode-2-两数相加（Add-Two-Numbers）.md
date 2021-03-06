---
title: Leetcode-2 两数相加（Add Two Numbers）
copyright: true
date: 2019-04-01 15:11:42
tags: leetcode
categories: 学习
---

#### 1. [题目](https://leetcode-cn.com/problems/add-two-numbers/submissions/)
>给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。</br>  
>如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。</br>  
>您可以假设除了数字 0 之外，这两个数都不会以 0 开头。
>示例：
>输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
>输出：7 -> 0 -> 8
>原因：342 + 465 = 807


#### 2. 解题思路
&nbsp; &nbsp; &nbsp; &emsp; 简单题，注意链表操作和进位即可
``` python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:

        head = ans = ListNode(0)
        is_carry = False
        while l1 != None and l2 != None:

            num = l1.val + l2.val
            if is_carry:
                num = num + 1
            if num >= 10:
                num = num % 10
                is_carry = True
            else:
                is_carry = False
            ans.next = ListNode(num)
            ans = ans.next
            l1 = l1.next
            l2 = l2.next

        while l1 != None:
            if is_carry:
                if l1.val + 1 >= 10:
                    ans.next = ListNode((l1.val + 1) % 10)
                    is_carry = True
                else:
                    ans.next = ListNode(l1.val + 1)
                    is_carry = False

            else:
                ans.next = ListNode(l1.val)
            l1 = l1.next
            ans = ans.next

        while l2 != None:
            if is_carry:
                if l2.val + 1 >= 10:
                    ans.next = ListNode((l2.val + 1) % 10)
                    is_carry = True
                else:
                    ans.next = ListNode(l2.val + 1)
                    is_carry = False
            else:
                ans.next = ListNode(l2.val)
            l2 = l2.next
            ans = ans.next

        if is_carry:
            ans.next = ListNode(1)
            is_carry = False
            ans = ans.next

        res = []
        while head != None:
            res.append(head.val)
            head = head.next

        # return "".join([""+str(each) for each in res])[:-1]
        return res[1:]
            
            
            
```
#### 3. 总结/分类
&emsp; 链表操作