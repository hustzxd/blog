---
title: Deep Leakage from Gradients
tags:
  - Attack
  - distributed training
  - collaborative learning
date: 2020-01-16 18:16:11
---


# Motivation
<img src="dlg_motivation.png" width="70%" height="70%">
在分布式多节点训练时，模型是共享的，梯度由每个节点根据私有的数据训练产生，然后参数服务器根据梯度来更新模型。

共享部分：
模型 （包括网络结构和权重）

私有部分：
每个子节点的训练数据

可获取：
有私有训练数据产生的梯度

DLG的原理：**通过梯度来获取私有的训练数据**


> 个人理解总结

## 简单函数完全可逆
假设简单函数如下，简单函数的要求是可以写出其导数的解析表达式
$$y = wx^2$$
根据BP算法，可以得出权重的梯度：
$$
\nabla w = \nabla y\cdot 2x \\
\nabla y = y - label \\
$$

## 复杂模型宏观可逆
通过DLG可以
Given learning model F() and its weights W, if we have the $\nabla w$
Obtain the training data

# Method
<img src="dlg_method.png" width="70%" height="70%">
方法也非常的简单，根据图示，根据随机的输入和label，便可以得到梯度$\nabla W'$，优化$||\nabla W - \nabla w'||^2$就可以了。优化时，将input和label看做可更新的变量，它们的梯度通过BP链反传得到。经过一定的迭代次数后，便能得到高度相似的输入


<img src="out.gif" width="40%" height="40%">
可以粗略的总结为，$\nabla W$与 $x$之间时双射关系，可以根据其中一个，得到对应的另一个。
<img src="dlg_image.png" width="20%" height="20%">

## batch 训练引出的问题
在实际训练中，通常是一个batch来产生一组梯度，假设 batch size = N，那么就有$N!$组合，这些组合产生的梯度是相同的，映射关系如下图所示

<img src="dlg_batch.png" width="20%" height="20%">
在这种条件下，如果同时调节batch的输入，那么每个instance的学习方向往往是不能确定的。paper中也给了解决方案，就是每次只更新batch中的一个instance，这样最终把整个batch更新完。

需要注意的是红框标记部分，DLG只学到了batch组合中的一种情况，和原始图片的顺序不相同，这也和前文的分析一致。
<img src="dlg_result.png" width="70%" height="70%">

## Defense Strategies
- Noisy Gradients (复杂模型宏观可逆)
- Gradient Compression and Sparsiﬁcation (复杂模型宏观可逆)
- Large Batch, High Resolution and Cryptology
	DLG currently only works for batch size up to 8 and image resolution up to 64×64.









