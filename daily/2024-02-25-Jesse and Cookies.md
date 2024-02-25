## Info
- Title : Jesse and Cookies
- Description :[ [[https://leetcode.com/problems/first-unique-character-in-a-string/description/ ](https://www.hackerrank.com/challenges/one-week-preparation-kit-queue-using-two-stacks)](https://www.hackerrank.com/challenges/one-week-preparation-kit-jesse-and-cookies)](https://www.hackerrank.com/challenges/one-week-preparation-kit-jesse-and-cookies)
- Provider : hackerRank

## Intuition
어떻게 시간 복잡도를 줄일 수 있는지
## Approach
<!-- Describe your approach to solving the problem. -->
정렬에 소모되는 자원을 어떻게 줄일 수 있는지에 대해서, 우선 순위 큐를 사용하면서도 
어레이를 우선순위 큐로 초기화 시키는 부분을 생각해야함

## Code
```python
#!/bin/python3

import math
import os
import random
import re
import sys
import heapq


#
# Complete the 'cookies' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER k
#  2. INTEGER_ARRAY A
#

def cookies(k, A):
    # Write your code here
    if not A:
        return -1
    heapq.heapify(A)
    for i in range(len(A)):
        first = heapq.heappop(A)
        if first >= k:
            return i
        if not A:
            return -1        
        heapq.heappush(A, first + 2*heapq.heappop(A))
    return -1
    
if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    first_multiple_input = input().rstrip().split()

    n = int(first_multiple_input[0])

    k = int(first_multiple_input[1])

    A = list(map(int, input().rstrip().split()))

    result = cookies(k, A)

    fptr.write(str(result) + '\n')

    fptr.close()

```
