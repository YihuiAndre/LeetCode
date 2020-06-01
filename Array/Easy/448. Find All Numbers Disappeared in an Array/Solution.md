# Problem
[448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

[中文](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/)

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

**Example:**
```text
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```


# Solution
## Idea#1:
* Iterate through the input array and look for the index base on the current element. Once found it, turn the element of that index as negative to indicate the existence of current element. Then, iterate the input array again to find if any element is not negative and add the index of those element into the return arraylist.

##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> res = new ArrayList<Integer>();
        for(int i = 0, len = nums.length; i < len; i++){
            int index = Math.abs(nums[i]) - 1;
            if(nums[index] > 0) nums[index] = -nums[index];
        }
        for(int i = 0, len = nums.length; i < len; i++){
            if(nums[i] > 0) res.add(i+1);
        }
        return res;
    }
```
