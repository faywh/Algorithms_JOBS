# 数据结构与算法专题之数组篇

@Author：Howard Wonanut

@整理时间： 2020年1月-2月

标记说明：⭐ 综合评价（星星越多，题目质量越高） 🔺 典型题目



[TOC]

## 1 写在前面

虽然数组是一个再简单不过的数据结构了，但是以数组为基础可以出各种各样的相关题目。从数据结构的角度除法，基本的**栈和队列**可以基于数组实现，**并查集**可以使用数组实现，本质上是一个完全二叉树的**堆**也可以使用数组实现，再比如**字符串数组**、**双指针**、**滑动窗口**等等。基于数组可以实现绝大部分的数据结构。再从算法的角度出发，基于数组可以实现**二分查找**（分治思想），**字符串匹配算法**（KMP）、**回溯**（DFS）、离不开数组或者二维数组的**动态规划**等等，可见数组的重要性。

虽然以上的很多算法问题只是将数组看作一个容器，但数组在无形中将以上所有的复杂问题联系在了一起，只有掌握好了数组这个基础的数据结构，解决复杂的问题才能游刃有余。话不多说，上本章节脉络图：



// TODO 脉络图



数组的优点：

- 构建简单
- 能在O(1)的时间内根据数组的下标查询元素
- 对于排序的数组，查询时间复杂度为O(logn)

数组的缺点：

- 插入删除的时间复杂度为O(n)
- 需要占用连续的区间
- 在没有排序的数组中查找元素的复杂度为O(n)



> **忠告**
>
> - 对于每一道题不要只满足于AC，多考虑各种特殊情况以及多种解法。
> - 做题思路：完全理解题意、确定大致思路、考虑边界情况、实现、测试、提交



### 1.1 数组基础知识

// TODO



### 1.2 数组题型解题技巧总结

数组题的技巧主要有：

- 双指针以及多指针的使用可以极大的降低空间复杂度以及时间复杂度
- 滑动窗口思想有时能够解决棘手的问题
- 需要特别注意边界问题



## 2 数组相关题型

### 2.1 快慢指针

- [704-二分查找](./src/704-binary-search.md)  ⭐⭐ 🔺
- [283-移动零](./src/283-move-zeros.md)  ⭐⭐ 🔺
- [27-移除元素](./src/27-remove-element.md)  ⭐⭐
- [26-删除排序数组中的重复项](./src/26-remove-duplicates-from-sorted-array.md)   ⭐
- [80-删除排序数组中的重复项II](./src/80-remove-duplicates-from-sorted-array-ii.md) ⭐⭐⭐ 🔺
- [154. 寻找旋转排序数组中的最小值 II](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array-ii/) `数组`⭐⭐⭐⭐⭐ 🔺



### 2.2 对撞指针

- [167. 两数之和-ii](./src/167-two-sum-ii-input-array-is-sorted.md) ⭐⭐ 🕑
- [125. 验证回文串](https://leetcode-cn.com/problems/valid-palindrome/) ⭐
- [11. 盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/) ⭐⭐⭐



### 2.3 三路快排

`快排思想很重要`

- [75-颜色分类](./src/75-sort-colors.md) ⭐⭐⭐ 🔺
- [215. 数组中的第K个最大元素](./src/215-kth-largest-element-in-an-array.md) ⭐⭐⭐⭐ 🔺 🕑



### 2.4 滑动窗口

- [209. 长度最小的子数组](./src/209-minimum-size-subarray-sum.md)
- [3. 无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)
- [438. 找到字符串中所有字母异位词](https://leetcode-cn.com/problems/find-all-anagrams-in-a-string/)
- [76. 最小覆盖子串](https://leetcode-cn.com/problems/minimum-window-substring/)
- [239. 滑动窗口最大值](https://leetcode-cn.com/problems/sliding-window-maximum/) ⭐⭐⭐⭐ 🔺



### 2.5 数组DP

- [119-杨辉三角](./src/119-pascals-triangle-ii.md) ⭐



### 2.6 数组和矩阵其他题目

- [189-旋转数组](./src/189-rotate-array.md) ⭐⭐⭐ 🔺
- [1232-缀点成线](./src/1232-check-if-it-is-a-straight-line.md) ⭐
- [121-买股票的最佳时机](./src/121-best-time-to-buy-and-sell-stock.md) ⭐