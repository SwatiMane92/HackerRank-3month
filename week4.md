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
## 3 Number Line Jumps
The problem you're dealing with involves two kangaroos on a number line. Each kangaroo starts at a specific position and jumps forward a certain distance with each jump. You need to determine if there is a point where both kangaroos will land on the same position at the same time after making the same number of jumps.

### Goal:
You need to check if there exists a non-negative integer `n` such that:
 x1 + n  v1 = x2 + n v2 

Simplifying the equation:
 x1 - x2 = n (v2 - v1) 

This can be further simplified to:
 n = {x1 - x2}/{v2 - v1} 

### Conditions for YES:

1. **Divisibility:** For `n` to be an integer (number of jumps), the difference `(x1 - x2)` must be divisible by `(v2 - v1)`.
  
2. **Positive n:** The number of jumps `n` must be non-negative, i.e., `n >= 0`.



```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'kangaroo' function below.
#
# The function is expected to return a STRING.
# The function accepts following parameters:
#  1. INTEGER x1
#  2. INTEGER v1
#  3. INTEGER x2
#  4. INTEGER v2
#

def kangaroo(x1, v1, x2, v2):
    # Write your code here
    if v1 != v2:
        n = (x2 - x1) / (v1 - v2)
        if n >= 0 and n.is_integer():
            return "YES"
    return "NO"

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    first_multiple_input = input().rstrip().split()
    x1 = int(first_multiple_input[0])
    v1 = int(first_multiple_input[1])
    x2 = int(first_multiple_input[2])
    v2 = int(first_multiple_input[3])
    result = kangaroo(x1, v1, x2, v2)
    fptr.write(result + '\n')
    fptr.close()
```

# 4 Separate the Numbers

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'separateNumbers' function below.
#
# The function accepts STRING s as parameter.
#

def separateNumbers(s):
    n = len(s)
    
    # Try to find a beautiful sequence starting with different lengths
    for length in range(1, n//2 + 1):
        # Get the first number from the string
        first_number = int(s[:length])
        expected = str(first_number)
        next_number = first_number + 1
        
        # Build the expected sequence
        while len(expected) < n:
            expected += str(next_number)
            next_number += 1
        
        # Check if the built sequence matches the original string
        if expected == s:
            print("YES", first_number)
            return
    
    # If no valid sequence is found, print NO
    print("NO")

if __name__ == '__main__':
    q = int(input().strip())
    for q_itr in range(q):
        s = input()
        separateNumbers(s)
```
# 5 Closest Numbers

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'closestNumbers' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def closestNumbers(arr):
    arr.sort()  # Step 1: Sort the array
    min_diff = float('inf')  # Initialize min_diff with a large number
    result = []
    
    # Step 2: Find the minimum difference
    for i in range(len(arr) - 1):
        diff = arr[i + 1] - arr[i]
        if diff < min_diff:
            min_diff = diff
            result = [arr[i], arr[i + 1]]  # Start a new result list
        elif diff == min_diff:
            result.extend([arr[i], arr[i + 1]])  # Add to the result list
    
    return result

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    arr = list(map(int, input().rstrip().split()))
    result = closestNumbers(arr)
    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')
    fptr.close()
```

## 6 Tower Breakers

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'towerBreakers' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER n
#  2. INTEGER m
#

def towerBreakers(n, m):
    # If tower height is 1, player 2 always wins
    if m == 1:
        return 2
    # If the number of towers is even, player 2 wins by mirroring moves
    if n % 2 == 0:
        return 2
    # Otherwise, player 1 wins
    else:
        return 1

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    t = int(input().strip())
    for t_itr in range(t):
        first_multiple_input = input().rstrip().split()
        n = int(first_multiple_input[0])
        m = int(first_multiple_input[1])
        result = towerBreakers(n, m)
        fptr.write(str(result) + '\n')
    fptr.close()
```

## 7 Minimum Absolute Difference in an Array

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'minimumAbsoluteDifference' function below.
#
# The function is expected to return an INTEGER.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def minimumAbsoluteDifference(arr):
    arr.sort()  # Step 1: Sort the array
    min_diff = float('inf')  # Initialize to a very large number
    
    for i in range(1, len(arr)-1):
        diff = abs(arr[i+1] - arr[i])  # Step 2: Find difference between consecutive elements
        min_diff = min(min_diff, diff)  # Update minimum difference if the current one is smaller
    
    return min_diff

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    arr = list(map(int, input().rstrip().split()))
    result = minimumAbsoluteDifference(arr)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 8 Caesar Cipher
### Example:
If `char = 'b'`, `k = 3`, and `shift = ord('a')`:
- `ord('b') - ord('a') = 98 - 97 = 1` (position of 'b' is 1).
- Add `k`: `1 + 3 = 4` (move 3 positions to the right).
- `% 26` keeps it within the alphabet (though it's not needed here as 4 is already within the range).
- `4 + ord('a') = 4 + 97 = 101`.
- `chr(101)` gives `'e'`.

So, `'b'` shifted by 3 positions becomes `'e'`.

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'caesarCipher' function below.
#
# The function is expected to return a STRING.
# The function accepts following parameters:
#  1. STRING s
#  2. INTEGER k
#

def caesarCipher(s, k):
    result = []  # This will store the encrypted characters
    k = k % 26  # To handle cases where k is larger than 26

    for char in s:
        if char.isalpha():  # Check if the character is a letter
            shift = ord('a') if char.islower() else ord('A')
            # Shift the character by k positions
            new_char = chr((ord(char) - shift + k) % 26 + shift)
            result.append(new_char)
        else:
            result.append(char)  # If not a letter, keep it the same

    return ''.join(result)  # Combine the list into a string

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    s = input()
    k = int(input().strip())
    result = caesarCipher(s, k)
    fptr.write(result + '\n')
    fptr.close()
```
