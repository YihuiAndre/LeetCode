# Problem
[Leetcode](https://leetcode.com/problems/max-consecutive-ones/)

Given a binary array, find the maximum number of consecutive 1s in this array.

**Example 1**:
```text
Input: [1,1,0,1,1,1]
Output: 3
```
**Explanation**: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
Note:

* The input array will only contain 0 and 1.
* The length of input array is a positive integer and will not exceed 10,000


# Solution
## Steps:
* iterate the input array and keep track of the maximun consecutive of one.
* when iterating the input array, if the current element is one, begin to start counting of the consecutive of one. If the current element is zero, compare it with the maximun consecutive of one. If bigger, then reset the maximum consecutive of one with the new consecutive of one. If smaller, do nothing. In both cases, reset the count as zero.
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public int findMaxConsecutiveOnes(int[] nums) {
        int maxConsecutive = 0, counting = 0;
        for(int binary : nums){
            if(binary == 1) counting++;
            else{
                if(counting > maxConsecutive){
                    maxConsecutive = counting;
                }
                counting = 0;
            }
        }
        return maxConsecutive;
    }
```