## LeetCode_0023_合并K个升序链表（困难, 2022-10）
<!--info
tags: [链表, 堆, lc100]
source: LeetCode
level: 困难
number: '0023'
name: 合并K个升序链表
companies: []
-->

> [23. 合并K个升序链表 - 力扣（LeetCode）](https://leetcode.cn/problems/merge-k-sorted-lists)

<summary><b>问题简述</b></summary>

```txt
给你一个链表数组，每个链表都已经按升序排列。

请你将所有链表合并到一个升序链表中，返回合并后的链表。
```

<!-- 
<details><summary><b>详细描述</b></summary>

```txt
```

</details>
-->

<!-- <div align="center"><img src="../../../_assets/xxx.png" height="300" /></div> -->

<summary><b>思路</b></summary>

- 维护一个优先队列（最小堆），队列中每个元素为各链表中的当前节点；
- 依次弹出队首元素，如果当前队列还有元素就继续加入队列；
- 提示：
    - 优先队列的内部移动依赖于比较运算符；
    - Python 标准库提供了一个简单的堆队列实现 [`heapq`](https://docs.python.org/zh-cn/3/library/heapq.html)；

<details><summary><b>Python（写法 1，不重载运算符）</b></summary>

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        
        import heapq

        h = []  # 模拟堆
        cnt = 0  # 节点计数，防止对 node 排序，因为 node 没有重载 __lt__ 运算符
        for node in lists:
            if node:
                heapq.heappush(h, (node.val, cnt, node))  # 如果没有 cnt，那么当 val 相等时，就会比较 node
                cnt += 1
        
        dummy = cur = ListNode()
        while h:
            _, _, node = heapq.heappop(h)  # 弹出堆顶节点（当前最小
            cur.next = node
            cur = cur.next
            if (node := node.next):  # 如果该链表还有元素，继续加入堆
                heapq.heappush(h, (node.val, cnt, node))
                cnt += 1
        
        return dummy.next
```

</details>


<details><summary><b>Python（写法 2，重载运算符）</b></summary>

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        
        import heapq

        # 重载 ListNode 的 < 运算符
        ListNode.__lt__ = lambda o1, o2: o1.val < o2.val

        h = []  # 模拟堆
        for node in lists:
            if node:
                heapq.heappush(h, node)  # 因为重载了 < 运算符，直接加入节点
        
        dummy = cur = ListNode()
        while h:
            node = heapq.heappop(h)  # 弹出堆顶节点（当前最小）
            cur.next = node
            cur = cur.next
            if (node := node.next):  # 如果该链表还有元素，继续加入堆
                heapq.heappush(h, node)
        
        return dummy.next
```

</details>
