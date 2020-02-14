---
title: Defensive Quantization
tags: 
	- Quantization
	- Defense
	- Attack
---


- Lipschitz constant
用来描述 输入波动对输出波动影响大小 的量
波动的大小可以用：
$$ D(X, X^{adj}) = \frac{|| X - X^{adj} ||^2}{||X||^2}$$
有一个函数，$f: X \to Y$ 如果满足
$$ D_Y(f(x_1), f(x_2)) \le k D_X(x_1, x_2), \forall x_1, x_1 \in X $$
对于实数$k \ge 0$, 那么函数$f$被称为 Lipschitz continuous，它的Lipschitz constant是$k$.

对于CNN来说，输入是图片，输出是某一个视觉任务，比如分类任务。当对输入的图片进行扰动(对抗攻击)时，输出也会发生变化，在一些情况下会导致错误的分类。可以简单的认为：Lipschitz 约束强时，任务网络应对攻击的能力强，对应的鲁棒性好。

# Motivation

<img src="dq_motivation.png" width="50%" height="50%">

# Method

## 攻击方法


## 防御方法


## DQ

# Experiments

