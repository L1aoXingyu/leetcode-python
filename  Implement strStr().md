## 28.Implement strStr()

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example 1:**

```bash
Input: haystack = "hello", needle = "ll"
Output: 2
```

**Example 2:**

```bash
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```



Solution:

```python
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if haystack is None or needle is None:
            return -1
        
        if needle == haystack:
            return 0
        
        needle_len = len(needle)
        start = 0
        while start < len(haystack)-needle_len + 1:
            k = 0
            for j in range(needle_len):
                if haystack[start+j] == needle[j]:
                    k += 1
                else:
                    break
            if k == needle_len:
                return start
            else:
                start += 1
        return -1
```



Notes: 只需要从开始不断向后遍历，注意 needle 和 haystack 相同的情况，同时注意遍历到最后的下标是多少。