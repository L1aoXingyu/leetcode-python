## 125.Valid Palindrome

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
`"A man, a plan, a canal: Panama"` is a palindrome.
`"race a car"` is *not* a palindrome.



Solution:

```python
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        if s == '':
            return True
        
        start = 0
        end = len(s) - 1
        while start < end:
            while start < end and (not s[start].isalpha() and not s[start].isdigit()):
                start += 1
        
            while start < end and (not s[end].isalpha() and not s[end].isdigit()):
                end -= 1
        
            if s[start].lower() != s[end].lower():
                return False
            start += 1
            end -= 1
        return True
```



Notes: 只需要从头和尾不断往中间遍历，然后判断是否是回文即可，中间注意不是字母或者数字的字符，不断跳过。