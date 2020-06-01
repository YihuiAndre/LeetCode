# Problem
[1346. Check If N and Its Double Exist](https://leetcode.com/problems/check-if-n-and-its-double-exist/)

[中文](https://leetcode-cn.com/problems/check-if-n-and-its-double-exist/)

Given an array ```arr``` of integers, check if there exists two integers ```N``` and ```M``` such that ```N``` is the double of ```M``` ( i.e. ```N = 2 * M```).

More formally check if there exists two indices i and j such that :

* ```i != j```
* ```0 <= i, j < arr.length```
* ```arr[i] == 2 * arr[j]```

**Example 1:**
```text
Input: arr = [10,2,5,3]
Output: true
Explanation: N = 10 is the double of M = 5,that is, 10 = 2 * 5.
```
**Example 2:**
```text
Input: arr = [7,1,14,11]
Output: true
Explanation: N = 14 is the double of M = 7,that is, 14 = 2 * 7.
```

**Example 3:**
```text
Input: arr = [3,1,7,11]
Output: false
Explanation: In this case does not exist N and M, such that N = 2 * M.
```
**Constraints:**
* ```2 <= arr.length <= 500```
* ```-10^3 <= arr[i] <= 10^3```

# Solution
## Idea#1:
* **Brute Force:** Iterating the input array and check every elements except itself to find its exists double integer
##  Time Complexity:
Time Complexity: O(n^2), Space Complexity: O(1)

```java
    public boolean checkIfExist(int[] arr) {
        for(int i = 0, len = arr.length; i < len; i++){
            for(int j = 0; j < len; j++){
                if(j != i && arr[i] == 2*arr[j]){
                    return true;
                }
            }
        }
        return false;
    }
```

