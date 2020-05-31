# Problem
[905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)

Given an array ```A``` of non-negative integers, return an array consisting of all the even elements of ```A```, followed by all the odd elements of ```A```.

You may return any answer array that satisfies this condition.

**Example 1:**
```text
Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.
```
**Note:** 

1. ```1 <= A.length <= 5000```
2. ```0 <= A[i] <= 5000```


# Solution
## Idea#1:
* This question is similar to [27. Remove Element](../27.%20Remove%20Element/Solution.md) in [Idea#3](../27.%20Remove%20Element/Solution.md#idea3). If there is an odd number, switch it with the last element and decrease the length of the input array by one (```Not the Capacity!!```)
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public int[] sortArrayByParity(int[] A) {
        int length = A.length-1, tmp;
        for(int i = 0; i < length; i++){
            while(A[i]%2!=0 && i < length){
                tmp = A[length];
                A[length--] = A[i];
                A[i] = tmp;
            }
        }
        return A;
    }
```
