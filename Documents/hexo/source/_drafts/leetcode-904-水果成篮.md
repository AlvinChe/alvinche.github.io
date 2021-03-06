---
title: leetcode - 904 水果成篮
tags:
- leetcode 
- 刷题笔记
date: 2019-03-13 14:56:44
---



---

>在一排树中，第 i 棵树产生 tree[i] 型的水果。
>你可以从你选择的任何树开始，然后重复执行以下步骤：
>
<!--more-->
>把这棵树上的水果放进你的篮子里。如果你做不到，就停下来。
>移动到当前树右侧的下一棵树。如果右边没有树，就停下来。
>请注意，在选择一颗树后，你没有任何选择：你必须执行步骤 1，然后执行步骤 2，然后返回步骤 1，然后执行步骤 2，依此类推，直至停止。
>
>你有两个篮子，每个篮子可以携带任何数量的水果，但你希望每个篮子只携带一种类型的水果。
>用这个程序你能收集的水果总量是多少？
>
>>示例 1：
>>
>>输入：[1,2,1]
>>输出：3
>>解释：我们可以收集 [1,2,1]。
>>示例 2：
>
>>输入：[0,1,2,2]
>>输出：3
>>解释：我们可以收集 [1,2,2].
>>如果我们从第一棵树开始，我们将只能收集到 [0, 1]。
>>示例 3：
>
>>输入：[1,2,3,2,2]
>>输出：4
>>解释：我们可以收集 [2,3,2,2].
>>如果我们从第一棵树开始，我们将只能收集到 [1, 2]。
>>示例 4：
>
>>输入：[3,3,3,1,2,1,1,2,3,3,4]
>>输出：5
>>解释：我们可以收集 [1,2,1,1,2].
>>如果我们从第一棵树或第八棵树开始，我们将只能收集到 4 个水果。

### 解题思路
这题其实要求其实很简单，就是找出数组中长度最大的连续由2种元素构成的子数组，返回这个子数组的长度。但由于本题有时间限制，只是朴素的解法会出现超时的情况，需要对实现进行一定的优化。

参考花花酱的hashtable+ sliding windows
![花花酱解法](https://upload-images.jianshu.io/upload_images/1016401-daaa3408bc498df7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

```c++
class Solution {
public:
// 朴素解法
    int totalFruit(vector<int>& tree) {
        int size = tree.size();
        int fruit[size] = {0};
        int max =0;
        
        for(int i = 0; i< size;i++){
            int number = 1;
            int type1 = -1;
            // 第一种水果
            type1 = tree[i];
            int type2 = -1;
            for(int j = i+1; j<size ;j++){
                // 第二种水果
                if(tree[j]!=tree[i]){
                    // type2 is null
                    if(type2 < 0){
                        type2 = tree[j];
                        number++;
                    }else{
                        // 出现第三种水果，跳出循环
                        if(tree[j] != type2){
                            break;
                        }else{
                            number++;
                        }
                    }
                    
                }else{
                    number++;
                }
            }
            fruit[i] = number;
            if(number> max)
                max = number;
        }
        return max;
    }
    
   
public:
// by [花花酱] (https://zxi.mytechroad.com/blog/hashtable/leetcode-904-fruit-into-baskets/)

  int totalFruit(vector<int>& tree) {        
    map<int, int> idx; // {fruit -> last_index}
    int ans = 0;
    int cur = 0;
    for (int i = 0; i < tree.size(); ++i) {
      int f = tree[i]; // 取一种水果
      if (!idx.count(f)) { // 返回值只有0或1
         // !idx.count(f) ==  1,即出现某种新水果时
        if (idx.size() == 2) { // 如果已经有了两种水果，再出现第三种水果的时候
          auto it1 = begin(idx); 
          auto it2 = next(it1);
          if (it1->second > it2->second) swap(it1, it2);
          // 找到之前两种水果中，下标最小的水果，开始新的窗口
          cur = i - it1->second - 1; // cur存新窗口的大小       
          idx.erase(it1); // 删除下标较小的水果
        }       
      }   
      // 添加新水果的下标信息
      idx[f] = i;  
      // 比较新窗口和上一个窗口的大小
      ans = max(++cur, ans);
    }
    return ans;
  }

};
```

