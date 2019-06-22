---
title: PyTorch Begin
date: 2018-08-10 17:48:36
tags:
	- PyTorch
---


## Recommand approach for saving model
[Stack overflow](https://stackoverflow.com/questions/42703500/best-way-to-save-a-trained-model-in-pytorch)
- First
```python
# save
torch.save(model.state_dict(), PATH)
# load
model = Model(args)
model.load_state_dict(torch.load(PATH))
```

- Second
```python
# save
torch.save(mode, PATH)
# load
model = torch.load(PATH)
```

### Pytorch DataParallel
[csdn](https://blog.csdn.net/qq_19598705/article/details/80396325)
