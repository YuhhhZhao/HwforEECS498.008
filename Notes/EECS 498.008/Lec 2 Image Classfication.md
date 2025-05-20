
### **Challenges**

- 语义鸿沟 `Sematic gap` 
- 视角 `Viewpoint Variation`
- 类内变异 `Intraclass Variation`
- 细粒度 `fine-grained`
- 背景干扰 `Background Clutter`
- 光线不同 `Illumination Changes`
- 变形 `Deformation`
- 遮挡 `Occlusion`

CiFar 、Imagenet  、 Omniglot(训练数据少)

距离度量（Distance Metric） ：比较图像之间的值

## K - Nearest Neighbor Classifier
 
![[Pasted image 20250303104609.png]]
    ![[Pasted image 20250303104913.png]]
 `更多的邻节点判断会使边界更加光滑`
    ![[Pasted image 20250303104943.png]]
 `更合理的距离公式选择也同样会让边界更加光滑`
	 e.g. 比较研究论文使用  tf-idf similarity 
#### Setting Hyperparameters
   ![[Pasted image 20250303105821.png]]
   训练 - 验证 - 测试
   ![[Pasted image 20250303110044.png]]
    交叉验证


#### problem 
Curse of Dimensionality
#### Convnet feature
