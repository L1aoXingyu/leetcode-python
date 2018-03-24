## 594.strStr II

Implement `strStr` function in O(n + m) time.

`strStr` return the first index of the target string in a source string. The length of the target string is *m* and the length of the source string is *n*.
If target does not exist in source, just return -1.

**Example**

```bash
Given source = abcdef, target = bcd, 
return 1
```



Solution:

```python
class Solution:
    """
    @param: source: A source string
    @param: target: A target string
    @return: An integer as index
    """
    
    def strStr2(self, source, target):
        # write your code here
        if target is None or source is None:
            return -1
        
        if len(target) == 0:
            return 0
            
        BASE = 1e6
        m = len(target)
        
        # Get power within Base.
        power = 1
        for i in range(m-1):
            power = (power * 31) % BASE
        
        # Get target code.
        targetCode = 0
        for i in range(m):
            targetCode = (targetCode * 31 + ord(target[i])) % BASE
            
        hashCode = 0
        for i in range(len(source)):
            hashCode = (hashCode * 31 + ord(source[i])) % BASE
            
            # abcde
            if i < m - 1:
                continue
            
            # double check the string
            if hashCode == targetCode:
                if source[i + 1 - m : i + 1] == target:
                    return i + 1 - m
            else:
                # abc -> bc
                hashCode = hashCode - ord(source[i - m + 1]) * power
                if hashCode < 0:
                    hashCode += BASE
        
        return -1
```



Notes: 这是 Rabin Karp 算法，通过对 Target 和 source 建立 hash code，从而将一串字符的比较变成整数与整数的比较，实现 $O(n^2)$ 变为 $O(n + m)$ 的时间复杂度