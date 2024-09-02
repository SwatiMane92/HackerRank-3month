# Week 6

## 2 Sherlock and Array

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'balancedSums' function below.
#
# The function is expected to return a STRING.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def balancedSums(arr):
    total_sum = sum(arr)  # Step 1: Compute the total sum
    left_sum = 0  # Initialize left_sum to 0
    
    for num in arr:  # Step 2: Iterate through the array
        # Compute the right_sum as total_sum minus the current element and left_sum
        right_sum = total_sum - left_sum - num
        
        if left_sum == right_sum:  # Step 3: Check if left_sum equals right_sum
            return "YES"
        
        left_sum += num  # Update the left_sum for the next iteration
    
    return "NO"  # Step 4: If no index found, return "NO"

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    T = int(input().strip())
    for T_itr in range(T):
        n = int(input().strip())
        arr = list(map(int, input().rstrip().split()))
        result = balancedSums(arr)
        fptr.write(result + '\n')

    fptr.close()
```


## 4 Gaming Array 1

```python
#!/bin/python3

import os

#
# Complete the 'gamingArray' function below.
#
# The function is expected to return a STRING.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def gamingArray(arr):
    max_elem = float('-inf')
    moves = 0
   
    for num in arr:
        if num > max_elem:
            max_elem = num
            moves += 1
   
    return "BOB" if moves % 2 == 1 else "ANDY"

if __name__ == '__main__':
    # Read number of games
    t = int(input().strip())
    results = []
   
    for _ in range(t):
        n = int(input().strip())
        arr = list(map(int, input().strip().split()))
        result = gamingArray(arr)
        results.append(result)
   
    # Write results to the output
    with open(os.environ['OUTPUT_PATH'], 'w') as fptr:
        fptr.write('\n'.join(results) + '\n')
```

## 5 Forming a Magic Square

A 3x3 magic square is a 3x3 grid filled with distinct integers from 1 to 9 such that the sum of the numbers in each row, column, and diagonal is always the same. This common sum is known as the magic constant, which is 15 for a 3x3 magic square.

```python
```

## 6 Recursive

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'superDigit' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. STRING n
#  2. INTEGER k
#

def superDigit(n, k):
    # Write your code here
    def find_super_digit(x):
        if x < 10:
            return x
        digit_sum=sum(int(i) for i in str(x))
        return find_super_digit(digit_sum)
    initial_sum=sum(int(i) for i in n)
    effective_sum=initial_sum * k
    return find_super_digit(effective_sum)
    

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    first_multiple_input = input().rstrip().split()

    n = first_multiple_input[0]

    k = int(first_multiple_input[1])

    result = superDigit(n, k)

    fptr.write(str(result) + '\n')

    fptr.close()
```

