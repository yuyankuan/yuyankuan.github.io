---
layout: post
title: MathJax LiangShuZhiHe
date: 2020-06-21
categories: LiangShuZhiHe
tags: mathjax 
---

mathjax in markdown :)

**关于两数之和的算法**：

介绍一下简单的算法：
给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。

**示例**：

给定nums=[2、7、11、15]，target = 9
因为nums[0]+nums[1]=2+7=9
所以返回[0,1]

对于这道题，首先想到的就是暴力方法，即使用两个for循环，遍历两次数组，看有没有和是目标值的。显然这样时间复杂度太大，O(n*n)
因此需要改良的算法，用到哈希查找的方法。
建立哈希表，从左向右扫描一遍，将整数与索引存放到map中。扫描一遍，对其中的每一个整数K，搜索 target-K 在map中是否存在即可。若存在，则输出 K 与 target-K 的下标即可。此算法的时间复杂度为O(n)
语言：java

**代码：**
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement)) {
            return new int[] { map.get(complement), i };
        }
        map.put(nums[i], i);
    }
    throw new IllegalArgumentException("No two sum solution");
}

**注意：**

转化思想，与其一个个比较数组中的两数之和是否为目标值不如确定一个加数，使用目标值减去其得到另一个加数，看是否在数组中存在