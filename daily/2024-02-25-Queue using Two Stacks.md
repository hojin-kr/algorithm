## Info
- Title : Queue using Two Stacks
- Description : [https://leetcode.com/problems/first-unique-character-in-a-string/description/ ](https://www.hackerrank.com/challenges/one-week-preparation-kit-queue-using-two-stacks)
- Provider : hackerRank

## Intuition
스택 두개로 큐를 구현하고 사용
## Approach
<!-- Describe your approach to solving the problem. -->
간단한 큐를 구현

## Code
```python
# Enter your code here. Read input from STDIN. Print output to STDOUT

class MyQueue:
    def __init__(self):
        self.stack1 = []
        self.stack2 = []
        
    def enqueue(self, x):
        self.stack1.append(x)
        
    def dequeue(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
                
        if self.stack2:
            return self.stack2.pop()
        else:
            return None
            
    def front(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        
        if self.stack2:
            return self.stack2[-1]
        else:
            return None

def qu(q, command):
    # each command imploement
    command = command.split(" ")
    if command[0] == "1":
        value = command[1]
        queue.enqueue(value)
    elif command[0] == "2":
        queue.dequeue()
    elif command[0] == "3":
        print(queue.front())
        
    else:
        print("None command", command)


if __name__ == '__main__':
    t = int(input().strip())
    
    queue = MyQueue()
    for t_itr in range(t):
        command = input().rstrip().strip()
        qu(queue, command)
        
```
