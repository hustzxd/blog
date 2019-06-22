---
title: Ubuntu environment configuration
date: 2019-5-2 19:33:30
tags:
	- cuda
	- nvidia-driver
	- ubuntu
---

## Update /etc/apt/source.list
```bash
sudo vim /etc/apt/source.list

# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse

# 预发布软件源，不建议启用
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse
# deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
```


## Base software
```bash
sudo apt-get install vim
sudo apt-get install screen
sudo apt-get install git
sudo apt-get install zsh
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
sudo apt-get install htop
sudo apt-get install graphviz
sudo apt-get install unrar
```

## CUDA9.0
```bash
cd /home/ict/Downloads/cuda9
# nvidia-driver
sudo dpkg -i nvidia-driver-local-repo-ubuntu1604-387.34_1.0-1_amd64.deb
sudo apt-get update
sudo apt-get install cuda-drivers
sudo reboot
# cuda9.0
cd /home/ict/Downloads/cuda9
sudo dpkg -i cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64-deb
sudo apt-get update
sudo apt-get install cuda
# cudnn
sudo dpkg -i libcudnn7-dev_7.1.3.16-1+cuda9.0_amd64.deb
sudo dpkg -i libcudnn7_7.1.3.16-1+cuda9.0_amd64.deb
```

## Remove CUDA
```bash
sudo apt-get --purge remove "nvidia-*"
```

## Using the specified GPU
```bash
CUDA_VISIBLE_DEVICES="0,1"
```


