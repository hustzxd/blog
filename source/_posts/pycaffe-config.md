---
title: 'pycaffe config '
date: 2018-08-27 16:03:24
tags:
	- pycaffe
	- caffe
	- opencv
---

# Problem
There is always some trouble when we want use `pycaffe` and `opencv` at the same time :(
```python
import caffe
import cv2
```

# Solution
> We just do not use Anaconda!!!!!

```bash
cd caffe/python
for req in $(cat requirements.txt); do pip install $req; done
pip install opencv-python
```
```python
import os.path as osp
import sys

def add_path(path):
    if path not in sys.path:
        sys.path.insert(0, path)

caffe_path = '/home/zhaoxiandong/caffe'

# Add caffe to PYTHONPATH
caffe_path = osp.join(caffe_path, 'python')
add_path(caffe_path)

import caffe
import cv2
# successful !::::))))
```

# References
https://github.com/NVIDIA/DIGITS/issues/156