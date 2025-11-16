---
title: Collatz Conjecture
date: 2025-06-27T18:27:39+05:30
---

``` python
"""
Given a positive integer, return the number of steps it takes to reach 1 according to the rules of the Collatz Conjecture.
"""

def steps(number):
    step = 0
    if number > 0:
        while number > 1:
            step += 1
            if number % 2 == 0:
                number = number / 2
            else:
                number = (number * 3) + 1
    else:
        raise ValueError("Only positive integers are allowed")
    return step

```
