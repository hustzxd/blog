---
title: Transposed Convolution in PyTorch
tags:
  - PyTorch
  - Transposed Convolution
date: 2019-05-21 17:02:45
---


# 引言
Convolution运算的一些参数我们结合图示比较容易理解，卷积核在feature map中滑动，对应元素乘加得到输出。但是Transposed Convolution具体是怎么运算的，其中的参数配置又有什么具体的作用，需要我们初学者深入研究一下。

<img src="no_padding_strides.GIF" width="20%" height="20%">
如图所示，对于Convolution来说，下层为输入，上层为输出；对于Transposed Convolution来说，为Convolution的逆运算或者求导运算，上层为输入，下层为输出。

# Transposed Convolution in PyTorch


## 参数列表
```
torch.nn.ConvTranspose1d(in_channels, out_channels, kernel_size, stride=1, padding=0, output_padding=0, groups=1, bias=True, dilation=1, padding_mode='zeros')
```

与公式中变量的对应关系为：

| Param        | Variable name |
|--------------|---------------|
| in_channels  | $c_{in}$    |
| out_channels | $c_{out}$      |
| kernel_size  | $k$       |
| stride       | $s$         |
| padding      | $p$    |
| output_padding | $op$ |
| groups       | $g$ |
| dilation     | $d$ |


$$
L_{out} = L_{in} * s - 2 \times p + d \times (k - 1) + op + 1
$$


```python
In [14]: deconv
Out[14]: ConvTranspose1d(1, 1, kernel_size=(3,), stride=(1,), bias=False)

In [15]: x
Out[15]: tensor([[[1., 1.]]])

In [16]: deconv.weight
Out[16]: 
Parameter containing:
tensor([[[1., 1., 1.]]], requires_grad=True)

In [17]: y = deconv(x)

In [18]: y
Out[18]: tensor([[[1., 2., 2., 1.]]], grad_fn=<SqueezeBackward1>)
```
<img src="IMG_0241.jpg" width="20%" height="20%">

```python
In [22]: x
Out[22]: tensor([[[1., 1.]]])

In [23]: deconv
Out[23]: ConvTranspose1d(1, 1, kernel_size=(3,), stride=(2,), bias=False)

In [24]: deconv.weight
Out[24]: 
Parameter containing:
tensor([[[1., 1., 1.]]], requires_grad=True)

In [25]: y = deconv(x)

In [26]: y
Out[26]: tensor([[[1., 1., 2., 1., 1.]]], grad_fn=<SqueezeBackward1>)
```
<img src="IMG_0242.jpg" width="20%" height="20%">

```python
In [30]: x
Out[30]: tensor([[[1., 1.]]])

In [31]: deconv
Out[31]: ConvTranspose1d(1, 1, kernel_size=(3,), stride=(4,), bias=False)

In [32]: deconv.weight.data
Out[32]: tensor([[[1., 1., 1.]]])

In [33]: y = deconv(x)

In [34]: y
Out[34]: tensor([[[1., 1., 1., 0., 1., 1., 1.]]], grad_fn=<SqueezeBackward1>)
```
<img src="IMG_0243.jpg" width="20%" height="20%">

## Convert Transposed Convolution to Convolution
{% pdf deconv.pdf %}

