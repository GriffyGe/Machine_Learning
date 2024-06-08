### **Table of Contents**

1. Pytorch环境配置
2. 

## 1. Pytorch环境配置

- Step1: Anaconda安装
- Step2: 检查显卡驱动是否正确安装

  显卡 对于pytorch使用没有影响 -> 主要起到**训练加速**的作用

  显卡配置：驱动 + CUDA Toolkit (跟随pytorch一键安装)

- Step3: 创建pytorch环境

  不同的project可能需要不同的pytorch版本，因此需要建立不同的环境以满足。

  ```
  #Create the environment(python=xx可以指定该环境下的python版本)
  conda create -n env_name python=xx
  #Activate the environment
  conda activate env_name
  #Deactivate the environment

  #
  ```

- 
