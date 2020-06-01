# Problem
[26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) 

[中文](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

Given a sorted array nums, remove the duplicates *in-place* such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array** *in-place* with O(1) extra memory.
 

**Example 1:**
```text
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

**Example 2:**
```text
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```

**Clarification:**

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by **reference**, which means modification to the input array will be known to the caller as well.

Internally you can think of this:
```java
// nums is passed in by reference. (i.e., without making a copy)
int len = removeElement(nums, val);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```


# Solution
## Idea#1:
* This LeetCode question is similar to [27. Remove Element](https://leetcode.com/problems/remove-element/). It can use [Idea#2](https://github.com/YihuiAndre/LeetCode/blob/master/Array/27.%20Remove%20Element/Solution.md#idea2) to solve it.
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public int removeDuplicates(int[] nums) {
        int len = nums.length, numOfRemove = 0;
        for(int i = 1; i < len; i++){
            if(nums[i-1] == nums[i]){
                numOfRemove++;
            }
            else{
                nums[i-numOfRemove] = nums[i];
            }
        }
        return len - numOfRemove;
    }
```
