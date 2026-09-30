# Product of Array Except Self — LeetCode 238

## Problem Statement

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

The solution must run in **O(n)** time and should not use division.

### Example

**Input:**
nums = [1,2,3,4]

**Output:**
[24,12,8,6]

---

## Approach

We use **prefix and suffix products**.

1. Create an `answer` array filled with `1`.
2. Traverse the array from left to right.
3. Store the product of all elements before the current index.
4. Traverse the array from right to left.
5. Multiply each position by the product of all elements after it.
6. Return the `answer` array.

---

## Code

    class Solution:
        def productExceptSelf(self, nums):
            n = len(nums)
            answer = [1] * n

            prefix = 1

            for i in range(n):
                answer[i] = prefix
                prefix *= nums[i]

            suffix = 1

            for i in range(n - 1, -1, -1):
                answer[i] *= suffix
                suffix *= nums[i]

            return answer

---

## Time Complexity

**O(n)**

We traverse the array twice.

## Space Complexity

**O(1)**

Only a few variables are used apart from the output array.
