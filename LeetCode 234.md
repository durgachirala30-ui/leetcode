# Palindrome Linked List — LeetCode 234

## Problem Statement

Given the head of a singly linked list, return `true` if the linked list is a palindrome.

A palindrome is a sequence that reads the same forward and backward.

### Example

**Input:**
head = [1,2,2,1]

**Output:**
true

### Example 2

**Input:**
head = [1,2]

**Output:**
false

---

## Approach

We use **Fast and Slow Pointers** and reverse the second half of the linked list.

1. Create two pointers, `slow` and `fast`.
2. Move `slow` one step at a time.
3. Move `fast` two steps at a time.
4. When `fast` reaches the end, `slow` will be at the middle.
5. Reverse the second half of the linked list.
6. Compare the first half with the reversed second half.
7. If all values are equal, return `True`.
8. Otherwise, return `False`.

---

## Code

    class Solution:
        def isPalindrome(self, head):

            slow = head
            fast = head

            # Find the middle
            while fast and fast.next:
                slow = slow.next
                fast = fast.next.next

            # Reverse the second half
            prev = None

            while slow:
                next_node = slow.next
                slow.next = prev
                prev = slow
                slow = next_node

            # Compare both halves
            left = head
            right = prev

            while right:
                if left.val != right.val:
                    return False

                left = left.next
                right = right.next

            return True

---

## Time Complexity

**O(n)**

We traverse the linked list a constant number of times.

## Space Complexity

**O(1)**

Only a few pointers are used.
