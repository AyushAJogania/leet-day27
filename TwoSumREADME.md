# leet-day27

# Two Sum

## Problem Description

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers in the array that add up to the given `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

## Examples

**Example 1:**
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**
```
Input: nums = [3,3], target = 6
Output: [0,1]
```

## Constraints

- 2 <= nums.length <= 10^4
- -10^9 <= nums[i] <= 10^9
- -10^9 <= target <= 10^9
- Only one valid answer exists.

## Approach

We can solve this problem using a hash map to store the numbers we have encountered so far. For each number `num` in the `nums` array, we calculate the complement `target - num`. If the complement is already present in the hash map, we have found the pair of numbers that add up to the target, and we return their indices. If not, we add `num` to the hash map.

This approach helps us achieve a time complexity of O(n) as we iterate through the array only once and perform constant time operations for hash map lookups.

## Implementation

Here's the C++ code implementation of the solution:

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> numToIndex;
        vector<int> result;
        
        for (int i = 0; i < nums.size(); ++i) {
            int complement = target - nums[i];
            if (numToIndex.count(complement)) {
                result.push_back(numToIndex[complement]);
                result.push_back(i);
                break;
            }
            numToIndex[nums[i]] = i;
        }
        
        return result;
    }
};
```

## Complexity Analysis

- Time complexity: O(n), where n is the length of the `nums` array.
- Space complexity: O(n), as in the worst case, we may need to store all numbers in the hash map.
