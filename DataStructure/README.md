# Data_structure

[TOC]

## 第一章 绪论（上）

### (b)计算模型

#### 01b-1: 性能测度

效率：DSA

度量

#### 01b-2: 问题规模

算法分析：正确性和成本（**运行时间**+存储空间）

问题实例的**规模**，往往是决定计算成本的问题

#### 01b-3: 最坏情况

T(n)

![image-20210713103712643](README.assets/image-20210713103712643.png)

#### 01b-4: 理想模型

实验统计不行

抽象理想平台

#### 01b-5 & 6: 图灵机 & 实例 TM

![image-20210713104352278](README.assets/image-20210713104352278.png)

#### 01b-7: RAM模型 & 实例

random access machine

算法的运行时间 算法需要执行的基本操作次数

### (c)大O记号

#### 01c-1: 主流长远

![image-20210713105454123](README.assets/image-20210713105454123.png)

#### 01c-2: 大O记号

O：上界

Ω：下界（最好情况）

![image-20210713105835365](README.assets/image-20210713105835365.png)

#### 01c-3: 高效解

逐渐复杂

O(1)

O((logn)^c)

#### 01c-4 : 有效解

令人满意

O(n^c)

#### 01c-5 : 难解

无效算法

O(2^n)

#### 01c-6: 2−Subset

Np-complete 不是多项式可以解决的问题

#### 01c-7: 增长速度

![image-20210713111646391](file://D:/Data/postgraduate/work/C++/CppLearningNote/DataStructure/README.assets/image-20210713111646391.png?lastModify=1626146249)

## 第二章 绪论（下）

### (d)算法分析

#### 01d-1: 算法分析

正确性（不变性 x 单调性） + 复杂度

主要方法：

迭代：级数求和

递归：递归跟踪 + 递推方程

猜测 + 验证

#### 01d-2: 级数

![image-20210713143718136](README.assets/image-20210713143718136.png)

![image-20210713144000725](README.assets/image-20210713144000725.png)

#### 01d-3: 循环

O(n^2)

O(n^2)

![image-20210713145203879](README.assets/image-20210713145203879.png)

![image-20210713144903133](README.assets/image-20210713144903133.png)



#### 01d-5: 正确性的证明

![image-20210713150153552](README.assets/image-20210713150153552.png)

#### 01d-6: 封底估算-1 -2

近似估计，定性

三生三世 10^10 

一天 10^5

计算机 1Ghz 10^9

![image-20210713151032088](README.assets/image-20210713151032088.png)

### (e)递归与迭代

#### 01-E-1: 迭代与递归

#### 01-E-2: 减而治之

![image-20210713153446255](README.assets/image-20210713153446255.png)

#### 01-E-3: 递归跟踪

简单递归的分析

![image-20210713153727774](README.assets/image-20210713153727774.png)

#### 01-E-4: 递推方程

![image-20210713154010845](README.assets/image-20210713154010845.png)

#### 01-E-5: 数组倒置

#### 01-E-6: 分而治之

![image-20210713155427534](README.assets/image-20210713155427534.png)

#### 01-E-7: 二分递归：数组求和

![image-20210713155525888](README.assets/image-20210713155525888.png)

### （xc）动态规划

#### 01XC-1: 动态规划

递归获得规律然后转化为迭代

#### 01XC-2: Fib()：递推方程

O(2^n)

#### 01XC-3: Fib()：封底估算

可以得到大概的时间

#### 01XC-4: Fib()：递归跟踪

递归实例被大量重复使用

#### 01XC-5: Fib()：迭代

由自顶向下递归，变为自底向上迭代

#### 01XC-6: 最长公共子序列

LCS

#### 01XC-7: LCS：递归

## 第二章 向量（上）

### (a)接口与实现

#### 02A-1 接口与实现

线性序列：vector和list

1）ADT/实现

2）算法

抽象数据类型 = 数据模型 +  操作

数据结构 = 基于特定语言，实现ADT的一整套算法

#### 02A-2 向量ADT

向量是数组的抽象和泛化，元素的类型不限于基本类型

![image-20210713195424986](README.assets/image-20210713195424986.png)

search是有向序列，不超过e的最大的值

#### 02A-3 接口操作实例

#### 02A-4 构造与析构

Vector模板类

![image-20210727151352653](README.assets/image-20210727151352653.png)

![image-20210727151531144](README.assets/image-20210727151531144.png)

#### 02A-5 复制

![image-20210727151635979](README.assets/image-20210727151635979.png)

### （b）可扩充向量

#### 02B-1 可扩充向量

![image-20210727151841291](README.assets/image-20210727151841291.png)

#### 02B-2 动态空间管理

![image-20210727152346183](README.assets/image-20210727152346183.png)

![image-20210727152412654](README.assets/image-20210727152412654.png)

 

#### 02B-3 递增式扩容

每I次都需要扩容，相当于每次扩容的成本为O(n)

#### 02B-4 加倍式扩容

O(1)

![image-20210727152859993](README.assets/image-20210727152859993.png)

#### 02B-5 分摊复杂度

![image-20210727152938032](README.assets/image-20210727152938032.png)

### （c）无序向量

#### 02C-1 概述

#### 02C-2: 循秩访问

元素访问

![image-20210727163833313](README.assets/image-20210727163833313.png)

![image-20210727163956177](README.assets/image-20210727163956177.png)

#### 02C-3 插入

![image-20210727164127842](README.assets/image-20210727164127842.png)

#### 02C-4 区间删除

![image-20210727164333618](README.assets/image-20210727164333618.png)

#### 02C-5 单元素删除

![image-20210727164658753](README.assets/image-20210727164658753.png)

#### 02C-6 查找

![image-20210727164841398](README.assets/image-20210727164841398.png)

#### 02C-7 唯一化

![image-20210727165320953](README.assets/image-20210727165320953.png)

![image-20210727165554503](README.assets/image-20210727165554503.png)

#### 02C-8 遍历

![image-20210727165721826](README.assets/image-20210727165721826.png)

![image-20210727165849713](README.assets/image-20210727165849713.png)

### （d1）有序向量：唯一化

#### 02D1-1 有序性

![image-20210727193003396](README.assets/image-20210727193003396.png)

#### 02D1-2 唯一化（低效版）

![image-20210727193107492](README.assets/image-20210727193107492.png)

#### 02D1-3 复杂度（低效版）

O(n^2)

#### 02D1-4 唯一化（高效版）

![image-20210727193417833](README.assets/image-20210727193417833.png)

### （d2）有序向量：二分查找

#### 02D2-2 接口

![image-20210727200901613](README.assets/image-20210727200901613.png)

#### 02D2-3 语义

![image-20210727201034483](README.assets/image-20210727201034483.png)

#### 02D2-4 原理

![image-20210727201434473](README.assets/image-20210727201434473.png)

#### 02D2-5 实现

![image-20210727201506277](README.assets/image-20210727201506277.png)

![image-20210727201659305](README.assets/image-20210727201659305.png)

![image-20210727201807727](README.assets/image-20210727201807727.png)

## 第二章 向量（下）

### （d3）有序向量：Fibonacci查找

#### 02D3-2 实现

![image-20210727204005079](README.assets/image-20210727204005079.png)

二分查找相当于在一半的那个点，Fibonacci相当于是在黄金分割比的点

### （d4）有序向量：二分查找（改进）

#### 02D4-1 构思

![image-20210727205436177](README.assets/image-20210727205436177.png)

#### 02D4-2 版本B

![image-20210727205618856](README.assets/image-20210727205618856.png)

#### 02D4-3 语义

![image-20210727205739777](README.assets/image-20210727205739777.png)

所以需要版本C

#### 02D4-4 版本C

![image-20210727205936150](README.assets/image-20210727205936150.png)

### （d5）有序向量：插值查找

#### 02D5-1 原理

上面是考虑单调，现在考虑分布，均匀且独立的随机分布

通过数值来估计选择的点

#### 02D5-2 实例

![image-20210727210936453](README.assets/image-20210727210936453.png)

#### 02D5-3 性能分析

最差是O（n）

![image-20210727211033708](README.assets/image-20210727211033708.png)

![image-20210727211155957](README.assets/image-20210727211155957.png)

### （e）起泡排序

![image-20210727211539701](README.assets/image-20210727211539701.png)

![image-20210727211452506](README.assets/image-20210727211452506.png)

O（n^2）

### （f）归并排序

O（nlogn）

#### 02F-2 归并排序：主算法

![image-20210727212652193](README.assets/image-20210727212652193.png)

#### 02F-3 二路归并：实例

![image-20210727212802404](README.assets/image-20210727212802404.png)

#### 02F-4 二路归并：实现

![image-20210727212913792](README.assets/image-20210727212913792.png)

## 第三章 列表

### （a）接口与实现

#### 03A-1 从静态到动态

#### 03A-2 从向量到列表

![image-20210727220334771](README.assets/image-20210727220334771.png)

#### 03A-3 从秩到位置

![image-20210727220624721](README.assets/image-20210727220624721.png)

#### 03A-4 实现

![image-20210727220728272](README.assets/image-20210727220728272.png)

![image-20210727220751144](README.assets/image-20210727220751144.png)

![image-20210727220806287](README.assets/image-20210727220806287.png)

![image-20210727220851577](README.assets/image-20210727220851577.png)

![image-20210727220919456](README.assets/image-20210727220919456.png)

### （b）无序列表

#### 03B-1 循秩访问

效率低下

![image-20210729204603510](README.assets/image-20210729204603510.png)

#### 03B-2 查找

![image-20210729204749002](README.assets/image-20210729204749002.png)

#### 03B-3 插入与复制

![image-20210729205632596](README.assets/image-20210729205632596.png)

![image-20210729210034039](README.assets/image-20210729210034039.png)

#### 03B-4 删除与析构

![image-20210729210141057](README.assets/image-20210729210141057.png)

![image-20210729210407839](README.assets/image-20210729210407839.png)

#### 03B-5 唯一化

![image-20210729210712004](README.assets/image-20210729210712004.png)

![image-20210729210812046](README.assets/image-20210729210812046.png)

### （c）有序列表

#### 03C-1 唯一化·构思

![image-20210729210859195](README.assets/image-20210729210859195.png)

#### 03C-3 查找

![image-20210729211020612](README.assets/image-20210729211020612.png)

### （d）选择排序

#### 03D-1 构思

从篮子里面找到最大的苹果，然后放在第一个位置

#### 03D-2 实例

![image-20210729211643862](README.assets/image-20210729211643862.png)

#### 03D-3 实现

![image-20210729211718591](README.assets/image-20210729211718591.png)

![image-20210729212056239](README.assets/image-20210729212056239.png)

#### 03D-6 性能

![image-20210729212632434](README.assets/image-20210729212632434.png)

### （e）插入排序

#### 03E-2 构思

![image-20210729212908404](README.assets/image-20210729212908404.png)

#### 03E-4 实例

![image-20210729213101410](README.assets/image-20210729213101410.png)

#### 03E-5 实现

![image-20210729213139548](README.assets/image-20210729213139548.png)

#### 03E-6 性能分析

![image-20210729213405498](README.assets/image-20210729213405498.png)

#### 03E-7 平均性能

![image-20210729213456157](README.assets/image-20210729213456157.png)

