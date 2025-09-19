# LeetCode Revision Notebook

## Problem 1: Two Sum

**Problem Statement:**
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

**Hints:**

- Use a HashMap for faster lookup
- Think about the complement: `target - nums[i]`

<details>
  <summary><b>Click to view Solution (Python)</b></summary>

```python
# Solution hidden by default
# Expand to view

class Solution:
    def twoSum(self, nums, target):
        lookup = {}
        for i, num in enumerate(nums):
            if target - num in lookup:
                return [lookup[target - num], i]
            lookup[num] = i
```

</details>

---

## Problem 2: Valid Parentheses

**Problem Statement:**
Given a string containing only the characters `'(', ')', '{', '}', '[' and ']'`, determine if the input string is valid.

**Hints:**

- Use a stack
- Match closing brackets with the last open bracket

<details>
  <summary><b>Click to view Solution (Python)</b></summary>

```python
# Solution hidden by default
# Expand to view

class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        mapping = {")": "(", "}": "{", "]": "["}
        for char in s:
            if char in mapping:
                top = stack.pop() if stack else "#"
                if mapping[char] != top:
                    return False
            else:
                stack.append(char)
        return not stack
```

</details>
