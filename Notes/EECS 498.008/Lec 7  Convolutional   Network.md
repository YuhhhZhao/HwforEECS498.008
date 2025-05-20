![[Pasted image 20250317133422.png]]
利用一个过滤层 将原始数据分成多个过滤器的形状，然后分别进行计算，得到新的层
![[Pasted image 20250317133709.png]]
四维 可以看作是多个三维
![[Pasted image 20250317134037.png]]
**加入非线性函数  ReLU等**

卷积网络不仅仅是学习一个数据 而是学习一组数据 

![[Pasted image 20250317134904.png]]
添加填充(padding)来让输出和输入的维数相同

#### stride（幅度）
![[Pasted image 20250317135537.png]]
添加步幅 来让输入维度快速下降

#### Pooling
kernel size 卷积核 代表了每次处理的单元大小
Max pooling ; average pooling 

![[Pasted image 20250317141146.png]]
### Batch Normalization
![[Pasted image 20250317141352.png]]
使用一层，来代表数据的标准化