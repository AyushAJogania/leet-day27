# Search in Rotated Sorted Array II

## Problem Statement

You are given an integer array `nums` sorted in non-decreasing order (not necessarily with distinct values). Before being passed to your function, `nums` is rotated at an unknown pivot index `k` (`0 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (0-indexed).

Write a function `search` that takes an array `nums` and an integer `target` as input and returns `true` if the target is in `nums`, or `false` if it is not in `nums`.

## Examples

**Example 1:**
```
Input: nums = [2,5,6,0,0,1,2], target = 0
Output: true
```

**Example 2:**
```
Input: nums = [2,5,6,0,0,1,2], target = 3
Output: false
```

## Constraints

- 1 <= nums.length <= 5000
- -104 <= nums[i] <= 104
- `nums` is guaranteed to be rotated at some pivot.
- -104 <= target <= 104

## Approach

To solve this problem, we can use a binary search approach with some modifications to handle cases where there are duplicate elements in the array.

1. Initialize two pointers `left` and `right` pointing to the beginning and end of the array, respectively.
2. While `left` is less than or equal to `right`, calculate the `mid` index.
3. Check if `nums[mid]` is equal to the `target`, in which case we return `true`.
4. Handle the case where there are duplicate elements at the beginning, middle, and end of the array.
5. Check if the left half of the array (`nums[left] <= nums[mid]`) is sorted:
   - If `nums[left] <= target` and `target < nums[mid]`, update `right` to `mid - 1` to search in the left half.
   - Otherwise, update `left` to `mid + 1` to search in the right half.
6. If the left half is not sorted, the right half must be sorted:
   - If `nums[mid] < target` and `target <= nums[right]`, update `left` to `mid + 1` to search in the right half.
   - Otherwise, update `right` to `mid - 1` to search in the left half.
7. If the target is not found after the loop, return `false`.

## Complexity Analysis

- Time complexity: O(log n), where n is the length of the `nums` array.
- Space complexity: O(1), as no extra space is used.
