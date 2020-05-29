# Problem
[485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

Given a binary array, find the maximum number of consecutive 1s in this array.

**Example 1**:
```text
Input: [1,1,0,1,1,1]
Output: 3
```
**Explanation**: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
Note:

1. ```The input array will only contain 0 and 1.```
2. ```The length of input array is a positive integer and will not exceed 10,000```


# Solution
## Idea#1:
* iterating the input array and keep track of the maximun and current consecutive of one.
* During the iteration, if the current element is one, increase the current consecutive of one by one. If the current element is zero, reset the current counting of one to zero. 
* Comparing and updating the current consecutive of one and the maximum consecutive of one in each loop. If bigger, replace the maximum consecutive of one with the new value. If smaller, do nothing.
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public int findMaxConsecutiveOnes(int[] nums) {
        int maxConsecutive = 0, counting = 0;
        for(int binary : nums){
            if(binary == 1) counting++;
            else counting = 0;
            if(counting > maxConsecutive){
                maxConsecutive = counting;
            }
        }
        return maxConsecutive;
    }
```
