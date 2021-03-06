---
title: LR 机器学习复习笔记-1
tags: 
- 机器学习
- 面试复习
categories: [学习]
mathjax:  true
toc: true
date: 2019-03-14 10:39:00
---



#### 1. 基本原理

<!--more-->

逻辑斯特回归，Logistic Regression，二分类问题

+ 算法性质：他的输出永远在0到1之间
+ 适用情况：标签y取离散值
+ 如何拟合参数的：
  + 将根据参数得到的计算值映射到0-1区间

#### 2. 推导公式

训练集：$ { ( x ^ {  ( 1 )  } ,y ^ { ( 2 )  } ) , ( x ^ { ( 1 ) },y ^ { ( 2 ) } ),...,( x ^ { ( m ) },y ^ { ( m ) } ) } $

数据范围：$  x \in [ x_0 , x_1 , ... , x_n ] ^T , y \in { \{0,1\} } ​$ 

LR映射函数 sigmoid :  $    h_\theta(x) = \dfrac{ 1 } { 1+e^{ - \theta^T x} } ​$ 

损失函数：$Cost(h_\theta(x),y) = -y \log(h_\theta( x ) )  - (1-y) \log(1-h_\theta(x)  )$ 

> PS:为什么不用线性模型的平方和（MSE）
>
> 答：将平方和带入 $ h_\theta(x) $  会得到一个非凸函数（non-convexfunction），非凸函数影响梯度随机算法寻找全局最小值

代价函数：$ J(\theta)= \dfrac{ 1 } { m } \sum^m_{ i=1 }  Cost(h_\theta(x^{ (i ) } ) - y ^ { ( i ) } ) $

> 代价函数与损失函数关系：个体与总体的关系



#### 3. 代价函数代码

```python
import numpy as np
def cost(theta, X, y)：
	theta = np.matrix(theta)
    X = np.matrix(X)
    y = np.matrix(y)
    first = np.multiply(-y, np.log(sigmoid(X*theta.T)))
    second = np,multiply(1-y,np.log(1-sigmoid(X*theta.T)))
    return np.sum(first-second)/(len(X))
    
```



#### 4. 如何求得使代价函数最小的参数

**梯度下降算法**: $repeat  { \{  \theta_ j:= \theta_j - \alpha \frac { \partial } { \partial_{ \theta_j } } J (\theta) \}  } ;​ $

$ Want \min _\theta J(\theta) ​ $:

$ repeat  { \{  \theta_ j:= \theta_j - \alpha \frac{ 1 } { m } \sum_{ i=1 }^m  (h_\theta( x ^ { i } )  - y^{ ( i ) } ) }  x_j^ { ( i ) } $





#### 5. 如何理解梯度下降

参考这篇文章：[深入浅出--梯度下降法及其实现](https://www.jianshu.com/p/c7e642877b0e)

复习的时候脑子一时短路，想不明白梯度下降的原理了



#### 6. 面试常常问到的问题

后面再补