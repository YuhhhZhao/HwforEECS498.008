![[Pasted image 20250302135118.png]]
- 一维向量的shape是(5,),而一维矩阵的shape是(5，1)
- `np.arange([起点]，终点，[步长])` 生成一个列表 ，从起点到终点
### Array math

- `np.add()` 相加
- `np.subtract() `相减
- `np.multiply()` 相乘 非矩阵乘法
- `np.divide()` 相除 非矩阵除法
- `np.sqrt()` 每个元素作开方
- `np.dot()` 矩阵乘法 等同于逻辑运算符 `@`
- `np.sum() `
  区分行和列 不加axis为全加
![[Pasted image 20250302141031.png]]
- `x.T` 转置
- `np.empty_like(x)` 创建一个和x相同行数列数的空矩阵
- `np.tile(x,2,3)` 将x矩阵（向量）沿横方向复制三倍 纵方向复制两倍
### Matplotlib
### Images

