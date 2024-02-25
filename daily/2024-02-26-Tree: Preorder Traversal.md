## Info
- Title : Tree: Preorder Traversal
- Description : https://www.hackerrank.com/challenges/one-week-preparation-kit-tree-preorder-traversal
- Provider : hackerRank

## Intuition
이진 트리 이해
## Approach
<!-- Describe your approach to solving the problem. -->
이진트리의 원리와 코드로 구현한 구조에 대해서 이해해야하며, 전체를 탐색하고 출력을 원하는 정보가 무엇인지 파악해야함

## Code
```python3
class Node:
    def __init__(self, info): 
        self.info = info  
        self.left = None  
        self.right = None 
        self.level = None 

    def __str__(self):
        return str(self.info) 

class BinarySearchTree:
    def __init__(self): 
        self.root = None

    def create(self, val):  
        if self.root == None:
            self.root = Node(val)
        else:
            current = self.root
         
            while True:
                if val < current.info:
                    if current.left:
                        current = current.left
                    else:
                        current.left = Node(val)
                        break
                elif val > current.info:
                    if current.right:
                        current = current.right
                    else:
                        current.right = Node(val)
                        break
                else:
                    break

"""
Node is defined as
self.left (the left child of the node)
self.right (the right child of the node)
self.info (the value of the node)
"""
def preOrder(root):
    #Write your code here
    # preOrder
    if root is None:
        return
    
    print(root.info, end=' ')

    preOrder(root.left)
    preOrder(root.right)


tree = BinarySearchTree()
t = int(input())

arr = list(map(int, input().split()))

for i in range(t):
    tree.create(arr[i])

preOrder(tree.root)
```
