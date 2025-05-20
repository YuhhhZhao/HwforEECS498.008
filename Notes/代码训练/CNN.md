### 反向传播
![[Pasted image 20250319204427.png]]
其中L代表损失函数 F代表过滤器 X代表输入函数 O代表输出
**W规模的设定**
![[Pasted image 20250323210242.png]]

#### Kaiming Initialization
Kaiming初始化背后的动机是解决深度神经网络训练期间可能出现的梯度消失或爆炸问题。在深度网络中，尤其是使用整流线性单元（ReLU）激活函数的深度网络中，传统的权重初始化方法（例如随机正态或Xavier初始化）可能会导致梯度在反向传播期间在各层中传播时消失或爆炸。

### 重要知识点！！
![[Pasted image 20250329154343.png]]
permute可以对张量进行重排

### batchnorm
使用后可以更少的依赖于learning_rate的值