# Week3

## Permuting Two Arrays
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'twoArrays' function below.
#
# The function is expected to return a STRING.
# The function accepts following parameters:
#  1. INTEGER k
#  2. INTEGER_ARRAY A
#  3. INTEGER_ARRAY B
#

def twoArrays(k, A, B):
    # Write your code here
    # Sort A in ascending order
    A.sort()
    
    # Sort B in descending order
    B.sort(reverse=True)
    
    # Check each pair
    for i in range(len(A)):
        if A[i] + B[i] < k:
            return "NO"  # If any pair fails, return NO
    
    return "YES"  # If all pairs pass, return YES

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    q = int(input().strip())
    for q_itr in range(q):
        first_multiple_input = input().rstrip().split()
        n = int(first_multiple_input[0])
        k = int(first_multiple_input[1])
        A = list(map(int, input().rstrip().split()))
        B = list(map(int, input().rstrip().split()))
        result = twoArrays(k, A, B)
        fptr.write(result + '\n')
    fptr.close()

```

## 2 Subarray Division 2

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'birthday' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER_ARRAY s
#  2. INTEGER d
#  3. INTEGER m
#

def birthday(s, d, m):
    count = 0
    for i in range(len(s) - m + 1):
        if sum(s[i:i + m]) == d:
            count += 1
    return count
##OR
def birthday(s, d, m):
#     # Write your code here
#     count = 0
#     n = len(s)
    
#     # Compute the sum of the first window
#     current_sum = sum(s[:m])
    
#     # Check if the first window sum matches d
#     if current_sum == d:
#         count += 1
    
#     # Slide the window from start to end
#     for i in range(m, n):
#         current_sum = current_sum + s[i] - s[i - m]
#         if current_sum == d:
#             count += 1
    
#     return count

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    s = list(map(int, input().rstrip().split()))
    first_multiple_input = input().rstrip().split()
    d = int(first_multiple_input[0])
    m = int(first_multiple_input[1])
    result = birthday(s, d, m)
    fptr.write(str(result) + '\n')
    fptr.close()
```
## 3 XOR Strings 3
```python
def strings_xor(s, t):
    res = ""
    for i in range(len(s)):
        if s[i] == t[i]:
            res += '0';
        else:
            res += '1';

    return res

s = input()
t = input()
print(strings_xor(s, t))
```

## 4 Sales by Match

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'sockMerchant' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER n
#  2. INTEGER_ARRAY ar
#

def sockMerchant(n, ar):
    # Write your code here
    stck_count={}
    pairs=0
    for stack in ar:
        if stack in stck_count:
            stck_count[stack]+=1
        else:
            stck_count[stack]=1
    for key,values in stck_count.items():
       pairs+=values//2
    return pairs

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    ar = list(map(int, input().rstrip().split()))
    result = sockMerchant(n, ar)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 5 Migratory Birds

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'migratoryBirds' function below.
#
# The function is expected to return an INTEGER.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def migratoryBirds(arr):
    # Write your code here
    bird_count={}
    for i in arr:
        if i in bird_count:
            bird_count[i]+=1
        else:
            bird_count[i]=1
    max_count=max(bird_count.values())
    return min([bird for bird , count in bird_count.items() if count==max_count ] ) 

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    arr_count = int(input().strip())
    arr = list(map(int, input().rstrip().split()))
    result = migratoryBirds(arr)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 6 Zig Zag Sequence

```python
  def findZigZagSequence(a, n):
    a.sort()
    mid = int((n - 1)//2)
    a[mid], a[n-1] = a[n-1], a[mid]

    st = mid + 1
    ed = n - 2
    while(st <= ed):
        a[st], a[ed] = a[ed], a[st]
        st = st + 1
        ed = ed - 1

    for i in range (n):
        if i == n-1:
            print(a[i])
        else:
            print(a[i], end = ' ')
    return

test_cases = int(input())
for cs in range (test_cases):
    n = int(input())
    a = list(map(int, input().split()))
    findZigZagSequence(a, n)




```
## 7 tringle perimeter
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'maximumPerimeterTriangle' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY sticks as parameter.
#
def maximumPerimeterTriangle(sticks):
    sticks.sort(reverse=True)
    for i in range(len(sticks)-2):
        a, b, c = sticks[i], sticks[i+1], sticks[i+2]
        if a < b+c:
             return [c,b,a]
    return [-1]

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    sticks = list(map(int, input().rstrip().split()))
    result = maximumPerimeterTriangle(sticks)
    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')
    fptr.close()
```

##7 Drawing Book

```python3
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'pageCount' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER n
#  2. INTEGER p
#

def pageCount(n, p):
    # Write your code here
    # Turns needed from the front
    turns_from_front =p//2
    
    # Turns needed from the back
    turns_from_back = n//2 - p//2
    
    # Return the minimum of the two
    return min(turns_from_front, turns_from_back)

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    p = int(input().strip())
    result = pageCount(n, p)
    fptr.write(str(result) + '\n')
    fptr.close()
```
