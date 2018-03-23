## 5. Longest Palindromic Substring

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example:**

```bash
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
```

 

**Example:**

```bash
Input: "cbbd"

Output: "bb"
```



Solution:

```python
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        if s == None or s == '':
            return ''
        
        longest = 0
        start = 0
        end = 0
        i = 0
        while i < len(s):
            odd_longest = self.find_longest_parlindrome(s, i, i)
            if odd_longest > longest:
                longest = odd_longest
                start = i - (longest - 1) / 2
                end = i + (longest - 1) / 2
            
            even_longest = self.find_longest_parlindrome(s, i, i+1)
            if even_longest > longest:
                longest = even_longest
                start = i - longest / 2 + 1
                end = i + 1 + longest / 2 - 1
            i += 1
        return s[start:end+1]
        
        
    def find_longest_parlindrome(self, s, i, j):
        longest = j - i - 1
        while (i >= 0) and (j < len(s)):
            if s[i] == s[j]:
                i -= 1
                j += 1
                longest += 2
            else:
                return longest
        return longest
```



Notes: 不断枚举中点，通过中点向两边延伸，判断是否是回文。