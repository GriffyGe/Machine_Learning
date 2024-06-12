# Pytorch学习Day4-Tensorboard入门

```
from torch.utils.tensorboard import SummaryWriter

# 1. 创建一个类
writer = SummaryWriter(log_dir="logs") #log_dir = Save directory location.

# 2.如何使用add_scalar
#Tensorboard installation: conda install conda-forge::tensorboard
#y = x
for i in range(100):
    writer.add_scalar(tag="y=2x",
                      scalar_value=3*i,
                      global_step=i)
writer.close()

# 3. 如何打开eventfile
# Terminal输入：
#tensorboard --logdir=logs
#默认端口为 6006，为了避免和别人的端口一致产生冲突，可以指定端口: --port
#tensorboard --logdir=logs --port=6007
```