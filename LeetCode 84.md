# Largest Rectangle in Histogram — LeetCode 84

## Problem Statement

Given an array of integers `heights` representing the heights of histogram bars, where each bar has a width of `1`, find the area of the largest rectangle in the histogram.

### Example

**Input:**
heights = [2,1,5,6,2,3]

**Output:**
10

The largest rectangle has a height of `5` and a width of `2`.

Area = 5 × 2 = 10

---

## Approach

We use a **Monotonic Stack**.

1. Create an empty stack to store the indices of the bars.
2. Traverse the histogram from left to right.
3. If the current height is smaller than the height at the top of the stack, calculate the rectangle area for the taller bar.
4. Continue removing bars while the current bar is smaller.
5. Calculate the width using the current index and the remaining stack index.
6. Keep track of the maximum area.
7. Add a `0` at the end to process all remaining bars.
8. Return the maximum area.

---

## Code

    class Solution:
        def largestRectangleArea(self, heights):
            stack = []
            max_area = 0

            heights.append(0)

            for i, h in enumerate(heights):

                while stack and heights[stack[-1]] > h:
                    height = heights[stack.pop()]

                    if stack:
                        width = i - stack[-1] - 1
                    else:
                        width = i

                    max_area = max(max_area, height * width)

                stack.append(i)

            return max_area

---

## Time Complexity

**O(n)**

Each element is pushed and popped from the stack at most once.

## Space Complexity

**O(n)**

The stack can store up to `n` indices.
