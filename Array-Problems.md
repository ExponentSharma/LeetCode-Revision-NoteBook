# 🚀 Arrays Revision Notebook


## 🧩 Problem 1: Two Sum

**Problem Statement:**  
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

**Example:**  
Input: `nums = [2,7,11,15], target = 9`  
Output: `[0,1]`  

**Hints:**  
- ⚡ Use a HashMap for faster lookup  
- 🧠 Think about the complement: `target - nums[i]`  

<details>
  <summary><b>💡 Click to view Solution (Java)</b></summary>

```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[] {}; // no solution case
    }
}
