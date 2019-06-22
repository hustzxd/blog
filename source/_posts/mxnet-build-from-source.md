---
title: mxnet-build-from-source
date: 2019-01-08 18:01:38
tags:
	- MXNet
	- GLUON
---

# Build MXNet from Source

## Clone the MXNet Project
```bash
git clone --recursive https://github.com/apache/incubator-mxnet mxnet
cd mxnet
```

## Download mklcudnn
```bash
cd 3rdparty/mkldnn/external
wget https://github.com/intel/mkl-dnn/releases/download/v0.17.2/mklml_lnx_2019.0.1.20180928.tgz
```

## Build
```bash
cd docs/install 
./install_mxnet_ubuntu_python.sh
```

## install python
```bash
cd python
pip install -e .
```

## Add operator in backend

### Why not add custom operator using `PythonOp` interface.
```python
class NDArrayOp(PythonOp):
    """Base class for numpy operators. numpy operators allow parts
    of computation in symbolic graph to be writen in numpy. This feature
    is intended for quickly hacking out a solution for non performance
    critical parts. Please consider write a c++ implementation if it becomes
    a bottleneck.
    Note that if your operator contains internal states (like arrays),
    it cannot be used for multi-gpu training.
    """
```

https://cwiki.apache.org/confluence/display/MXNET/CLion+setup+for+MXNet+development+on+Mac

## References
[install-mxnet-for-python](https://mxnet.incubator.apache.org/install/ubuntu_setup.html#install-mxnet-for-python)
[add op in backend](https://mxnet.incubator.apache.org/faq/add_op_in_backend.html)