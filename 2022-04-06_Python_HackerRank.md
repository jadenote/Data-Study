# Python_HackerRank_If-Else

### Problem

Task
Given an integer, , perform the following conditional actions:

If  is odd, print Weird
If  is even and in the inclusive range of  to , print Not Weird
If  is even and in the inclusive range of  to , print Weird
If  is even and greater than , print Not Weird




Input Format

A single line containing a positive integer, .

Constraints

Output Format

Print Weird if the number is weird. Otherwise, print Not Weird.

### Solution


```python

import math
import os
import random
import re
import sys

n = int(input())

if n %2 != 0 :
    print("Weird")
if n %2 == 0 and 2 <= n <= 5 :
    print("Not Weird")
if n %2 == 0 and 6 <= n <= 20 :
    print("Weird")
if n %2 == 0 and 20 < n :
    print("Not Weird")
```
