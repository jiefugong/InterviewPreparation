# Interview Preparation: Python
======================================

## Purpose  
This README will serve as a central point where I will manage solving interview questions and give tested solutions. 

## Table of Contents
1. [Arrays](#arrays)
1. [Strings](#strings)
1. [Stacks and Queues](#stacks-and-queues)
1. [Recursion](#recursion)
1. [Numbers](#numbers)
1. [Javascript Specific](#javascript)
1. [Linked Lists](#linked-lists)
1. To Be Continued

## Array
<a name="array--product"></a><a name="1.1"></a>
- **[1.1](#array--product) Given an array of integers, find the largest product yielded from three of the integers**

## Linked Lists
<a name="LinkedList-Reorder"></a><a name="7.1"></a>
- **[7.1](#LinkedList-Reorder) Given a singly linked list like: $L_o = L_1 \rightarrow L_2 \rightarrow ... \rightarrow L_{n-1} \rightarrow L_{n}$ rearrange it into: $L_o = L_1 \rightarrow L_n \rightarrow L_2 \rightarrow L_{n-1} \rightarrow ...$**

```python
def reorderList(self, head):
    """
    :type head: ListNode
    :rtype: void Do not return anything, modify head in-place instead.
    """
    if head is None or head == []:
        return

    # Separate the list into a first (which denotes the last node of the forward
    # section and rest, which constitutes all other nodes
    first = head
    rest = first.next   
    
    # While the number of nodes in the rest of the linked list is greater than 1
    # we know that we can continue to modify our list according to the question.
    while (self.listSize(rest) > 1):        
        second_to_last = rest
        last = rest.next

        if (last != None):
            while (last.next != None):
                second_to_last = second_to_last.next
                last = last.next
    
        # We keep track of the second to last and last node of rest
        # The second to last node allows us to determine where the list should end
        # The last node is what we'll continually move to the end of front
        second_to_last.next = None
    
        # Here we point our first node at the last one, 
        # point the next of last to rest, and reset the tail
        first.next = last
        last.next = rest
        first = rest
        rest = rest.next
```