# Problem
[414. Third Maximum Number](https://leetcode.com/problems/third-maximum-number/)

[中文](https://leetcode-cn.com/problems/third-maximum-number/)

Given a **non-empty** array of integers, return the **third** maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).
 

**Example 1:**
```text
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```

**Example 2:**
```text
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```

**Example 3:**
```text
Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```

# Solution
## Idea#1:
* Priority Queue: Inserting the three largest distinct value into the Priority Queue so it can use ```poll``` method in Priority Queue class to retrive the third biggest value. If the size of Priority Queue is two, reduce it to one by implementing ```poll``` method once.

##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(n)

```java
    public int thirdMax(int[] nums) {
        PriorityQueue<Integer> pq = new PriorityQueue<Integer>();
        for(int num : nums){
            if(!pq.contains(num)){
                if(pq.size() < 3) pq.add(num);
                else if(pq.peek() < num){
                    pq.poll();
                    pq.add(num);
                }
            }
        }
        while(pq.size() == 2){
            pq.poll();
        }
        return pq.poll();
    }
```
