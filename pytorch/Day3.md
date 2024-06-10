# Pytorch学习Day3-

## 学习内容：

1. OpenCV入门
2. Dataset类代码实战 - 读取文件夹中每一个图片的数据


### 1. OpenCV入门

- OpenCV：轻量、高效、开源，最广泛使用的计算机视觉工具
- 最基本使用
```
import cv2

print(cv2.getVersionString())

#图像数据存放在image变量中
image = cv2.imread("opencv_logo.jpg")

#输出图片维度
print(image.shape)
# output: (250, 250, 3)
#250*250:图片像素的横行和纵列
#*3：表示图片的三元色彩色通道
#数字化图片由像素网格构成 -> 所有的图像处理都是对像素进行数学变换

#通过窗口显示图片
cv2.imshow("hi_image", image) #窗口名 -> "hi_image"；变量名 -> image
cv2.waitKey() #窗口停留
```

### 2. Dataset类代码实战 - 读取文件夹中每一个图片的数据

```
from torch.utils.data import Dataset
import cv2
import os

class MyData(Dataset):

    def __init__(self, root_dir, label_dir):
        #self相当于指定了一个类中的全局变量
        self.root_dir = root_dir
        self.label_dir = label_dir
        self.path = os.path.join(self.root_dir, self.label_dir)
        self.image_path = os.listdir(self.path)

    def __getitem__(self, idx):
        img_name = self.image_path[idx]
        img_item_path = os.path.join(self.root_dir, self.label_dir, img_name)
        img = cv2.imread(img_item_path)
        label = self.label_dir
        return img, label

    def __len__(self):
        return len(self.image_path)

root_dir = "hymenoptera_data/hymenoptera_data/train"
ants_label_dir = "ants"
ants_dataset = MyData(root_dir, ants_label_dir)
bees_label_dir = "bees"
bees_dataset = MyData(root_dir, bees_label_dir)

img, label = ants_dataset[0]
img, label = bees_dataset[0]

cv2.imshow("img", img)
cv2.waitKey()

#将上述两个数据集拼接
train_dataset = ants_dataset + bees_dataset
```

