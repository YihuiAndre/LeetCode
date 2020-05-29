# Problem
[977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.
 

**Example 1:**
```text
Input: [-4,-1,0,3,10]
Output: [0,1,9,16,100]
```

**Example 2:**
```text
Input: [-7,-3,2,3,11]
Output: [4,9,9,49,121]
 ```

**Note:**

1. ```1 <= A.length <= 10000```
2. ```-10000 <= A[i] <= 10000```
3. ```A is sorted in non-decreasing order```


# Solution
## Idea:
* Sorted: Making all the elements in the input array multiply by itself and then sorted by increasing order.
##  Time Complexity:
Time Complexity: O(nlogn), Space Complexity: O(1)

```java
    public int[] sortedSquares(int[] A) {
        for(int i = 0, len = A.length; i < len; i++){
            A[i] = A[i] * A[i];
        }
        Arrays.sort(A);
        return A;
    }
```
