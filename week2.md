# Week 2
## 1 Lonely Interger
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'lonelyinteger' function below.
#
# The function is expected to return an INTEGER.
# The function accepts INTEGER_ARRAY a as parameter.
#

def lonelyinteger(a):
    dict_count = {}
    for i in a:
        if i in dict_count:
            dict_count[i] += 1
        else:
            dict_count[i] = 1

    for i, value in dict_count.items():
        if value == 1:
            return i
    

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    a = list(map(int, input().rstrip().split()))
    result = lonelyinteger(a)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 2 Grading Students

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'gradingStudents' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY grades as parameter.
#

def gradingStudents(grades):
    # Write your code here
    rounded_grades = []
    
    for grade in grades:
        if grade >= 38:
            next_multiple_of_5 = (grade + 4) // 5 * 5
            if next_multiple_of_5 - grade < 3:
                grade = next_multiple_of_5
        rounded_grades.append(grade)
    
    return rounded_grades

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    grades_count = int(input().strip())

    grades = []

    for _ in range(grades_count):
        grades_item = int(input().strip())
        grades.append(grades_item)

    result = gradingStudents(grades)

    fptr.write('\n'.join(map(str, result)))
    fptr.write('\n')

    fptr.close()

```

## 3 Flipping bits

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'flippingBits' function below.
# The function is expected to return a LONG_INTEGER.
# The function accepts LONG_INTEGER n as parameter.
#

def flippingBits(n):
    return n ^ 0xFFFFFFFF

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    q = int(input().strip())
    for q_itr in range(q):
        n = int(input().strip())
        result = flippingBits(n)
        fptr.write(str(result) + '\n')
    fptr.close()

```

## 4 Diagonal Difference

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'diagonalDifference' function below.
#
# The function is expected to return an INTEGER.
# The function accepts 2D_INTEGER_ARRAY arr as parameter.
#

def diagonalDifference(arr):
    # Write your code here
    n = len(arr)
    primary_diagonal_sum = 0
    secondary_diagonal_sum = 0
    
    for i in range(n):
        primary_diagonal_sum += arr[i][i]
        secondary_diagonal_sum += arr[i][n-1-i]
    
    return abs(primary_diagonal_sum - secondary_diagonal_sum)


if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    arr = []
    for _ in range(n):
        arr.append(list(map(int, input().rstrip().split())))
    result = diagonalDifference(arr)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 5 Counting Sort 1

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'countingSort' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def countingSort(arr):
    # Write your code here
    # Create an array of zeros with 100 elements
    result = [0] * 100
    
    # Iterate through the input array and update the frequency array
    for num in arr:
        result[num] += 1
    
    return result

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    arr = list(map(int, input().rstrip().split()))
    result = countingSort(arr)
    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')
    fptr.close()
```

## 6 Counting Valleys

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'countingValleys' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER steps
#  2. STRING path
#

def countingValleys(steps, path):
    # Write your code here
    altitude = 0
    valleys = 0
    in_valley = False

    for step in path:
        if step == 'U':
            altitude += 1
        elif step == 'D':
            altitude -= 1

        if altitude < 0 and not in_valley:
            in_valley = True
        if altitude >= 0 and in_valley:
            valleys += 1
            in_valley = False
    
    return valleys

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    steps = int(input().strip())
    path = input()
    result = countingValleys(steps, path)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 7 Pangrams

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'pangrams' function below.
#
# The function is expected to return a STRING.
# The function accepts STRING s as parameter.
#

def pangrams(s):
    # Write your code here
    # Convert the string to lowercase to handle case insensitivity
    s = s.lower()
    
    # Create a set of all the letters in the alphabet
    alphabet_set = set('abcdefghijklmnopqrstuvwxyz')
    
    # Create a set of all the letters in the string
    string_set = set(s)
    
    # Check if all alphabet letters are present in the string
    if alphabet_set.issubset(string_set):
        return 'pangram'
    else:
        return 'not pangram'

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    s = input()
    result = pangrams(s)
    fptr.write(result + '\n')
    fptr.close()
```

## 8 Mars Exploration

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'marsExploration' function below.
#
# The function is expected to return an INTEGER.
# The function accepts STRING s as parameter.
#

def marsExploration(s):
    # Write your code here
    # Define the SOS pattern
    pattern = "SOS"
    
    # Initialize a counter for the number of changes
    changes = 0
    
    # Iterate through the received message
    for i in range(len(s)):
        # Calculate the corresponding character in the SOS pattern
        if s[i] != pattern[i % 3]:
            changes += 1
    
    return changes

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    s = input()
    result = marsExploration(s)
    fptr.write(str(result) + '\n')
    fptr.close()
```
