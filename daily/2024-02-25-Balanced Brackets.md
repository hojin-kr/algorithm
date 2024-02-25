## Info
- Title : Balanced Brackets
- Description : https://www.hackerrank.com/challenges/one-week-preparation-kit-balanced-brackets
- Provider : hackerRank

## Intuition
스택 구조 이해
## Approach
<!-- Describe your approach to solving the problem. -->
짝 지어 배치되어야 하는 두 값에 대해서 스택 구조를 활용해서 접근

## Code
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'isBalanced' function below.
#
# The function is expected to return a STRING.
# The function accepts STRING s as parameter.
#

def isBalanced(s):
    # Write your code here
    stack = []
    for char in s:
        if char in '({[':
            # if open tag
            stack.append(char)
        else:
            # if close tag
            # check in the stack top
            if not stack:
                top = ''
            else:
                top = stack.pop()
            
            if (char == ')') and top != '(' or \
                (char == '}') and top != '{' or \
                (char == ']') and top != '[':
                return "NO"
    return "YES" if not stack else "NO"
        

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    t = int(input().strip())

    for t_itr in range(t):
        s = input()

        result = isBalanced(s)

        fptr.write(result + '\n')

    fptr.close()
```

