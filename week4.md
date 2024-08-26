# Week 4

## 1. Picking Numbers
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'pickingNumbers' function below.
#
# The function is expected to return an INTEGER.
# The function accepts INTEGER_ARRAY a as parameter.
#

def pickingNumbers(a):
    # Step 1: Sort the array
    a.sort()
    
    max_length = 0
    n = len(a)
    
    # Step 2: Iterate through the array
    for i in range(n):
        # Check the length of the subarray where absolute difference between any two elements is <= 1
        current_length = 1
        for j in range(i + 1, n):
            if a[j] - a[i] <= 1:
                current_length += 1
            else:
                break
        # Update the maximum length found
        max_length = max(max_length, current_length)
    
    return max_length



if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    a = list(map(int, input().rstrip().split()))
    result = pickingNumbers(a)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 2 Left Rotation

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'rotateLeft' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts following parameters:
#  1. INTEGER d
#  2. INTEGER_ARRAY arr
#

def rotateLeft(d, arr):
    n = len(arr)
    d = d % n  # Normalize rotations if d >= n
    return arr[d:] + arr[:d]


if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    first_multiple_input = input().rstrip().split()
    n = int(first_multiple_input[0])
    d = int(first_multiple_input[1])
    arr = list(map(int, input().rstrip().split()))
    result = rotateLeft(d, arr)
    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')
    fptr.close()
```

