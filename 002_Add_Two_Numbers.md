# 002. Add Two Numbers

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        num_arr = [[], []]
        self.convertNum(l1, num_arr[0])
        self.convertNum(l2, num_arr[1])
        
        buff_1 = 0
        buff_2 = 0
        for i in range(len(num_arr[0])):
            buff_1 *= 10
            buff_1 += num_arr[0].pop()
        for i in range(len(num_arr[1])):
            buff_2 *= 10
            buff_2 += num_arr[1].pop()
        buff_sum = buff_1 + buff_2
        
        buff_arr = []
        if buff_sum is 0:
            buff_arr.append(0)
        while buff_sum >= 1:
            buff_arr.append(int(buff_sum % 10))
            buff_sum //= 10
        return self.convertNode(buff_arr)
    
    def convertNode(self, arr):
        if len(arr) is 0:
            return
        val = arr.pop(0)
        list_node = ListNode(val)
        list_node.next = self.convertNode(arr)
        return list_node
    
    def convertNum(self, node, arr):
        arr.append(node.val)
        if node.next is None:
            return
        self.convertNum(node.next, arr)
```

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        result = ListNode(0)
        current_node = result
        
        p = l1
        q = l2
        carry = 0
        
        while p or q:
            x = 0 if p is None else p.val
            y = 0 if q is None else q.val
            sum = x + y + carry
            carry = sum // 10
            current_node.next = ListNode(int(sum % 10))
            current_node = current_node.next
            
            if p is not None: 
                p = p.next
            if q is not None: 
                q = q.next
        
        if carry > 0: 
            current_node.next = ListNode(carry)
        
        return result.next
```

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        result = current = ListNode(None)
        carry = 0
        
        while l1 and l2:
            carry, remainder = divmod(l1.val + l2.val + carry, 10)
            current.next = ListNode(remainder)
            l1, l2 = l1.next, l2.next
            current = current.next
        
        while l1:
            carry, remainder = divmod(l1.val + carry, 10)
            current.next = ListNode(remainder)
            l1 = l1.next
            current = current.next
            
        while l2:
            carry, remainder = divmod(l2.val + carry, 10)
            current.next = ListNode(remainder)
            l2 = l2.next
            current = current.next
            
        if carry != 0:
            current.next = ListNode(carry)
        
        return result.next
```