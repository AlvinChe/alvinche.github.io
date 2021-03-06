---
title: Leetcode-3 无重复字符的最长子串 Python
copyright: true
date: 2019-04-02 10:32:35
tags: leetcode
categories: 学习
---

#### 1. [题目](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/submissions/)
>给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。</br>
>示例 1:
>输入: "abcabcbb"
>输出: 3 
>解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。</br>
>示例 2:
>输入: "bbbbb"
>输出: 1
>解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。</br>
>示例 3:
>输入: "pwwkew"
>输出: 3
>解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
>     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。

#### 2. 解题思路
##### 2.1 朴素解法，暴力搜索
&emsp;为了枚举给定字符串的所有子字符串，我们需要枚举它们开始和结束的索引。假设开始和结束的索引分别为 $i$ 和 $j$。那么我们有 $0 \leq i \lt j \leq n $ ,$0≤i<j≤n $（这里的结束索引 j 是按惯例排除的）。因此，使用 $i$ 从0到n - 1,n−1 以及 j 从 i+1 到 n 这两个嵌套的循环，我们可以枚举出 s 的所有子字符串。

&emsp;要检查一个字符串是否有重复字符，我们可以使用集合。我们遍历字符串中的所有字符，并将它们逐个放入 set 中。在放置一个字符之前，我们检查该集合是否已经包含它。如果包含，我们会返回 false。循环结束后，我们返回 true。

##### 2.2 滑动窗口
&emsp;利用python 的字典，或者java中的`Map<Character, Integer> map`
存储每个字符出现位置的索引。
&emsp;使用变量end来记录上次该字符出现的位置长度，删掉从该字符前一次出现，及其以前的重复出现，也可以理解成不重复字符串的开始位置；
&emsp;使用变量m来记录不重复字符出现的最大长度；
&emsp;each是遍历字符串的当前index

``` python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if len(s) == 0 : return 0
        end = 0
        dic = {}
        m = 0
        for each in range(len(s)):
            if s[each] in dic :
                end = max(end,dic[s[each]]+1)
            dic[s[each]] = each
            m = max(m,each-end+1)
            
        return m
```
第二种理解[思路](https://blog.csdn.net/ieearth/article/details/79927955 )：
&emsp;求无重复字符的最长子串的长度，从头到尾遍历字符串时（索引index），考虑到无重复字符，我们先把字符逐个放到容器set中，并更新最长子串的长度，如果遇到了重复字符，即当前遍历的字符在set中，则要从set中删除重复字符，包括这个重复字符前面的所有字符，也就是从当前子串的最左边（left）开始删除，直到删除重复字符

#### 3. 总结/分类
&emsp;字符串，滑动窗口

