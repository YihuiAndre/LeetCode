# Problem
[1089. Duplicate Zeros](https://leetcode.com/problems/duplicate-zeros/)

Given a fixed length array arr of integers, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written.

Do the above modifications to the input array in place, do not return anything from your function.
 

**Example 1:**
```text
Input: [1,0,2,3,0,4,5,0]
Output: null
Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4]
```

**Example 2:**
```text
Input: [1,2,3]
Output: null
Explanation: After calling your function, the input array is modified to: [1,2,3]
 ```

**Note:**

1. ```1 <= arr.length <= 10000```
2. ```0 <= arr[i] <= 9```


# Solution
## Idea:
* ***Brute Force:*** Iterating the input array one by one. If zero present and index of it not locate at the end of the input array, insert zero to the next index and shift the remaining elements to the right. Then, Skiping the next index and move to the next next index.
##  Time Complexity:
Time Complexity: O(n^2), Space Complexity: O(1)

```java
    public void duplicateZeros(int[] arr) {
        for(int i = 0, len = arr.length; i < len; i++){
            if(arr[i] == 0 && i != len-1){
                for(int j = arr.length-1; j > i+1; j--){
                    arr[j] = arr[j-1];
                }
                arr[++i] = 0;
            }
        }
    }
```

## Idea:
* Create a new array to copy the element in the input array one by one and keep track of the number of element in the new array. If there is a zero in the input array and remaining space in new array is more than two, copy two zero to the new array. After it, copying all the elements from the new array to the input array
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(n)

```java
    public void duplicateZeros(int[] arr) {
        int[] result = new int[arr.length];
        int lengthOfResult = 0;
        for(int i = 0, len = arr.length; i < len && lengthOfResult < len; i++){
            if(lengthOfResult != len-1 && arr[i] == 0){
                result[lengthOfResult++] = 0;
            }
            result[lengthOfResult++] = arr[i];
        }
        for(int j = 0, len = result.length; j < len; j++){
            arr[j] = result[j];
        }
    }
```