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
# The function accepts STRING expression as parameter.
#

def isBalanced(expression):
    # Write your code here
    map = {')': '(', '}': '{', ']': '['}
    stack = []
    for c in expression:
        if c in map.values(): 
            stack.append(c)
            
        elif c in map:  
            if stack and stack[-1] == map[c]:
                stack.pop() 
            else:
                return "NO"  
        else:
            return "NO"  
    return "YES" if not stack else "NO"

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    t = int(input().strip())

    for t_itr in range(t):
        expression = input()

        res = isBalanced(expression)

        fptr.write(res + '\n')

    fptr.close()

#Test Case as per Hackerrank
3
{[()]}
{[(])}
{{[[(())]]}}
# output
YES
NO
YES
