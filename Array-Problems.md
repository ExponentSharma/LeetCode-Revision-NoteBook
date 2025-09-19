# 🚀 Arrays Revision Notebook

## 🧩 Problem 1: Two Sum

**Problem Statement:**  
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

**Example:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
```

**Hints:**

- ⚡ Use a HashMap for faster lookup
- 🧠 Think about the complement: `target - nums[i]`

**Complexity:**

- ⏱️ Time: **O(n)**
- 💾 Space: **O(n)** (HashMap stores up to n elements)

<details>
  <summary><b>💡1) Brute Force (Nested Loops)</b></summary>

```JAVA
class Solution {
    public int[] twoSum(int[] nums, int target) {
     // first pair hi return krna hai (Brute force)
        for (int i = 0; i < arr.length; i++) {
                for (int j = i + 1; j < arr.length; j++) {
                        if (arr[i] + arr[j] == target) {
                               return new int[] { i, j };
                             }
                          }
                      }
                return new int[] {};
            }
}
```

</details>
<details>
  <summary><b>💡2) Hashmap approach (check if not present add)</b></summary>

```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        //efficient approach
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

```

</details>

---

## 🧩 Problem 2 : Find Duplicate Elements in an Array

**Problem Statement:**
Given an integer array `arr`, find all duplicate elements in the array and return them in a list.

**Example:**

```
Input:  arr = [1, 2, 3, 1, 3, 6, 6]
Output: [1, 3, 6]
```

**Hints:**

- 🔎 Start with a simple brute-force check (compare every pair)
- ⚡ Use a `HashSet` to reduce time to O(n)
- 🔁 Sorting helps if you can modify or copy the array (O(n log n))
- 🧠 Index-marking trick is fastest O(n) with O(1) extra but requires values in range `1..n` and modifies input

---

<details>
  <summary><b>1) Brute-force (Nested loops) — Simple, intuitive</b></summary>

**Idea:** Compare every pair `(i, j)` and collect duplicates. Avoid adding the same duplicate multiple times.

**Complexity:**

- ⏱️ Time: **O(n²)** (two nested loops)
- 💾 Space: **O(k)** for result list (k = number of duplicates)

```java
import java.util.ArrayList;

class Solution {
    static ArrayList<Integer> duplicates(int arr[]) {
        ArrayList<Integer> duplicates = new ArrayList<>();
        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] == arr[j] && !duplicates.contains(arr[i])) {
                    duplicates.add(arr[i]);
                }
            }
        }
        return duplicates;
    }
}
```

</details>

<details>
  <summary><b>2) HashSet approach — Fast & easy (recommended)</b></summary>

**Idea:** Use one `HashSet` to track seen values. When a value is already in `seen`, add it to a `dup` set. Convert `dup` to list at the end.

**Complexity:**

- ⏱️ Time: **O(n)**
- 💾 Space: **O(n)** (for `seen` and `dup` sets)

```java
import java.util.ArrayList;
import java.util.HashSet;

class Solution {
    static ArrayList<Integer> duplicates(int arr[]) {
        HashSet<Integer> seen = new HashSet<>();
        HashSet<Integer> dup = new HashSet<>();
        for (int val : arr) {
            if (seen.contains(val)) {
                dup.add(val);
            } else {
                seen.add(val);
            }
        }
        return new ArrayList<>(dup);
    }
}
```

</details>

<details>
  <summary><b>3) Sorting approach — Good if modifying or copying array is OK</b></summary>

**Idea:** Sort the array and scan adjacent elements to find duplicates. This groups equal values together.

**Complexity:**

- ⏱️ Time: **O(n log n)** (due to sorting)
- 💾 Space: **O(1)** extra if sort in-place (or O(n) if you need a copy)

```java
import java.util.ArrayList;
import java.util.Arrays;

class Solution {
    static ArrayList<Integer> duplicates(int arr[]) {
        ArrayList<Integer> duplicates = new ArrayList<>();
        if (arr.length == 0) return duplicates;

        Arrays.sort(arr); // modifies input
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] == arr[i - 1]) {
                // avoid adding same duplicate multiple times
                if (duplicates.isEmpty() || duplicates.get(duplicates.size() - 1) != arr[i]) {
                    duplicates.add(arr[i]);
                }
            }
        }
        return duplicates;
    }

}
```

</details>

<details>
  <summary><b>4) Index-marking trick — O(n) time, O(1) extra (when applicable)</b></summary>

**Idea:** If array values are in the range `1..n` (n = arr.length), use each value `val` to mark index `val-1` negative. On second visit the position is already negative → duplicate. This **modifies** the input array.

**Important:** This method only works when each value `val` satisfies `1 <= val <= n`. Also it mutates the array (we restore it after detection in the example below).

**Complexity:**

- ⏱️ Time: **O(n)**
- 💾 Space: **O(1)** (ignoring output list)

```java
import java.util.ArrayList;

class Solution {
    static ArrayList<Integer> duplicates(int arr[]) {
        ArrayList<Integer> duplicates = new ArrayList<>();

        for (int i = 0; i < arr.length; i++) {
            int val = Math.abs(arr[i]);
            int idx = val - 1; // map value to index
            if (idx < 0 || idx >= arr.length) {
                // index trick not applicable for this value range
                continue;
            }
            if (arr[idx] < 0) {
                // already visited => duplicate
                if (!duplicates.contains(val)) duplicates.add(val);
            } else {
                // mark as visited
                arr[idx] = -arr[idx];
            }
        }

        // restore original array values (optional)
        for (int i = 0; i < arr.length; i++) arr[i] = Math.abs(arr[i]);

        return duplicates;
    }
}
```

</details>

---
