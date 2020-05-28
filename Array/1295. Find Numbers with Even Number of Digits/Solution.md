# Problem
[Leetcode](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/)

Given an array nums of integers, return how many of them contain an **even number** of digits.
 

**Example 1:**
```text
Input: nums = [12,345,2,6,7896]
Output: 2
Explanation: 
12 contains 2 digits (even number of digits). 
345 contains 3 digits (odd number of digits). 
2 contains 1 digit (odd number of digits). 
6 contains 1 digit (odd number of digits). 
7896 contains 4 digits (even number of digits). 
Therefore only 12 and 7896 contain an even number of digits.
```

**Example 2:**
```text
Input: nums = [555,901,482,1771]
Output: 1 
Explanation: 
Only 1771 contains an even number of digits.
 ```

**Constraints:**

1. ```1 <= nums.length <= 500```
2. ```1 <= nums[i] <= 10^5```


# Solution
## Idea:
* Converting all the elements in the input array to datatype String and then recording the number of length of the String that can be divisible by 2
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public int findNumbers(int[] nums) {
        int numEven = 0;
        for(int num : nums){
            if(String.valueOf(num).length() % 2 == 0) numEven++;
        }
        return numEven;
    }
```