# Problem
[941. Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array/)

Given an array ```A``` of integers, return ```true``` if and only if it is a *valid mountain array*.

Recall that A is a mountain array if and only if:

* ```A.length >= 3```
* There exists some ```i``` with ```0 < i < A.length - 1``` such that:
    
    *```A[0] < A[1] < ... A[i-1] < A[i]```
    *```A[i] > A[i+1] > ... > A[A.length - 1]```

![img](./img.png)

**Example 1:**
```text
Input: [2,1]
Output: false
```

**Example 2:**
```text
Input: [3,5,5]
Output: false
```

**Example 3:**
```text
Input: [0,3,2,1]
Output: true
```

**Note:** 

1. ```0 <= A.length <= 10000```
2. ```0 <= A[i] <= 10000```


# Solution
## Idea#1:
* Iterating the input array start from the beginning index to find the turning point. When finding the turning point, make sure it follow the rule of ```A[0] < A[1] < ... A[i-1] < A[i]``` . 
* Then, return false for not existing turning point or turning point that locate at the biginning of the index.
* Iterating the input array start from the turning point and make sure it follow the rule of ```A[i] > A[i+1] > ... > A[A.length - 1]```.
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public boolean validMountainArray(int[] A) {
        if(A.length < 3) return false;
        int turningPoint = -1;
        for(int i = 1, len = A.length; i < len; i++){
            if(A[i-1] == A[i]) return false;
            if(A[i-1] > A[i]){
                turningPoint = i-1;
                break;
            }
        }
        if(turningPoint == -1 || turningPoint == 0) return false;
        for(int i = turningPoint+1, len = A.length; i < len; i++){
            if(A[i-1] < A[i] || A[i-1] == A[i]) return false;
        }
        return true;
    }
```
