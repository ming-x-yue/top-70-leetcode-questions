# Two Sum

## Question:

Given an array of integers `nums` and an integer `target`, return
indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and
you may not use the same element twice.

You can return the answer in any order.


## How to Solve:

Maintain a hash map (`unordered_map` in C++) that at every iteration records the difference between the target and the current number as key, and the current number's index as the value.

Whenever we encounter a current number that matches an existing key in the hash map, we know a pair of two-sum has been found. Then, we can return the existing key's matching value (which is the index of the first number of the two-sum) and the current index (the index of the second number of the two-sum).

## Brute force: 

Brute force method checks for every pair of elements in the array whether there is a pair that sums up to the target number. It checks for every element i in the array whether there is an element j in the rest of the array where i < j such that i+j=target.

## Time Complexity

The time complexity is O(n) because it traverses the array once and uses the hash map to check whether a target is found. Searching a key in the hash map (dictionary) only requires O(1), which is faster than the search time in brute force by iterating through the array another time.

## My Python Solution:
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        complement = {}
        for i in range(len(nums)):
            complem = target - nums[i]
            if complem in complement:
                return [i, complement[complem]]
            complement[nums[i]] = i
        
        return -1
```