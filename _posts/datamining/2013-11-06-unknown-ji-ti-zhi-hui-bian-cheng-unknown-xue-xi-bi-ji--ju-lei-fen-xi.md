---
layout: post
title: "《集体智慧编程》学习笔记：聚类分析"
description: ""
category: "datamining"
tags: datamining 学习笔记
---
{% include JB/setup %}

# 监督学习&无监督学习

监督学习是利用样板输入和期望输出来学习如何预测的技术。程序通过输入和期望输出的训练后，我们可以再传入一组输入，然后期望程序可以通过前面学到的“知识”产生一个输出。前面讲到的推荐算法就属于监督学习。  
聚类则是一种无监督学习。它的目的在一组数据种找寻某种结构。  

# 数据准备

聚类分析数据准备常见的做法是定义一组公共的属性，并且能够量化。      
比如要做文章的聚类，属性可以是每个单词的个数；要做购物网站买家的聚类，属性可以是够买某个类目下商品的个数，或者金额。  

# 距离量化

聚类要找寻数据的某种结构，就要把数据中的点进行分组。分组的依据很容易理解肯定是根据数据的相似度。  
数据的相似度之前讲推荐算法时已经讲过，可以转换成距离公式来计算。  

# 分级聚类

分级聚类就是不断的把距离最近的2个点进行合并，合并后的点的数据取合并数据的平均值。  
这样最终会生成一个2叉数的结构。  

分级聚类的优点是产生的树状结构很直观。缺点是计算量比较大，需要多轮两两计算距离。  

# K-均值聚类

K均值聚类的计算过程如下：

1. 随机生成K的聚类点
2. 遍历每个数据点，看它们跟哪个聚类点最近
3. 把每个聚类点替换成第2步中离它最近的数据点的平均值
4. 重复2-3两步，直到聚类点稳定

K-均值聚类的优点是运算比较快，只需要计算聚类点和其他点之间的距离就可以了。  

<!--more-->

# 多维缩放

前面讲到，不同数据点的关系主要是通过定义并计算出它们的距离来表示。而一组数据的关系也可以通过它们两两之间的距离来表示。  
这种距离关系，如果需要直观的展现。则需要把它们映射到线、面或平面上，即用一维、二维、三维空间来表示。  

假设用空间里的一个点来代表一个数据，那么我们的目的就是让每两个点在空间中的距离和它们的数据距离尽量一致。  
  
其中误差我们可以用差值的平方和来表示，也就是要让平方和尽量小。  

其中一种实现方法过程如下：

1. 在空间中随机生成n个点，分别代表这n个数据
2. 循环遍历每2个点
3. 当这2个点的空间距离大于数据距离时，把其中一个点的每一项数值按照误差比率乘一个系数（比如0.01），向另一个点靠拢。反之，则每一项数值远离另一个点。
4. 重复2-3两步，直到平方和不再变小。


# 非负矩阵因式分解(NMF)

非负矩阵因式分解是一种比较复杂的技术。涉及到线性代数里的矩阵算法。  

既然叫非负矩阵因式分解，那么首先得先有矩阵，这里的矩阵是什么呢？  
前面我们说过了，我们的原始数据是，一组数据和它的一组公共属性的值。比如一群人和他们对一组电影的打分情况。  

那么一个人，对这组电影的打分，可以看成是一行数据；一部电影，每个人的打分，可以看成是一列数据。这样就可以组成一个矩阵了。


非负矩阵因式分解的过程是，随机定义一组特征列表，特征列表和这组数据组成一个权重矩阵，和公共属性组成特征矩阵。

权重矩阵的含义是，一个数据符合某个特征的程度。比如我喜欢喜剧片，那就应该在喜剧片这个特征下值比较高。

特征矩阵的含义是，一个属性对于某个特征的重要程度。比如周星驰的电影，就应该在喜剧片这个特征下占了重要的地位。  

非负矩阵因式分解的目标是，找到这2个矩阵，使得这2个矩阵的乘积跟原来的矩阵尽量接近。

其中误差我们同样可以用差值的平方和来表示（对矩阵里的每个值），也就是要让平方和尽量小。 

算法运算时使用乘法更新法则（这里先不细讲）。


算法的实现过程如下：

1. 随机生成一个特征矩阵和一个权重矩阵。
2. 计算特征矩阵和权重矩阵的乘积，并计算该乘积与原矩阵的误差。
3. 使用乘法更新法则，生成新的特征矩阵和权重矩阵。
4. 重复2-3两步，直到误差为0或者已经执行了足够多次。

  
NMF优点是能够看到复杂的关联关系，缺点是结果不够直观，很难理解。


问题：

通过权重矩阵和特征矩阵分别能看出什么信息？  
为什么非负矩阵因式分解，有负数会怎么样？  


  