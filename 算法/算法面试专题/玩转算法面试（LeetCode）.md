
# 玩转算法面试 Leetcode题库分门别类详细解析

本篇笔记是学习liuyubobobo的玩儿转算法面试系列视频后总结而成

@Author: Howard Wonanut

@Date: 2019



[TOC]



## 0 前言
完成时间 | 2019-11-02

### 0.1 算法面试是什么？
让大家在面对面试中的算法问题时，有一个合理的思考路径；

- 不代表能够“正确”回答每一个算法问题，但是$\color{red}{合理的思考方向其实更重要}$，也是正确完成算法面试问题的前提

- 算法面试优秀不意味着技术面试优秀

- 技术面试优秀不意味着能够拿到Offer

### 0.1 向面试官多交流，仔细询问问题细节
比如面试官问一个简单的问题

> 对一组数据进行排序

由于不同的排序算法具有不同的特点以及应用场景，那么就需要考虑以下问题：

- 有没有可能包含大量的重复元素？

- 是否大部分数据距离它的正确位置很近？是否近乎有序？

- 是否数据的取值范围非常有限？比如对学生的成绩进行排序

- 是否需要稳定的排序

- 是否是使用链表存储的？

- 数据是否可以全部装在内存里？

这样能够展现你的思维严谨，考虑问题周全

### 0.2 算法面试优秀并不意味着技术面试优秀

- 项目经历和项目中遇到的实际问题

- 你遇到的印象最深的bug是什么？

### 0.3 技术面试优秀不意味着能够拿到Offer
技术面试只是面试的一部分，面试不仅仅是考察你的技术水平，还是了解你的过去以及形成的思考行为方式。

- 关于过去：**参与项目至关重要**
  
    - 自己做的小应用：计划表；备忘录
    
    - 自己解决的小问题：爬虫；数据分析
    
    - 一本优秀的技术书籍的代码整理
    
    - 技术博客、github


- 通过过去了解你的思考行为方式

    - 遇到的最大挑战？
    
    - 犯过的错误？
    
    - 遭遇的失败？
    
    - 最享受的工作内容？
    
    - 遇到冲突的处理方式？
    
    - 做的最与众不同的事？
    
- 准备好合适的问题问面试官

    - 整个小组的大概运行模式是怎样的？
    
    - 整个项目的后续规划是如何的？
    
    - 这个产品中的某个问题是如何解决的？
    
    - 对某个技术很感兴趣，在你的小组中会有怎样的机会学习这种技术？
    
### 0.4 算法面试的准备范围

1. 准备面试算法不需要啃完一本《算法导论》

    - 高级数据结构和算法面试的提及概率很低，如红黑树、B-Tree、斐波那契堆、计算几何、数论等

    - 远远不需要达到信息学竞赛难度
    
2. 不要轻视基础算法和数据结构
    - 各种排序算法
    
    - 基础数据结构和算法的实现：如堆、二叉树、图
    
    - 基础数据结构的使用：如链表、栈、队列、哈希表、图、并查集等
    
    - 基础算法：深度优先、广度优先、二分查找、递归
    
    - 基本算法思想：递归、分治、回溯、贪心、动态规划
    
### 0.5 选择合适的OJ（online judge）
1. LeetCode 👍
2. HackerRank（对问题的分类很详细、偏竞赛）

### 0.6 $\color{red}{不要忽视暴力法}$
如下面的题目：

> 在一个字符串中寻找没有重复字母的最长子串，如“abcabcbb”的结果为“abc”



## 1 时间复杂度分析
完成时间 | 2019-11-02

> n表示数据规模，O(f(n))表示运行算法所需要执行的指令数和f(n)成正比

### 1.1 数据规模的概念

如果要想在1s内解决问题：

- $O(n)$的算法可以处理大约$10^7 - 10^8$级别的数据

- $O(n^2)$的算法可以处理大约$10^3 - 10^4$级别的数据

- $O(n\log n)$的算法可以处理大约$10^6 - 10^7$级别的数据

## 2 数组
完成时间 | 2019-11-02 / 11-05

常见的问题都和数组有关：

- 排序：选择排序、插入排序、归并排序、快速排序

- 查找：二分查找

- 数据结构：栈、队列、堆

### 2.1 写一个正确的二分查找程序？

> 需要明确变量的含义！处理好边界条件的问题！

二分查找以其边界条件难以确定而出名，那么先写一个二分查找代码热热身


```python
def binarySearch(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```


```python
binarySearch([1,2,3,5,6,8,9], 10)
```




    -1



那么下面问题来了，如果将上面代码中第2行的代码改为：


```python
left, right = 0, len(arr)
```

原来的二分查找代码会有什么变化呢？仔细思考一下

*参考答案如下*


```python
def binarySearch(arr, target):
    left, right = 0, len(arr)
    while left < right: # 这里需要修改，因为right的值取不到
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid # 这里需要修改，因为[left,right)右边是开区间！
    return -1
```


```python
binarySearch([1,2,3,5,6,8,9], 3)
```




    2



你以为这样就结束了？其实直到1962年才写出完全正确的二分查找的代码原因在于上面代码的第4行：


```python
mid = (left + right) // 2
```

由于这里使用了加法，当left和right的值很大的时候该加法运算可能会产生上溢出，这才是罪魁祸首！

真正正确的二分查找法应该避免上面进行加法运算，从而避免整型溢出的问题：


```python
mid = left + (right - left) // 2
```

因此最终的二分查找算法应该是下面这样的：


```python
def binarySearch(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

### 2.2 面试问题热身

#### LeetCode 283 Moves Zeros
> 
> 给定一个数组nums，写一个函数，将数组中所有的0挪到数组的末尾，⽽维持其他所有非0元素的相对位置。
> 举例: nums = [0, 1, 0, 3, 12]，函数运⾏后结果为[1, 3, 12, 0, 0]

以下给出使用快慢指针的最优解


```python
def moveZeros(arr):
    left, right = 0, 0
    while right != len(arr):
        if arr[right] != 0:
            arr[left] = arr[right]
            left += 1
        right += 1
    while left != len(arr):
        arr[left] = 0
        left += 1
    return arr
```


```python
moveZeros([1, 0, 3, 4, 0, 6])
```




    [1, 3, 4, 6, 0, 0]



#### 🐂LeetCode 27 Remove Element

> 给定一个数组nums和一个数值val，将数组中所有等于val的元素删除，并返回剩余的元素个数。
>
> 如nums=[3,2,2,3], val=3.
> 返回2，且nums中前两个元素为2


```python
def removeElement(arr, val):
    left, right = 0, 0
    while right != len(arr):
        if arr[right] != val:
            arr[left] = arr[right]
            left += 1
        right += 1
    return left, arr
```


```python
removeElement([3,2,2,3], 3)
```




    (2, [2, 2, 2, 3])



#### 🐂LeetCode 26 Remove Duplicated from Sorted Array
`简单`

> 给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。
>
> 不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。


```python
class Solution:
    def removeDuplicates(self, nums):
        if len(nums) <= 1:
            return len(nums)
        
        i, j = 0, 0
        while j < len(nums):
            if nums[i] != nums[j]:
                i = i + 1
                nums[i] = nums[j]
            j += 1
        return i + 1
```

#### ⭐⭐⭐⭐LeetCode 80 Remove Duplicated from SOrted Array II
`中等` 

这道题有点绕，一遍没写出来

> 给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。
>
> 不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。


```python
class Solution:
    def removeDuplicates(self, nums):
        i = 0
        for num in nums:
            if i < 2 or num > nums[i - 2]:
                nums[i] = num
                i += 1
        return i
```

### 2.3 三路快排
三路快排使用三个指针，是一种经常使用到的思想

#### LeetCode 75 Sort Colors
`中等`

>给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。
>
>此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。
>
>**注意:**
>不能使用代码库中的排序函数来解决这道题。


这道题解法较多，第一种，可以使用计数排序


```python
class Solution(object):
    def sortColors(self, nums):
        count = [0] * 3
        for num in nums:
            count[num] += 1
        
        idx = 0
        for i in range(3):
            for j in range(count[i]):
                nums[idx] = i
                idx += 1
        return nums
```

还可以使用三路快排，只需要一次遍历即可完成，而且空间复杂度为$O(1)$!

详细的解释看：https://leetcode-cn.com/problems/sort-colors/solution/yan-se-fen-lei-by-leetcode/


```python
class Solution(object):
    def sortColors(self, nums):
        left, right, ptr = -1, len(nums), 0
        while ptr < right:
            if nums[ptr] == 1:
                ptr += 1
            elif nums[ptr] == 0:
                left += 1
                nums[left], nums[ptr] = nums[ptr], nums[left]
                ptr += 1
            else:
                right -= 1
                nums[ptr], nums[right] = nums[right], nums[ptr]
        return nums
```

#### ⭐⭐⭐⭐LeetCode 215 Kth Largest Elements in an Array
`中等` `经典`

> 在未排序的数组中找到第 k 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

如果要高效率的完成这道题，用$O(n)$的时间复杂度完成这个问题，就需要使用到快排算法的思想了


```python
## Todo
```

### 2.4 对撞指针（双索引技术）
#### LeetCode 167 Two Sum II - Input array is sorted
`简单` `对撞指针`

> 给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。
>
>函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。
>
>**说明:**
>
>返回的下标值（index1 和 index2）不是从零开始的。
>
>你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。



```python
class Solution(object):
    def twoSum(self, numbers, target):
        left, right = 0, len(numbers) - 1
        while left < right:
            if numbers[left] + numbers[right] < target:
                left += 1
            elif numbers[left] + numbers[right] > target:
                right -= 1
            else:
                return [left+1, right+1]
                
        return []
```

#### LeetCode 125 Valid Palindrome
`简单` `对撞指针` `回文串`

> 给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
>
> 说明：本题中，我们将空字符串定义为有效的回文串。

可以使用对撞指针解决这个问题,首先使用了正则表达式去掉所有非数字和字母的字符，然后再对字符串做判断能简化代码


```python
import re
class Solution(object):
    def isPalindrome(self, s):
        s = re.sub("[^a-z0-9]", "" ,s.lower())
        l, r = 0, len(s) - 1
        while l < r:
            if s[l] == s[r]:
                l += 1
                r -= 1
            else:
                return False
        return True
```


```python
s = Solution()
s.isPalindrome("")
```




    True



#### LeetCode 344 Reverse String
`简单` `对撞指针`

> 编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 char[] 的形式给出。
>
> 不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用 O(1) 的额外空间解决这一问题。
>
> 你可以假设数组中的所有字符都是 ASCII 码表中的可打印字符。


```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: None Do not return anything, modify s in-place instead.
        """
        l, r = 0, len(s) - 1
        while l < r:
            s[l], s[r] = s[r], s[l]
            l, r = l + 1, r - 1
        return s
```

#### LeetCode 345 Reverse String
`简单` `对撞指针`

> 编写一个函数，以字符串作为输入，反转该字符串中的元音字母。


```python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        sp_list = ['a', 'o', 'e', 'i', 'u', 'A', 'E', 'I', 'O', 'U']
        s = list(s)
        l, r = 0, len(s) - 1
        while l < r:
            if s[l] not in sp_list:
                l += 1
            elif s[r] not in sp_list:
                r -= 1
            else:
                s[l], s[r] = s[r], s[l]
                l += 1
                r -= 1
        return ''.join(s)
```

#### LeetCode 11 Container With Most Water
`中等` `对撞指针`

> 给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。
>
> 说明：你不能倾斜容器，且 n 的值至少为 2。



```python
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max_area = 0
        l, r = 0, len(height) - 1
        while l < r:
            cur_area = (r - l) * min(height[l], height[r])
            max_area = max(max_area, cur_area)
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1
        return max_area
```

### 2.5 滑动窗口（双索引技术）
