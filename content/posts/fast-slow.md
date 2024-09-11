+++
title = 'Fast and Slow pointers'
date = 2024-09-10T21:30:06-06:00
draft = false
+++

This is a pattern that uses two pointers approach, however there's a special thing about this pattern:
- One pointer moves faster than the other.

The Fast and Slow pattern follows the [Hare and Tortoise algorithm](https://en.wikipedia.org/wiki/Cycle_detection).

The algorithm is pretty useful when dealing with cyclic Linked lists or arrays. It actually proves that by moving the pointers in that way they will be at the same position at some point in time.

So, the algorithm excels on finding a cycle in a linked list:

## Check if a linked list has a cycle

```python
class Node:
  def __init__(self, value, next=None):
    self.value = value
    self.next = next

def hasCycle(head: Node) -> bool:
  # two pointers, fast (hare) and slow (tortoise):
  fast, slow = head, head

  while fast is not None and fast.next is not None:
    fast = fast.next.next  # two jumps
    slow = slow.next       # one small step

    # the algorithm proves both pointers will meet at some point
    if fast == slow:
      return True

  return False
```


Also the algorithm helps us to find the middle Node of a linked list in `O(N)` time complexity and time `O(1)` constant space

## Find mid point of a linked list

```python
class Node:
  def __init__(self, value, next=None):
    self.value = value
    self.next = next

def findMiddle(head: Node) -> Node:
  fast, slow = head, head

  # if no cycle, fast will be None at the time slow reaches the mid point of the linked list
  while fast is not None and fast.next is not None:
    fast = fast.next.next
    slow = slow.next

  return slow
```

So, with this said, we can calculate the node that starts the cycle in a linked list

## Determine which node starts the cycle in a linked list

```python
class Node:
  def __init__(self, value, next=None):
    self.value = value
    self.next = next

def findCycleStart(head: Node) -> Node:
  fast, slow = head, head

  while fast is not None and fast.next is not None:
    fast = fast.next.next
    slow = slow.next

    # cycle found
    if fast == slow:
      cycle_length = findCycleLength(slow)
      break

  return getCycleStart(head, cycle_length)

def findCycleLength(slow: Node) -> int:
  current = slow
  cycle_length = 0

  # since we are in a cycle, break when both pointers meet again
  while True:
    current = current.next
    cycle_length += 1

    if current == slow:
      break

  return cycle_length


def getCycleStart(head: Node, cycle_length: int) -> Node:
  fast, slow = head, head

  # move fast pointer  `cycle_length` jumps and pointers will meet again
  while cycle_length > 0:
    fast = fast.next
    cycle_length -= 1

  # one step at a time
  while fast != slow:
    fast = fast.next
    slow = slow.next

  return slow
```
