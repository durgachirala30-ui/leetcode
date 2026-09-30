# Odd Even Linked List — LeetCode 328

## Problem Statement

Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices.

The first node is considered to have index `1`.

The relative order inside the odd and even groups should remain the same.

### Example

**Input:**
head = [1,2,3,4,5]

**Output:**
[1,3,5,2,4]

---

## Approach

We use two pointers: `odd` and `even`.

1. Set `odd` to the first node.
2. Set `even` to the second node.
3. Store the first even node in `even_head`.
4. Connect the odd nodes together.
5. Connect the even nodes together.
6. Move the `odd` and `even` pointers forward.
7. Continue until the even list reaches the end.
8. Attach the even list after the odd list.
9. Return the original head.

For example:

`1 → 2 → 3 → 4 → 5`

Odd nodes:

`1 → 3 → 5`

Even nodes:

`2 → 4`

Final list:

`1 → 3 → 5 → 2 → 4`

---

## Code

    class Solution:
        def oddEvenList(self, head):

            if not head or not head.next:
                return head

            odd = head
            even = head.next
            even_head = even

            while even and even.next:

                odd.next = even.next
                odd = odd.next

                even.next = odd.next
                even = even.next

            odd.next = even_head

            return head

---

## Time Complexity

**O(n)**

We traverse the linked list once.

## Space Complexity

**O(1)**

Only a few pointers are used.
