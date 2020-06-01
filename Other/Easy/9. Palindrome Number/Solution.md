# Problem
[9. Palindrome Number](https://leetcode.com/problems/palindrome-number/)

[中文](https://leetcode-cn.com/problems/palindrome-number/)

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.


**Example 1:**
```text
Input: 121
Output: true
```

**Example 2:**
```text
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**Example 3:**
```text
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```
**Follow up:** 

Coud you solve it without converting the integer to a string?


# Solution
## Idea#1:
* Convert the number to String datatype and compare beginning index and ending index of the character. If the same, increase the beginning index and decrease the ending index until they are the same or the beginning index is bigger than the ending index.
##  Time Complexity:
Time Complexity: O(n), Space Complexity: O(1)

```java
    public boolean isPalindrome(int x) {
        if(x < 0) return false;
        String num = String.valueOf(x);
        for(int begin = 0, end = num.length()-1; begin != end && begin < end; begin++, end--){
            if(num.charAt(begin) != num.charAt(end)){
                return false;
            }
        }
        return true;
    }
```
