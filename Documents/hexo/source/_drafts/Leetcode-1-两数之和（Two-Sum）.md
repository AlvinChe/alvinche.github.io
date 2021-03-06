---
title: Leetcode -1 两数之和（Two Sum）
copyright: true
date: 2019-04-01 13:57:26
tags:
 - leetcode
categories: 学习
---

#### 1. [题目](https://leetcode-cn.com/problems/two-sum/)
> 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
> 你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。
> 示例:
> 给定 nums = [2, 7, 11, 15], target = 9
> 因为 nums[0] + nums[1] = 2 + 7 = 9
> 所以返回 [0, 1]

#### 2. 解题思路
##### 2.1 朴素解法（暴力遍历）
通过两次循环，每次循环遍历列表，这种算法的时间复杂度是 `O(n^2)`

##### 2.2 哈希存储
思路：利用hash表，key：当前值，value：索引
解题方法：遍历数组时，查询hash表中，是否存在target - nums[i]。
若有，返回当前索引和存在的key的value；
若不存在，则将当前值和索引存入hash表中
python中的字典就是天然hash表；c++中的unorder_map；
Java中`HashMap<Integer,Integer> hm = new HashMap<Integer,Integer>(); `

代码如下：
``` python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_hash = {}
        for each in range(len(nums)):
            dif = target - nums[each]
            if dif in nums_hash:
                return [nums_hash[dif], each]
            else:
                nums_hash[nums[each]] = each
```

#### 3. 总结/分类
数据结构的巧妙利用