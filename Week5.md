# Week 5

## 1 Max Min

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'maxMin' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER k
#  2. INTEGER_ARRAY arr
#

def maxMin(k, arr):
    # Step 1: Sort the array
    arr.sort()
    
    # Step 2: Initialize the minimum unfairness to a large number
    min_unfairness = float('inf')
    
    # Step 3: Slide over the sorted array to find the minimum difference
    for i in range(len(arr) - k + 1):
        unfairness = arr[i + k - 1] - arr[i]
        if unfairness < min_unfairness:
            min_unfairness = unfairness
    
    # Step 4: Return the minimum unfairness
    return min_unfairness

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    k = int(input().strip())
    arr = []
    for _ in range(n):
        arr_item = int(input().strip())
        arr.append(arr_item)
    result = maxMin(k, arr)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 2 Strong Password
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'minimumNumber' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER n
#  2. STRING password
#

def minimumNumber(n, password):
    # Character sets to check
    numbers = "0123456789"
    lower_case = "abcdefghijklmnopqrstuvwxyz"
    upper_case = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    special_characters = "!@#$%^&*()-+"

    # Flags to check if the password contains required characters
    has_digit = False
    has_lower = False
    has_upper = False
    has_special = False

    # Check each character in the password
    for char in password:
        if char in numbers:
            has_digit = True
        elif char in lower_case:
            has_lower = True
        elif char in upper_case:
            has_upper = True
        elif char in special_characters:
            has_special = True

    # Count the missing character types
    count_missing_types = 0
    if not has_digit:
        count_missing_types += 1
    if not has_lower:
        count_missing_types += 1
    if not has_upper:
        count_missing_types += 1
    if not has_special:
        count_missing_types += 1

    # Calculate the minimum number of characters to add
    return max(count_missing_types, 6 - n)
if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    password = input()
    answer = minimumNumber(n, password)
    fptr.write(str(answer) + '\n')
    fptr.close()
```

## 3 Dynamic Array

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'dynamicArray' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts following parameters:
#  1. INTEGER n
#  2. 2D_INTEGER_ARRAY queries
#

def dynamicArray(n, queries):
    # Create an empty 2D array
    arr = [[] for _ in range(n)]
    
    # Initialize the variable for the last answer
    last_ans = 0
    
    # List to store results of type 2 queries
    results = []
    
    # Process each query
    for query in queries:
        query_type, x, y = query
        
        # Calculate the index based on x and last_ans
        idx = (x ^ last_ans) % n
        
        if query_type == 1:
            # Append y to the selected array
            arr[idx].append(y)
        elif query_type == 2:
            # Assign value and store result
            last_ans = arr[idx][y % len(arr[idx])]
            results.append(last_ans)
    
    return results

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    first_multiple_input = input().rstrip().split()
    n = int(first_multiple_input[0])
    q = int(first_multiple_input[1])
    queries = []
    for _ in range(q):
        queries.append(list(map(int, input().rstrip().split())))
    result = dynamicArray(n, queries)
    fptr.write('\n'.join(map(str, result)))
    fptr.write('\n')
    fptr.close()
```

## 4 Smart Number 2

```python
import math

def is_smart_number(num):
    val = int(math.sqrt(num))
    if val * val == num:
        return True
    return False

for _ in range(int(input())):
    num = int(input())
    ans = is_smart_number(num)
    if ans:
        print("YES")
    else:
        print("NO")
```

## 5 Missing Numbers

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'missingNumbers' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts following parameters:
#  1. INTEGER_ARRAY arr
#  2. INTEGER_ARRAY brr
#

def missingNumbers(arr, brr):
    # Create dictionaries to count frequencies
    arr_count = {}
    brr_count = {}
    
    # Count frequencies in arr
    for num in arr:
        if num in arr_count:
            arr_count[num] += 1
        else:
            arr_count[num] = 1
    
    # Count frequencies in brr
    for num in brr:
        if num in brr_count:
            brr_count[num] += 1
        else:
            brr_count[num] = 1
    
    # Find missing numbers
    missing = []
    for num in brr_count:
        if brr_count[num] > arr_count.get(num, 0):
            missing.append(num)
    
    # Sort and return the missing numbers
    missing.sort()
    return missing

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    arr = list(map(int, input().rstrip().split()))
    m = int(input().strip())
    brr = list(map(int, input().rstrip().split()))
    result = missingNumbers(arr, brr)
    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')
    fptr.close()
```

## 6 The Full Counting Sort

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'countSort' function below.
#
# The function accepts 2D_STRING_ARRAY arr as parameter.
#

def countSort(arr):
    # Determine the maximum integer value to define the size of the helper array
    max_int = max(int(pair[0]) for pair in arr)
    
    # Create a list of empty lists (buckets) for each integer value
    buckets = [[] for _ in range(max_int + 1)]
    
    # Populate the buckets with strings, replacing the first half with '-'
    for i, (num, string) in enumerate(arr):
        num = int(num)
        if i < len(arr) // 2:
            buckets[num].append('-')
        else:
            buckets[num].append(string)
    
    # Flatten the list of buckets and print the result
    result = []
    for bucket in buckets:
        result.extend(bucket)
    
    print(' '.join(result))

if __name__ == '__main__':
    n = int(input().strip())
    arr = []
    for _ in range(n):
        arr.append(input().rstrip().split())
    countSort(arr)
```

## 7 Grid Challenge
One test case is failed but it's okay not think more
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'gridChallenge' function below.
#
# The function is expected to return a STRING.
# The function accepts STRING_ARRAY grid as parameter.
#

def gridChallenge(grid):
    # Sort each row alphabetically
    sorted_grid = [''.join(sorted(row)) for row in grid]
    
    # Check if columns are in alphabetical order
    n = len(sorted_grid)
    for col in range(n):
        for row in range(1, n):
            if sorted_grid[row][col] < sorted_grid[row - 1][col]:
                return "NO"
    
    return "YES"
    
if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    t = int(input().strip())
    for t_itr in range(t):
        n = int(input().strip())
        grid = []
        for _ in range(n):
            grid_item = input()
            grid.append(grid_item)
        result = gridChallenge(grid)
        fptr.write(result + '\n')
    fptr.close()
```

## 8 Sansa and XOR

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'sansaXor' function below.
#
# The function is expected to return an INTEGER.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def sansaXor(arr):
    result = 0
    n = len(arr)
    
    for i in range(n):
        # Count the number of subarrays in which arr[i] appears
        count = (i + 1) * (n - i)
        # If the count is odd, include arr[i] in the final result
        if count % 2 == 1:
            result ^= arr[i]
    
    return result

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    t = int(input().strip())
    for t_itr in range(t):
        n = int(input().strip())
        arr = list(map(int, input().rstrip().split()))
        result = sansaXor(arr)
        fptr.write(str(result) + '\n')
    fptr.close()
```
