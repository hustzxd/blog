---
title: paper-of-quantization
date: 2020-9-10 17:20:22
tags:
	- paper
	- quantization
---

## 1. Post-Training Quantization(PTQ)

[**EasyQuant**](#2020), [**LAQ**](#2020), [**ACIQ**](#2019), [**Post training**](#2019)

## 2. Training-Aware Quantization(TAQ)

---

## 3. Binary

---

### 2020
1. **LSQ**: Learned Step Size Quantization **ICLR2020**
52. Mixed Precision DNNs: All you need is a good parametrization **ICLR2020 sony**
54. **HAWQv2**: Hessian Aware trace-Weighted Quantization of Neural Networks
55. **LLSQ**: Learned Symmetric Quantization of Neural Networks for Low-precision Integer Hardware. **ICLR2020** **ICT**
56. **ZeroQ**: A Novel Zero-Shot Quantization Framework. **Berkeley, Peking University**
57. **SS-Auto**: A Single-Shot, Automatic Structured Weight Pruning Framework of DNNs with Ultra-High Efficiency. **IBM Watson Lab**
58. **IR-Net**: Forward and Backward Information Retention for Accurate Binary Neural Networks. **CVPR2020**
59. **BiDet**: An Efficient Binarized Object Detector. **CVPR2020**
60. **BBG**: Balanced Binary Neural Networks with Gated Residual.
1. **APQ**: Joint Search for Network Architecture, Pruning and Quantization Policy. **CVPR2020 MIT** architecture, channel pruning, HAQ三者结合的NAS方法，可操作性确实更好，motivation也合适。
2. **SAT**: Rethinking neural network quantization. Scale-Adjusted Training **ICLR2020 reject** [paper](https://openreview.net/forum?id=HygQ7TNtPr) 
1. **EasyQuant**: Post-training Quantization via Scale Optimization. 优化每层的输出的与余弦距离 [code](https://github.com/deepglint/EasyQuant)中给出了加速效果实验
2. **LAQ**: Loss Aware Post-training Quantization [code](https://github.com/ynahshan/nn-quantization-pytorch/blob/master/lapq/README.md) **intel AIPG** ACIQ的进化版，方法更加简洁，实现更直接，效果也更加好



### 2019
#### ICLR
1. **ACIQ**: analytical clipping for integer quantization of neural networks. **ICLR2019 reject** **intel AIPG**
44. Per-Tensor Fixed-point quantization of the back-propagation algorithm. **ICLR2019**
45. **RQ**: Relaxed Quantization for disretized NNs. **ICLR2019**

#### NIPS
1. **Post training** 4-bit quantization of convolution networks for rapid-deployment. **NIPS 2019** AIPG, Intel

#### ICCV
1. **DSQ**: Differentiable Soft Quantization: Bridging Full-Precision and Low-Bit Neural Networks. **ICCV2019** SenseTime, Beihang

#### CVPR

1. **FQN**: Fully Quantized Network for Object Detection. **CVPR2019**
53. **QIL**: Learning to Quantize Deep Networks by Optimizing Quantization Intervals with Task Loss **CVPR2019**

#### Other

1. **SAWB**: Accurate and efficient 2-bit quantized neural networks. **sysml2019**
47. **SQuantizer**: Simultaneous Learning for Both Sparse and Low-precision Neural Networks. **2019** AIPG, Intel
48. Distributed Low Precision Training Without Mixed Precision. **Oxford snowcloud.ai**
49. __Adaptive__ Precision Training: Quantify Back Propagation in Neural Networks with Fixed-point Numbers. **ICT Cambricon** int8 for weights and activations, int16 for most of the gradients.
50. **AdaBits**: Neural Network Quantization with Adaptive Bit-Widths. **ByteDance** 想法和上篇论文很像
50. **WAGEUBN**: Training High-Performance and Large-Scale Deep Neural Networks with Full 8-bit Integers. 应该算是WAGE的进阶版了

### 2018

#### ICLR2018
1. **VNQ**: Variational network quantization. **ICLR2018**
16. **WAGE**: Training and Inference with Integers in Deep Neural Networks. **ICLR2018** oral tsinghua 不仅量化了weight,activation还量化了error, gradient.
21. Alternating multi-bit quantization for recurrent neural networks. **ICLR2018** alibaba
28. Mixed Precision Training. FP16 training **ICLR2018** baidu
30. Model Compression via distillation and quantization. **ICLR2018** google
33. Quantized back-propagation: training binarized neural networks with quantized gradients. **ICLR2018**

#### CVPR2018
1. **Clip-Q**: Deep network compression learning by In-Parallel Pruning Quantization. **CVPR2018** SFU quantization 与pruning同时进行，达到更优的压缩结果。先使用贝叶斯优化搜索 layer-wise的（p,q),然后在进行fine-turning，达到最大目的的压缩权重，没有涉及到激活值的量化和压缩
23. **ELQ**: Explicit loss-error-aware quantization for low-bit deep neural networks. **CVPR2018** intel tsinghua
31. Quantization and training of neural networks for efficient integer-arithmetic-only inference. **CVPR2018** Google
37. **TSQ**: two-step quantization for low-bit neural networks. **CVPR2018**
36. **SYQ**: learning symmetric quantization for efficient deep neural networks. **CVPR2018** xilinx
32. Towards Effective Low-bitwidth Convolutional Neural Networks. **CVPR2018**

#### ECCV2018
1. **LQ-NETs**: learned quantization for highly accurate and compact deep neural networks. **ECCV2018** Microsoft
19. **Bi-Real Net**: Enhancing the performance of 1-bit CNNs with improved Representational capability and advanced training algorithm. **ECCV2018** HKU
38. **V-Quant**: Value-aware quantization for training and inference of neural networks. **ECCV2018** facebook

#### NIPS2018
1. Heterogeneous Bitwidth Binarization in Convolutional Neural Networks. **NIPS2018** microsoft
25. **HAQ**: Hardware-Aware automated quantization. **NIPS workshop 2018** mit
35. Scalable methods for 8-bits training of neural networks. **NIPS2018** intel

#### AAAI2018
1. From Hashing to CNNs: training Binary weights vis hashing. **AAAI2018** nlpr

#### Other
1. **Synergy**: Algorithm-hardware co-design for convnet accelerators on embedded FPGAs. **2018** UC Berkeley
22. Efficient Non-uniform quantizer for quantized neural network targeting Re-configurable hardware. **2018**
27. **HALP**: High-Accuracy Low-Precision Training. **2018** stanford
29. **PACT**: parameterized clipping activation for quantized neural networks. **2018** IBM
34. **QUENN**: Quantization engine for low-power neural networks. **CF18ACM**
39. **UNIQ**: Uniform noise injection for non-uniform quantization of neural networks. **2018**
41. Training competitive binary neural networks from scratch. **2018**
42. **A white-paper**: Quantizing deep convolutional networks for efficient inference. **2018** google


### 2015-2016

1.  Deep learning with limited numerical precision. **2015 IBM**
2.  **DoReFa-Net**: Training low bit-width convolutional neural networks with low bit-width gradients. **2016**
4.  **BNN**: Binarized Neural Networks. **NIPS2016**
7.  **TWNs**: Ternary weight networks. **NIPS2016** ucas
3.  **XNOR-Net**: ImageNet Classification using binary convolutional neural networks. **ECCV2016 washington**
6.  Hardware-oriented approximation of convolutional neural networks. **ICLR2016**
8.  Quantized convolutional neural networks for mobile devices. **CVPR2016** nlpr

### 2017
9.  **Flexpoint**: an adaptive numerical format for efficient training of deep neural networks. **2017** intel
10. **INQ**: Incremental network quantization, towards lossless CNNs with low-precision weights. **ICLR2017** intel labs china
11. **TTQ**: Trained ternary quantization. **ICLR2017** stanford
12. **WRPN**: wide reduced-precision networks. **2017** Accelerator Architecture Lab, Intel
14. **HWGQ**: Deep Learning with Low Precision by Half-wave Gaussian Quantization. **CVPR2017**
13. A **Survey** of Model Compression and Acceleration for Deep Neural Networks. **2017**
14. **LP-SGD** Understanding and Optimizing Asynchronous Low-Precision Stochastic Gradient Descent **ISCA2017**
15. How to Train a Compact Binary Neural Network with High Accuracy? **NLPR MicroSoft**

## Other
1.  Fixed point quantization of deep convolutional networks. **2016**
40. Training a binary weight object detector by knowledge transfer for autonomous driving. **2018**
48. Low-bit Quantization of Neural Networks for Efﬁcient Inference. **2019** huawei

---
[top](#2020)

