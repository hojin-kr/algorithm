## Info
- Title : Merge two sorted linked lists
- Description : [[https://leetcode.com/problems/first-unique-character-in-a-string/description/ ](https://www.hackerrank.com/challenges/one-week-preparation-kit-queue-using-two-stacks)](https://www.hackerrank.com/challenges/one-week-preparation-kit-merge-two-sorted-linked-lists)
- Provider : hackerRank

## Intuition
링크 리스트에 대한 이해 정의된 클래스를 해석하고 활용
## Approach
<!-- Describe your approach to solving the problem. -->
정렬된 두개의 링크드 리스트에 대해서 정렬된 상태를 유지하며 머지하는 방식에 대해서 접근 필요

## Code
```
#!/bin/python3

import math
import os
import random
import re
import sys

class SinglyLinkedListNode:
    def __init__(self, node_data):
        self.data = node_data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None

    def insert_node(self, node_data):
        node = SinglyLinkedListNode(node_data)

        if not self.head:
            self.head = node
        else:
            self.tail.next = node


        self.tail = node

def print_singly_linked_list(node, sep, fptr):
    while node:
        fptr.write(str(node.data))

        node = node.next

        if node:
            fptr.write(sep)

# Complete the mergeLists function below.

#
# For your reference:
#
# SinglyLinkedListNode:
#     int data
#     SinglyLinkedListNode next
#
#
def mergeLists(head1, head2):
    dummy = SinglyLinkedList()
    current = dummy
    
    while head1 is not None and head2 is not None:
        if head1.data < head2.data:
            current.next = head1
            head1 = head1.next
        else:
            current.next = head2
            head2 = head2.next
        current = current.next
        
    if head1 is not None:
        current.next = head1
    elif head2 is not None:
        current.next = head2
    
    return dummy.next

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    tests = int(input())

    for tests_itr in range(tests):
        llist1_count = int(input())

        llist1 = SinglyLinkedList()

        for _ in range(llist1_count):
            llist1_item = int(input())
            llist1.insert_node(llist1_item)
            
        llist2_count = int(input())

        llist2 = SinglyLinkedList()

        for _ in range(llist2_count):
            llist2_item = int(input())
            llist2.insert_node(llist2_item)

        llist3 = mergeLists(llist1.head, llist2.head)

        print_singly_linked_list(llist3, ' ', fptr)
        fptr.write('\n')

    fptr.close()
```
