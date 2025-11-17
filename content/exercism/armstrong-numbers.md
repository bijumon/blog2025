---
title: Armstrong Numbers
date: 2025-06-27T18:27:39+05:30
---

``` python
"""
Determine whether a number is an Armstrong number
"""

def is_armstrong_number(number):
    digits = [int(d) for d in str(number)]

    length = len(digits)
    total = 0
    for num in digits:
        total += (num ** length)
    return number == total

```
