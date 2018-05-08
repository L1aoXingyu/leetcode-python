## 409.Longest Palindrome

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example `"Aa"` is not considered a palindrome here.



Solutions:

```python
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: int
        """
        store_dic = dict()
        for single_str in s:
            if single_str in store_dic:
                del store_dic[single_str]
            else:
                store_dic[single_str] = 1

        if len(store_dic) == 0:
            return len(s) - len(store_dic)
        else:
            return len(s) - len(store_dic) + 1
```

Notes: 只需要建立 hash 表判断字符串中的是否有奇数，有多少个奇数就 ok 了。
