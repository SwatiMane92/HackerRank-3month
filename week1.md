# Wee1 

## 1. Plus Minus

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'plusMinus' function below.
#
# The function accepts INTEGER_ARRAY arr as parameter.
#

def plusMinus(arr):
    # Write your code here
    # Initialize counters
    positive_count = 0
    negative_count = 0
    zero_count = 0
    
    # Count the positive, negative, and zero values
    for num in arr:
        if num > 0:
            positive_count += 1
        elif num < 0:
            negative_count += 1
        else:
            zero_count += 1
    
    # Calculate the ratios
    total = len(arr)
    positive_ratio = positive_count / total
    negative_ratio = negative_count / total
    zero_ratio = zero_count / total
    
    # Print the ratios with 6 decimal places
    print(f"{positive_ratio:.6f}")
    print(f"{negative_ratio:.6f}")
    print(f"{zero_ratio:.6f}")

if __name__ == '__main__':
    n = int(input().strip())
    arr = list(map(int, input().rstrip().split()))
    plusMinus(arr)
```

## 2 Mini-Max Sum
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'miniMaxSum' function below.
#
# The function accepts INTEGER_ARRAY arr as parameter.
#

def miniMaxSum(arr):
    # Write your code here
    total_sum = sum(arr)
    
    # Find the minimum and maximum values in the array
    min_value = min(arr)
    max_value = max(arr)
    
    # Calculate the minimum sum (exclude the maximum element)
    min_sum = total_sum - max_value
    
    # Calculate the maximum sum (exclude the minimum element)
    max_sum = total_sum - min_value
    
    # Print the results as space-separated integers
    print(min_sum, max_sum)

if __name__ == '__main__':
    arr = list(map(int, input().rstrip().split()))
    miniMaxSum(arr)
```

## 3 Time Conversion
```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'timeConversion' function below.
#
# The function is expected to return a STRING.
# The function accepts STRING s as parameter.
#

def timeConversion(s):
    # Write your code here
    # Extract the hour, minute, second and period (AM/PM)
    period = s[-2:]
    hour = int(s[:2])
    minute = s[3:5]
    second = s[6:8]

    if period == 'AM':
        # Convert 12 AM to 00
        if hour == 12:
            hour = 0
    else:
        # Convert PM to 24-hour format
        if hour != 12:
            hour += 12

    # Format the hour to be two digits (e.g., 01, 02, etc.)
    hour = f'{hour:02}'

    # Return the formatted time in 24-hour format
    return f'{hour}:{minute}:{second}'

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    s = input()
    result = timeConversion(s)
    fptr.write(result + '\n')
    fptr.close()
```

## 4 Breaking the Records

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'breakingRecords' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY scores as parameter.
#

def breakingRecords(scores):
    # Write your code here
    max_score = scores[0]
    min_score = scores[0]
    max_count = 0
    min_count = 0
    
    # Iterate through the scores starting from the second game
    for score in scores[1:]:
        if score > max_score:
            max_score = score
            max_count += 1
        elif score < min_score:
            min_score = score
            min_count += 1
    
    # Return the counts as a list [max_count, min_count]
    return [max_count, min_count]

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    n = int(input().strip())
    scores = list(map(int, input().rstrip().split()))
    result = breakingRecords(scores)
    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')
    fptr.close()
```

## 5 Camel Case 4

```python
# Enter your code here. Read input from STDIN. Print output to STDOUT
import sys

def camel_case_operations(input_string):
    operation, item_type, value = input_string.split(';')
    
    if operation == 'S':  # Split operation
        if item_type == 'M':
            value = value[:-2]  # Remove '()' from the method name
        words = []
        current_word = ''
        for char in value:
            if char.isupper():
                if current_word:
                    words.append(current_word.lower())
                current_word = char
            else:
                current_word += char
        words.append(current_word.lower())
        print(' '.join(words))
        
    elif operation == 'C':  # Combine operation
        words = value.split()
        if item_type == 'C':
            words = [words[0].capitalize()] + [word.capitalize() for word in words[1:]]
        elif item_type == 'M':
            words = [words[0]] + [word.capitalize() for word in words[1:]]
            words[-1] += '()'
        else:  # Variable
            words = [words[0]] + [word.capitalize() for word in words[1:]]
        print(''.join(words))

# Read input from STDIN
input_data = sys.stdin.read().strip().splitlines()

# Process each line of input
for input_str in input_data:
    camel_case_operations(input_str)
```

## 6 Divisible Sum Pairs

```python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'divisibleSumPairs' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER n
#  2. INTEGER k
#  3. INTEGER_ARRAY ar
#

def divisibleSumPairs(n, k, ar):
    # Write your code here
    count = 0
    # Iterate over each pair (i, j) where i < j
    for i in range(n):
        for j in range(i + 1, n):
            # Check if the sum of the pair is divisible by k
            if (ar[i] + ar[j]) % k == 0:
                count += 1
    return count

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    first_multiple_input = input().rstrip().split()
    n = int(first_multiple_input[0])
    k = int(first_multiple_input[1])
    ar = list(map(int, input().rstrip().split()))
    result = divisibleSumPairs(n, k, ar)
    fptr.write(str(result) + '\n')
    fptr.close()
```

## 7 Sparse Arrays

```python

#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'matchingStrings' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts following parameters:
#  1. STRING_ARRAY strings
#  2. STRING_ARRAY queries
#

def matchingStrings(strings, queries):
    result = []
    for query in queries:
        count = strings.count(query)
        result.append(count)
    return result


if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    strings_count = int(input().strip())

    strings = []

    for _ in range(strings_count):
        strings_item = input()
        strings.append(strings_item)

    queries_count = int(input().strip())

    queries = []

    for _ in range(queries_count):
        queries_item = input()
        queries.append(queries_item)

    res = matchingStrings(strings, queries)

    fptr.write('\n'.join(map(str, res)))
    fptr.write('\n')

    fptr.close()

```
