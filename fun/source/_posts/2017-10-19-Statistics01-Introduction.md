---
title: 统计学习方法概论
date: 2017-10-19 14:30:19   
categories: Statistics
tags: 
    - ml
---

# 统计学习

《统计学习方法概论》一些基础概念的整理。

## 特点

计算机基于数据构建概率统计模型并用模型对数据进行预测分析的学科。

1. 统计学习以计算机及网络为平台，建立在计算机及网络上的。
2. 统计学习以数据为研究对象，数据驱动的学科。
3. 统计学习的目的是对数据进行预测与分析。
4. 统计学习以方法为中心，构建模型并应用模型进行预测与分析。
5. 统计学习是概率论、统计学、信息论、计算理论、最优化理论及计算机科学等对个领域的交叉学科。

学习的定义：**如果一个系统能够通过执行某个过程改进他的性能，这就是学习。**

## 统计学习的对象

- 统计学习的对象是数据。
- 统计学习对于数据的基本假设是同类数据具有一定的统计规律性，这是统计学习的前提。
- 以变量或变量组表示数据。数据分为由连续变量和离散变量表示的类型。

## 统计学习的目的

考虑学习什么样的模型和如何学习模型，以使模型能对数据进行准确的预测与分析，同时也要考虑尽可能地提高学习效率。

## 统计学习的方法

### 分类

- 监督学习
- 非监督学习
- 半监督学习
- 强化学习

### 方法概括

- 从给定的、有限的、用于学习的训练数据集合出发，假设数据是独立同分布产生的；
- 并假设要学习的模型属于某个函数的集合，称为假设空间；
- 应用某个评价标准，从假设空间中选取一个最优模型，使他对已知训练数据及未知测试数据在给定的评价准则下有最优的预测；
- 最优模型的选取由算法实现。

### 三要素

- 模型的假设空间——模型
- 模型选择的准侧——策略
- 模型学习的算法——算法

### 步骤

1. 得到一个有限的训练数据集合
2. 确定包含所有可能的模型的假设空间，即学习模型的集合
3. 确定模型选择的准则，即学习的策略
4. 实现求解最优模型的算法，即学习的算法
5. 通过学习方法选择最优模型
6. 理由学习的最有模型对新数据进行预测或分析

## 统计学习的研究

包括

- 统计学习方法：开发新的学习方法
- 统计学习理论：探求统计学习方法的有效性和效率，以及基本理论问题
- 统计学习应用：将统计学习方法应用到实际问题中去，解决实际问题

## 统计学习的重要性

1. 统计学习是处理海量数据的有效方法
2. 统计学习是计算机智能化的有效手段
3. 统计学习是计算机科学发展的重要组成部分

---

# 监督学习

## 基本概念

### 输入控件、特征空间与输出空间

- 在监督学习中，将输入与输出所有可能取值的集合称为输入空间与输出空间。

- 每个具体的输入时一个实例，通常由特征向量表示，所有特征向量组成特征空间。输入空间映射到特征空间，或直接作为特征空间。模型都是定义在特征空间上的。

- 将输入输出看作是定义在输入空间与输出空间上的随机变量的取值。输入、输出变量用大写字母表示，习惯上输入变量为X，输出变量为Y。输入输出变量的取值用小写字母表示，输入变量的取值写作x，输出变量的取值写作y。

- 以加上转置符号T的行向量表示列向量。

   $$
   x=(x^{(1)},x^{(2)},...,x^{(t)},...,x^{(n)})^T
   $$
   $x^{(1)}​$表示x的第i个特征。注意$x^{(1)}​$与$x_i​$不同，后者表示多个输入变量的第i个。即
   $$
   x_i=(x^{(1)}_i,x^{(2)}_i,...,x^{(t)}_i,...,x^{(n)}_i)^T
   $$

- 监督学习从训练数据集合中学习模型，对测试数据进行预测，训练数据由输入与输出对组成，训练集通常表示为

   $$
   T=\{(x_1,y_1),(x_2,y_2),...(x_N,y_N)\}
   $$

- 测试数据也由相应的输入和输出组成，输入与输出对又称为样本或样本点。

- X和Y可以是连续的也可以是离散的。根据输入、输出变量的不同类型，给与不同名称：

   - 回归问题：X与Y均为连续变量
   - 分类问题：Y为有限个离散变量
   - 标注问题：X与X均为离散变量


### 联合概率分布

监督学习假设X与Y遵循联合概率分布$P(X,Y)$，表示分布函数。在学习过程中，假设这一联合概率分布存在，但对学习系统来说，联合概率分布的具体定义是未知的。训练数据与测试数据被看作是依联合概率分布$P(X,Y)$独立同分布产生的。**统计学习假设数据存在一定统计规律**，X和Y具有联合概率分布的假设就是监督学习关于数据的基本假设。

###  假设空间

- 监督学习的目的在于学习一个由输入到输出的映射，即模型。


- 模型输入由属于空间到输出空间的映射的集合。这个集合就是假设空间。
- 监督学习的模型可以是概率模型或非概率模型，由条件概率分布$P(Y|X)$或决策函数$Y=f(X)$表示，虽具体学习方法而定。对具体的输入进行相应的输出预测时，写作$P(y|x)$ 或$y=f(x)$

## 问题的形式化

监督学习利用训练数据学习模型，训练数据是人工给出的，所以称为监督学习。

监督学习分为学习和预测两个过程，由学习系统和预测系统完成：

![监督学习问题](/images/2017-10-19-Statistics01-Introduction-0.jpg)

# 统计学习三要素

## 模型

- 占

## 策略

### 损失函数和风险函数

损失函数度量模型一次预测的好坏，风险函数度量平均意义下模型预测的好坏。

#### 0-1损失函数

$$
L(Y,f(X))=
\begin{cases}
1, & Y \neq f(X) \\
0, & Y=f(X) \\
\end{cases}
$$

#### 平方损失函数

$$
L(Y,f(X))=(Y-f(x))^2
$$

#### 绝对损失函数

$$
L(Y,f(X))=\lvert (Y-f(x))\rvert
$$

#### 对数损失函数或对数似然损失函数

$$
L(Y,P(Y\vert X))=-\log P(Y\vert X)
$$

可知损失函数越小，模型就越好。

所以损失函数的期望值是（也称风险函数或期望损失）：

$$
R_{exp}(f)=E_{p}[L(Y,f(X))]=\int_{x\times y}L(y,f(x))P(x,y)dxdy
$$

平均损失称为经验风险

$$
R_{emp}(f)=\frac {1}{N}\sum_{i=1}^{N}L(y_i,f(x_i))
$$




根据大数定律，当样本容量N趋于无穷时，经验风险趋于期望风险。但是训练样本有限，甚至很小，所以用经验风险估计期望风险常常不理想，要对经验风险进行一定的矫正。这就引入两个基本策略：

- 经验风险最小化
- 结构风险最小化
#### 经验风险最小化与结构风险最小化

经验风险最小的模型就是最有模型，其中$F$是假设空间：

$$
\min_{f\subset F}\frac {1}{N}\sum_{i=1}^{N}L(y_i,f(x_i))
$$

当样本容量大时，有很好的效果，比如极大似然估计就是经验风险最小化的一个例子。

**当模型使条件概率分布，损失函数是对数损失函数的时候，经验风险最小化就等价于极大似然估计**

但是！

当样本容量很小时会产生**过拟合**。

---

结构风险最小化等价于正则化。结构风险在经验风险上加上表示模型复杂度的正则化项或罚项。

$$
\min_{f\subset F}R_{srm}(f)=\frac {1}{N}\sum_{i=1}^{N}L(y_{i},f(x_{i})+\lambda J(f))
$$

- $J(f)$为模型的复杂度，是定义在假设空间上的范函。
- 模型$f$越复杂，复杂度$J(f)$就越大。
- 当模型是条件概率分布，损失函数是对数损失函数，模型复杂度由模型的先验概率表示时，结构风险最小化等价于贝叶斯估计中的最大后验概率估计
## 算法

- 占

# 模型评估与模型选择

## 训练误差与测试误差

当损失函数给定时，基于损失函数的模型训练误差和模型测试误差就自然成为学习方法评估的标准。

训练误差是训练数据集的平均损失：
$$
R_{emp}(\hat f)=\frac {1}{N}\sum_{i=1}^{N}L(y_i,\hat f(x_i))
$$

测试误差关于测试数据集的平均损失：
$$
e_{test}=\frac {1}{N^{'}}\sum_{i=1}^{N^{'}}L(y_i,\hat f(x_i))
$$

- 训练误差的大小，对判断给定的问题是不是一个容易学习的问题是有意义的，但本质上不重要。
- 测试误差反映了学习方法对未知的测试数据集的预测能力，是学习中的重要概念。

显然给定两种学习方法，测试误差小的方法具有更好的预测能力，是更有效的方法。

**将学习方法对未知数据的预测能力成为泛化能力。**

## 过拟合与模型选择

当假设空间含有不用复杂度（不同参数个数）的模型时，就要面临模型选择的问题。

- “真模型”是理想模型，我们的选择要尽可能逼近真模型，参数个数要与真模型相同。
- 过拟合：一味的提高对训练数据的预测能力，所选模型的复杂度往往比真模型要高，这种现象称为过拟合。过拟合是指学习时选择的模型所包含的参数过多。以至于出现这一模型对已知数据预测的很好，但对未知数据预测很差的现象。

**实例说明过拟合和模型选择：**

给定数据集$T=\{(x_{1},y_{1}),(x_{2},y_{2}),...,(x_{N},y_{N})\}$

假设给定10个数据点，用0~9次多项式函数对数据进行拟合。

![](/images/2017-10-19-Statistics01-Introduction-1.jpg)

设M次多项式为：
$$
f_{M}(x,w)=w_{0}+w_{1}x+w_{2}x^{2}+...+w_{M}x^{M}=\sum_{j=0}^{M}w_{j}x^{j}
$$
解决这一问题的方法：

1. 首选选择模型的复杂度，即确定多项式的次数；

2. 在给定的复杂度下，按照经验风险最小化策略，求解参数，即多项式系数。

3. 使用平方损失函数：
   $$
   L(w)=\frac {1}{2}\sum_{i=1}^{N}(f(x_{i},w)-y_{i})^2
   $$

4. 这是一个简单的最优化问题，将模型带入上式：
   $$
   L(w)=\frac {1}{2}\sum_{i=1}^{N}(\sum_{j=0}^{M}w_{j}x_{i}^{j}-y_{i})^{2}
   $$
   使用最小二乘法可以得出最优的多项式系数。

   上图给出了M=0，M=1，M=3，M=9时多项式的函数拟合情况。

   明显！

   - M=0：0个参数的形态是横线，拟合效果很差。
   - M=1：斜线拟合效果也很差。
   - M=9：通过训练数据的每个点，从训练数据的拟合角度来说，这是最好的结果。

   但是！

   训练数据本身可能存在噪声，这种拟合对于未知数据的预测能力不是最好的。这种现象就叫**过拟合。**


训练误差和测试误差的关系见下图：

![](/images/2017-10-19-Statistics01-Introduction-2.jpg)

明显对于测试误差来说，中间的某个状态是最优的，如何选择呢？

**正则化与交叉验证**！

# 正则化与交叉验证

## 正则化
