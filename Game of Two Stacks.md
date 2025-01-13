#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'twoStacks' function below.
#
# The function is expected to return an INTEGER.
# The function accepts following parameters:
#  1. INTEGER maxSum
#  2. INTEGER_ARRAY a
#  3. INTEGER_ARRAY b
#

def twoStacks(maxSum, a, b):
    sum = 0
    count = 0
    i = 0
    j = 0
    while i < len(a) and sum + a[i] <= maxSum:
        sum += a[i]
        i += 1
        count += 1

    max_count = count
    while j < len(b):
        sum += b[j]
        j += 1

        while sum > maxSum and i > 0:
            i -= 1
            sum -= a[i]
            count -= 1

        if sum <= maxSum:
            max_count = max(max_count, i + j)

    return max_count

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    g = int(input().strip())

    for g_itr in range(g):
        first_multiple_input = input().rstrip().split()

        n = int(first_multiple_input[0])

        m = int(first_multiple_input[1])

        maxSum = int(first_multiple_input[2])

        a = list(map(int, input().rstrip().split()))

        b = list(map(int, input().rstrip().split()))

        result = twoStacks(maxSum, a, b)

        fptr.write(str(result) + '\n')

    fptr.close()


#Test case as given in Hackerrank
1
5 4 10
4 2 4 6 1
2 1 8 5
#Output
4
