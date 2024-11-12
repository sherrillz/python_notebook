# Python Leetcode

### Blind 75


### 3. Longest Substring Without Repeating Characters
**Given a string s, find the length of the longest substring without repeating characters.**

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.``

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        n = len(s)
        maxLength = 0
        charSet = set()
        left = 0
        
        for right in range(n):
            if s[right] not in charSet:
                charSet.add(s[right])
                maxLength = max(maxLength, right - left + 1)
            else:
                while s[right] in charSet:
                    charSet.remove(s[left])
                    left += 1
                charSet.add(s[right])
        
        return maxLength
```

**Explaination**
1. We use a set (`charSet`) to keep track of unique characters in the current substring.
2. We maintain two pointers, left and right, to represent the  boundaries of the current substring.
4. The maxLength variable keeps track of the length of the longest substring encountered so far.
5. We iterate through the string using the right pointer.
6. If the current character is not in the set (charSet), it means we have a new unique character.
7. We insert the character into the set and update the maxLength if necessary.
8. If the character is already present in the set, it indicates a repeating character within the current substring.
9. In this case, we move the left pointer forward, removing characters from the set until the repeating character is no longer present.
10. We insert the current character into the set and continue the iteration.
11. Finally, we return the maxLength as the length of the longest substring without repeating characters.

### [5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/description/?envType=problem-list-v2&envId=xi4ci4ig)

**Given a string s, return the longest palindromic substring in s.**

Example 1:

Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s) <= 1:
            return s
        
        Max_Len=1
        Max_Str=s[0]
        for i in range(len(s)-1):
            for j in range(i+1,len(s)):
                if j-i+1 > Max_Len and s[i:j+1] == s[i:j+1][::-1]:
                    Max_Len = j-i+1
                    Max_Str = s[i:j+1]

        return Max_Str
```
``s[i:j+1]:`` Extracts a substring from index i to j (inclusive) from the string s.
``s[i:j+1][::-1]``: Reverses the extracted substring.
``s[i:j+1] == s[i:j+1][::-1]``: Checks if the substring is identical to its reversed version, thereby determining if it's a palindrome.

