# Problem
[88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.
 

**Example:**
```text
Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```

**Note:**

1. ```The number of elements initialized in nums1 and nums2 are m and n respectively.```
2. ```You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.```


# Solution
## Idea:
* Sorted: Copy all the elements in the input array 2 (```nums2```) to the input array 1 (```nums1```). Then, sorting the input array 1 (```nums1```).
##  Time Complexity:
Time Complexity: O((m+n)log(m+n)), Space Complexity: O(1)

```java
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        for(int i = m, len = m+n; i < len; i++){
            nums1[i] = nums2[i-m];
        }
        Arrays.sort(nums1, 0, m+n);
    }
```

## Idea:
* Create a new copy of the input array 1 (```nums1```) with capacity of m with the same element. 
* Iterating the elements in the new array and the input array 2 (```nums2```). Comparing and picking the smaller element among the two arrays to the input array 1 (```nums1```) and keep track of the number of the elements have been processed in the input array 1 (```nums1```), the input array 2 (```nums2```) and the new array. 
* when either the input array 2 (```nums2```) or the new array is finished processing, put the remainning element to the input array 1 (```nums1```).

## Steps:
**nums1:**

|  1  | 2 | 3 | 0 | 0 | 0 |
|-----|---|---|---|---|---|
|i+j=0|   |   |   |   |   |

**copy of nums1:**

|  1  | 2 | 3 |   |   |   |
|-----|---|---|---|---|---|
| i=0 |   |   |   |   |   |

**nums2:**

|  2  | 5 | 6 |   |   |   |
|-----|---|---|---|---|---|
| j=0 |   |   |   |   |   |

----

**nums1:**

| 1 | 2 | 2 | 3 |    0    | 0 |
|---|---|---|---|---------|---|
|   |   |   |   | i+j = 4 |   |

**copy of nums1:**

| 1 | 2 | 3 |     |   |   |
|---|---|---|-----|---|---|
|   |   |   | i=3 |   |   |

**nums2:**

| 2 |  5  | 6 |   |   |   |
|---|-----|---|---|---|---|
|   | j=1 |   |   |   |   |

----

**nums1:**

| 1 | 2 | 2 | 3 | 5 | 6 |         |
|---|---|---|---|---|---|---------|
|   |   |   |   |   |   | i+j = 4 |

**copy of nums1:**

| 1 | 2 | 3 |     |   |   |
|---|---|---|-----|---|---|
|   |   |   | i=3 |   |   |

**nums2:**

| 2 | 5 | 6 |     |   |   |
|---|---|---|-----|---|---|
|   |   |   | j=3 |   |   |

##  Time Complexity:
Time Complexity: O(m+n), Space Complexity: O(m)

```java
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int[] copyOfNums1 = Arrays.copyOf(nums1, m);
        int i, j;
        for(i = 0, j = 0; i < m && j < n;){
            if(copyOfNums1[i] > nums2[j]){
                nums1[i+j] = nums2[j];
                j++;
            }
            else{
                nums1[i+j] = copyOfNums1[i];
                i++;
            }
        }
        while(i != m){
            nums1[i+j] = copyOfNums1[i];
            i++;
        }
        while(j != n){
            nums1[i+j] = nums2[j];
            j++;
        }
    }
```
