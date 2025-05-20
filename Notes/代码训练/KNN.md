### 心得体悟

在计算欧氏距离的时候 可以先将向量压扁（flatted） 这样更通用
![[Pasted image 20250304145046.png]]

`torch.manual_seed(0) ` 设置CPU随机种子 设定后 随机函数出来的值都相同

`values, indices = torch.topk(dists, k, largest = False, dim = 0)` 可以取出前k小的数值

#### 交叉验证

- 关键在于将训练数据集分成N份，并选取其中一份为验证集
  选取的验证集range 1-N 并求出平均的acc

