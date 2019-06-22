---
title: install-tensorRT
date: 2018-10-26 15:59:49
tags:
	- cuda
	- nvidia-driver
	- ubuntu
	- tensorRT
---

# Install Driver and CUDA
[install cuda](https://joyeeo.github.io/2018/10/18/install-cuda/)

# Install TensorRT

## Download TensorRT 5.0
[tensorrt download](https://developer.nvidia.com/tensorrt)

Then, I got the following package:
`nv-tensorrt-repo-ubuntu1604-cuda9.0-trt5.0.0.10-rc-20180906_1-1_amd64.deb`

## Install TensorRT 5.0

```bash
sudo dpkg -i nv-tensorrt-repo-ubuntu1604-cuda9.0-trt5.0.0.10-rc-20180906_1-1_amd64.deb
sudo apt-key add /var/nv-tensorrt-repo-cuda9.0-trt5.0.0.10-rc-20180906/7fa2af80.pub  
sudo apt-get update
# Unluckily, I encountered the following problem.
## double free or corruption (fasttop): 0x0000000001368e00 ***
# I solved it by run: sudo apt-get purge libappstream3 
sudo apt-get install tensorrt 
```

## Demo
```bash
cd /usr/src/tensorrt/samples
sudo make -j32
cd ../bin
./samples_mnist
```
![mnist](mnist.png)
## Install PyCUDA
```bash
pip install pycuda
# error
# In file included from src/cpp/cuda.cpp:1:0:
#     src/cpp/cuda.hpp:14:18: fatal error: cuda.h: No such file or directory
#     compilation terminated.
#     error: command 'gcc' failed with exit status 1
export PATH=/usr/local/cuda/bin:$PATH
pip install pycuda
```
### uff custom plugin
```
cd /usr/src/tensorrt/samples/python/uff_custom_plugin
mkdir build && pushd build
cmake ..
make -j8
python2 lenet5.py
python2 mnist_uff_custom_plugin.py
```
