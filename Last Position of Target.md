## 458. Last Position of Target

Find the last position of a target number in a sorted array. Return -1 if target does not exist.

 Example

 ```bash
Given [1, 2, 2, 4, 5, 5].
For target = 2, return 2.
For target = 5, return 5.
For target = 6, return -1.
 ```



Solution:

```python
class Solution:
    """
    @param nums: An integer array sorted in ascending order
    @param target: An integer
    @return: An integer
    """
    def lastPosition(self, nums, target):
        # write your code here
        i = 0
        record = -1
        while i < len(nums):
            if nums[i] > target:
                break
            if nums[i] == target:
                record = i
            i += 1
        return record
```



Notes: 不断从头遍历查找，因为是排序的数组，所以 target 小于数组中的值时，可以跳出。