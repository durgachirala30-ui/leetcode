# Contains Duplicate II — LeetCode 219

## Problem Statement

Given an integer array `nums` and an integer `k`, return `true` if there are two distinct indices `i` and `j` such that:

`nums[i] == nums[j]`

and:

`abs(i - j) <= k`

Otherwise, return `false`.

### Example

**Input:**
nums = [1,2,3,1]
k = 3

**Output:**
true

---

## Approach

We use a **Hash Map (Dictionary)** to store the most recent index of each number.

1. Create an empty dictionary `seen`.
2. Traverse the array using index `i`.
3. Check if `nums[i]` already exists in `seen`.
4. If it exists, calculate the difference between the current index and previous index.
5. If the difference is less than or equal to `k`, return `True`.
6. Update the index of the current number.
7. If no valid duplicate is found, return `False`.

---

## Code

    class Solution:
        def containsNearbyDuplicate(self, nums, k):
            seen = {}

            for i in range(len(nums)):
                if nums[i] in seen:
                    if i - seen[nums[i]] <= k:
                        return True

                seen[nums[i]] = i

            return False

---

## Time Complexity

**O(n)**

We traverse the array once.

## Space Complexity

**O(n)**

The dictionary can store up to `n` elements.
