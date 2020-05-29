# Problem
[27. Remove Element](https://leetcode.com/problems/remove-element/)

Given an array nums and a value val, remove all instances of that value *in-place* and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array** *in-place* with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.
 

**Example 1:**
```text
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.

It doesn't matter what you leave beyond the returned length.
```

**Example 2:**
```text
Given nums = [0,1,2,2,3,0,4,2], val = 2,

Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4.

Note that the order of those five elements can be arbitrary.

It doesn't matter what values are set beyond the returned length.
```

**Clarification:**

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by **reference**, which means modification to the input array will be known to the caller as well.

Internally you can think of this:
```java
// nums is passed in by reference. (i.e., without making a copy)
int len = removeElement(nums, val);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```


# Solution
## Idea#1:
* **Brute Force**: Iterating the input array and look for the value (```val```). Once found it, remove it by shifting the elements on its right to left and recheck the new element in that index again. after iteration, return number of elements in the input array that doesn't be removed.

##  Time Complexity:
Time Complexity: O(n^2), Space Complexity: O(1)

```java
    public int removeElement(int[] nums, int val) {
        int len = nums.length;
        for(int i = 0; i < len;){
            if(nums[i] == val){
                for(int j = i; j < len-1; j++){
                    nums[j] = nums[j+1];
                }
                len--;
            }
            else{
                i++;
            }
        }
        return len;
    }
```

## Idea#2:
* Iterating the input array one by one and counting the number of element that need to be removed. If the current element contain n number of element with value (```val```) on the left side, then it will need to shift the index to the left for n index.


##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public int removeElement(int[] nums, int val) {
        int len = nums.length, numOfShift = 0;
        for(int i = 0; i < len; i++){
            if(nums[i] == val) numOfShift++;
            else nums[i-numOfShift] = nums[i];
        }
        return len-numOfShift;
    }
```

## Idea#3:

* Iterating the input array. If the current element has the same value (```val```), switch it with the last element of the input array and decrease the length of the input array (**Not the Capacity!!**) until the current element doesn't have the same value (```val```). Then, iterating to the next element.


## Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public int removeElement(int[] nums, int val) {
        int len = nums.length;
        for (int i = 0 ; i< len; ++i){
            while (nums[i]==val && i< len) {
                nums[i]=nums[--len];
            }
        }
        return len;
    }
```
