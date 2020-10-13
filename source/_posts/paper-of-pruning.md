---
title: paper of pruning
tags:
  - paper
  - 'compression, pruning, sparsity'
date: 2020-10-10 17:23:20
---



---
### ADMM
1. **ADMM-Pruning** A Systematic DNN Weight Pruning Framework using Alternating Direction Method of Multipliers. **2018 Yanzi Wang** 使用ADMM来进行pruning，效果很好。
2. **SS-Auto**: A Single-Shot, Automatic Structured Weight Pruning Framework of DNNs with Ultra-High Efficiency. **2020**
3. **ADMM-NN**: An Algorithm-Hardware Co-Design Framework of DNNs Using Alternating Direction Method of Multipliers
---
1. **LookAhead**: a far-sighted alternative of magnitude-based pruning. [PyToch](https://github.com/alinlab/lookahead_pruning) **ICLR2020**
2. Weight pruning via adaptive sparsity loss. $L(\{W_i\}, \{b_i\}) + \gamma L_s(\{b_i\})$， 前半部分，来让权重更新，并尽量让稀疏度降低；后半部分，尽量让稀疏度提高；通过两者的组合，来形成一个自适应的调节稀疏度的过程。[PyTorch](https://github.com/georgeretsi/SparsityLoss)
---
### Other
1. **DeepTwist** : learning model compression via occasional weight distortion. **ICLR 2019 reject**现在看起来还有点迷惑。与pruning, quantization, svd结合，优化compression的。只需要增加一个超参数，weight distortion 就是 weight-noise-injection