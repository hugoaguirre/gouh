+++
title = 'DSA: Two Pointers'
date = 2024-09-06T22:31:48-06:00
draft = false
+++

Two Pointer is basically what the name says. You've got to use two variables to track positions within an array or linked-lists.

This approach excels in the following:

## Data structures

- Arrays (sorted or unsorted)
- Linked lists

## Problem types

- Find a set of elements that fulfill certain constraints
  - Pairs, Triplets, Sub-arrays.

The most common problem types you'll encounter are something like this:

> Given an array of numbers and a target sum, find a pair in the array whose sum is equal to the given target.

> Given an array of unsorted numbers and a target number, find a triplet in the array whose sum is as close to the target number as possible.

## Tips and observations

I think the idea is pretty clear right? Either the array is sorted or not, you could always sort it with a pre-built in function and start manipulating the pointers at your wish.

A rule of thumb that I've been telling myself to follow is to **never name those pointers `i` and `j`**. Instead, name them `left` and `right`. Those names are much clear and will simplify things in your head.

## Common code structure

For simplicity sake, I'll write things in Python.

### Pointer at the beginning and end of an array

```python
from typing import List

def bothSides(arr: List[int]):
  """
    Dummy function that illustrates how to travel into an array using the Two Pointers approach.

    left pointer begins at position 0
    right pointer begins at the end of the array

    Based on problem-specific conditions the pointers will eventually meet each other, that's where the loop ends.
  """
  left = 0
  right = len(arr) - 1 

  # while loop stops when both pointers are at the same place 
  while left < right:
    if some_condition:
      left += 1
    else:
      right -= 1

  return
```

### One main index and pointers at both ends

```python
from typing import List

def mainIndexBothSides(arr: List[int]):
  """
    Dummy function that illustrates how to travel into an array using a main index and Two Pointers approach.

    idx pointer acts as a control pointer
    left pointer usually starts after `idx`
    right pointer begins at the end of the array
  """
  # Let's assume we are trying to get all triplets in the array [arr[i], arr[left], arr[right]]
  for i in range(len(arr)-2):
    right = len(arr) - 1
    left = i + 1 

    while left < right:
      if some_coindition:
        left += 1
      else:
        right -= 1
  return
```

### Right pointer pulls Left pointer

```python
from typing import List

def rightPullsLeft(arr: List[int]):
  """
    Dummy function that illustrates how right pointer pulls left pointer based on a condition

    left pointer increments only when right pointer encounters something
    right pointer starts at the beginning (same as left pointer)

    Pretty useful for subsequences-type problems (Leetcode #392)
  """
  left, right = 0, 0

  while right < len(arr):
    if some_condition:
      right += 1
      left += 1
    else:
      right += 1
```

Alright, that's it for Two Pointers.

Keep grinding!
