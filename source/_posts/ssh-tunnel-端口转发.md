---
title: ssh tunnel 端口转发
date: 2018-08-09 10:14:55
tags:
	- ssh tunnel
	- sublime
	- sftp
	- jupyter-notebook
---

# Problem description

- **A** PC
- **B** 有公网IP的服务器或者工作站
- **C** 和**B**在同一个局域网的机器
- **D** 任意一台能联网的机器

![img](ssh_tunnel.png)

我们想通过PC来连接**B**, **C**, **D**, 从而方便的来远程同步代码，和开启jupyter-notebook服务等。

# ssh command
主要用到了下边这条命令：

```bash
ssh -N -f -L <port2>:<ip1>:<port1> <username>@<ip>
```

- **N** 在后台运行
- **f** Fork into background after authentication. 后台认证用户密码，通常和-N连用，不用登录到远程主机。
- **L** 本地起端口映射到其他机器

# Example

## Access server C on PC A
Run on PC A:
```bash
ssh -N -f -L <A.custom.port>:<C.local.ip>:<C.custom.port> <username>@<B.public.ip>
```

## Access server D on PC A
Run on server D:
```bash
ssh -CfnNt -R <B.custom.port>:localhost:<D.custom.port> <username>@<B.public.ip>
```
Run on PC A:
```bash
ssh -N -f -L <A.custom.port>:localhost:<B.custom.port> <username>@<B.public.ip>
```

## A直接ssh登陆到C
Add the following code to `~/.ssh/config`
```
Host server
User C.username
Port 22
HostName <C.local.ip>
ProxyCommand ssh B.username@B.public.ip nc %h %p 2> /dev/null
```

Then, we can connect to server C directly.
```
ssh server
```

# Reference
[梦溪博客](http://blog.creke.net/722.html)
