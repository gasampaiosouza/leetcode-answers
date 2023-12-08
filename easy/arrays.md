# Easy Array Problems

This file contains solutions to easy-level problems related to arrays on LeetCode.

## Problem 1: Single Number
Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

### TypeScript Solution:
```typescript
// nums = [2, 2, 1] -> 1
// nums = [4, 1, 2, 1, 2] -> 4
// nums = [1] -> 1

function singleNumber(nums: number[]): number {
    const seen = new Map();

    for (let num of nums) {
        if (!seen.get(num)) seen.set(num, 1)
        else seen.delete(num)
    }

    return seen.entries().next().value[0]
};
```

### Explanation:

- **Map Approach:** The solution uses a `Map` to store the count of occurrences of each number. The key of the Map is the number, and the value is the number of times the number appears in the array.

- **Iteration:** The function iterates through the `nums` array, checking if the number exists in the `Map`. If it doesn't exist, it's added to the `Map` with a value of `1`. If it already exists, that entry is removed from the `Map`.

- **Return:** At the end, there remains only one number in the `Map`, which is the number that appears only once.

### Complexity:

- The function iterates through the entire `nums` array once, leading to a time complexity of **O(n)**, where **n** is the number of elements in the array.

- The usage of the `Map` keeps the space complexity at **O(n)**, as in the worst case, the `Map` will contain half of the elements from `nums`.
