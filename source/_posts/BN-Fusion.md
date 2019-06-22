---
title: BN_Fusion
tags:
  - PyTorch
  - Batch Normalization
date: 2019-02-26 21:18:23
---


# 引言
在PyTorch中，我们常在网络中遇到BN层，基本单元如果如下所示，则可以离线将Conv和BN进行fusion，从而在inference时不必计算BN。

![conv_bn](conv_bn.svg)

在PyTorch中`BatchNorm2d`的定义如下：
```py
class torch.nn.BatchNorm2d(num_features, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
```
参数列表如下：
```py
dict_keys(['weight', 'bias', 'running_mean', 'running_var', 'num_batches_tracked'])
```
与公式中变量的对应关系为：

| Param        | Variable name |
|--------------|---------------|
| eps          | $\epsilon$    |
| weight       | $\gamma$      |
| bias         | $\beta$       |
| running_mean | $\mu$         |
| running_var  | $\sigma^2$    |

# Key Idea
Convolution layer:
$$
	Y = X * w + b
$$
BatchNorm layer:
$$
	Y = \frac{X - \mu}{\sqrt{\sigma^2 + \epsilon}}  \gamma + \beta
$$ 

Convolution and BatchNorm fusion:

$$
	Y = \frac{(X * w + b) - \mu}{\sqrt{\sigma^2 + \epsilon}}  \gamma + \beta \\
	Y = \frac{\gamma w}{\sqrt{\sigma^2 + \epsilon}}X + \frac{b - \mu}{\sqrt{\sigma^2 + \epsilon}}\gamma + \beta \\
	w_{merged} = aw; \quad 
	b_{merged} = (b - \mu)a + \beta; \quad 
	a = \frac{\gamma}{\sqrt{\sigma^2 + \epsilon}}
$$

## Uniform Quantization

$$r = Sq$$ where constants $S$ is quantization parameter, intergers $q$ are mapped to real numbers $r$.

| param |            | type                    |
|-------|------------|-------------------------|
| S     | Scale      | fp32                    |
| q     | quantize   | int4 for w int5 for a   |

Quantized convolution layer:
$$
	Y = X * Sw_q + b \\
	where: w = Sw_q
$$

Quantized convolution and BatchNorm fusion:

$$
	Y = \frac{(X * Sw_q + b) - \mu}{\sqrt{\sigma^2 + \epsilon}}  \gamma + \beta \\
	Y = \frac{\gamma Sw_q}{\sqrt{\sigma^2 + \epsilon}}X + \frac{b - \mu}{\sqrt{\sigma^2 + \epsilon}}\gamma + \beta \\
	S_{merged} = aS; \quad
	w_{merged} = aw; \quad 
	b_{merged} = (b - \mu)a + \beta; \quad 
	a = \frac{\gamma}{\sqrt{\sigma^2 + \epsilon}}
$$

# References:

1. [Docs: torch.nn.BatchNorm2d](https://pytorch.org/docs/stable/nn.html?highlight=batchnorm#torch.nn.BatchNorm2d)
2. [BN层合并原理及实现](https://www.jianshu.com/p/e042d693f3fb)