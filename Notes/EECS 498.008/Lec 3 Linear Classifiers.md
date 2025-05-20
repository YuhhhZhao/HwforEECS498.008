
![[Pasted image 20250304195413.png]]

### Neural Network
- 使用损失函数来确定W的取值
	 Cross-Entropy Loss 交叉熵损失函数(Multinomial Logistic Regression)
	 Softmax function
	 使用信息理论中的计算方式来计算损失 
- 添加**正则化项**
	![[Pasted image 20250305154431.png]]
SVM 损失函数的求导
![[Pasted image 20250310120803.png]]

**向量化的重点**： 对向量求偏导的时候 可以得出一个综合的矩阵margin_sum 把需要用于乘法的系数放到这个矩阵当中。