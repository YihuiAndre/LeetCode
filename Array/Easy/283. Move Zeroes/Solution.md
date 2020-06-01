# Problem
[283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

[中文](https://leetcode-cn.com/problems/move-zeroes/)

Given an array ```nums```, write a function to move all ```0```'s to the end of it while maintaining the relative order of the non-zero elements.
 

**Example:**
```text
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Note:**

1. ```You must do this in-place without making a copy of the array.```
2. ```Minimize the total number of operations.```


# Solution
## Idea#1:
* This leetcode question can be done by using the similar idea in [A Better Repeated Deletion Algorithm - Answer](https://leetcode.com/explore/learn/card/fun-with-arrays/511/in-place-operations/3255/).
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public void moveZeroes(int[] nums) {
        int writeIndex = 0;
        for(int i = 0, len = nums.length; i < len; i++){
            if(nums[i] != 0) nums[writeIndex++] = nums[i];
        }
        while(writeIndex != nums.length){
            nums[writeIndex++] = 0;
        }
    }
```
