# Implement Queue using Stacks — LeetCode 232

## Problem Statement

Implement a queue using two stacks.

The queue should support the following operations:

- `push(x)` — Add an element to the queue.
- `pop()` — Remove and return the element from the front.
- `peek()` — Return the element at the front.
- `empty()` — Return `true` if the queue is empty.

A queue follows **FIFO (First In, First Out)**.

### Example

**Input:**
push(1)
push(2)
peek()
pop()
empty()

**Output:**
1
1
false

---

## Approach

We use **two stacks**: `stack1` and `stack2`.

1. Add new elements to `stack1`.
2. For `pop()` and `peek()`, check whether `stack2` is empty.
3. If `stack2` is empty, move all elements from `stack1` to `stack2`.
4. This reverses the order of the elements.
5. The top of `stack2` becomes the front of the queue.
6. For `empty()`, check whether both stacks are empty.

---

## Code

    class MyQueue:

        def __init__(self):
            self.stack1 = []
            self.stack2 = []

        def push(self, x):
            self.stack1.append(x)

        def pop(self):
            self.move()
            return self.stack2.pop()

        def peek(self):
            self.move()
            return self.stack2[-1]

        def empty(self):
            return len(self.stack1) == 0 and len(self.stack2) == 0

        def move(self):
            if not self.stack2:
                while self.stack1:
                    self.stack2.append(self.stack1.pop())

---

## Time Complexity

**Push:** O(1)

**Pop:** O(1) amortized

**Peek:** O(1) amortized

## Space Complexity

**O(n)**

The two stacks can store up to `n` elements.
