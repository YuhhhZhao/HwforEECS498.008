### 引用模块并检查版本
```python
import torch
print(torch.__version__)
```
## Tensor basics

**空张量** ： `x = torch.tensor([])`
     此时 x.shape = (0,) 

```python
# Create a rank 1 tensor from a Python list
a = torch.tensor([1, 2, 3])
print('Here is a:')
print(a)
print('type(a): ', type(a))  查看类型
print('rank of a: ', a.dim()) 查看维度
print('a.shape: ', a.shape) 查看长度
# Access elements using square brackets
print()
print('a[0]: ', a[0])
print('type(a[0]): ', type(a[0]))
print('type(a[0].item()): ', type(a[0].item())) 显示具体数值
# Mutate elements using square brackets
```
```python
# Create a two-dimensional tensor
b = torch.tensor([[1, 2, 3], [4, 5, 5]])
print('Here is b:')
print(b)
print('rank of b:', b.dim())
print('b.shape: ', b.shape)
# Access elements from a multidimensional tensor
print()
print('b[0, 1]:', b[0, 1])
print('b[1, 2]:', b[1, 2])
# Mutate elements of a multidimensional tensor
b[1, 1] = 100
print()
print('b after mutating:')
print(b)
```

**tensor的索引**  `b[0,1]` 代表第0行第1列的元素
**tensor的shape** `x.shape[i]` 指的是x多维度中的第i维度的值 
     并且 `type(x.shape)` 是torch.size
 
- **torch.zeros** : Creates a tensor of all zeros ==生成默认为float类型==
- **torch.ones** : Creates a tensor of all ones
- **torch.rand** : Creates a tensor with uniform random numbers
- **torch.eye** : 单位矩阵
- **torch.full** : 指定数的满矩阵 `x = torch.full((M,N),3.14)`
**Datatypes**
	混合取浮点型 
	`y0 = torch.tensor([1, 2], dtype=torch.float32)` 强制转换
```python
x1 = x0.float()  # Cast to 32-bit float
x2 = x0.double() # Cast to 64-bit float
x3 = x0.long() # Cast to 64-bit int
x3 = x0.to(torch.float32) # Alternate way to cast to 32-bit float
x4 = x0.to(torch.float64) # Alternate way to cast to 64-bit float
```
```python
x0 = torch.eye(3, dtype=torch.float64)  # Shape (3, 3), dtype torch.float64

x1 = torch.zeros_like(x0)               # Shape (3, 3), dtype torch.float64

x2 = x0.new_zeros(4, 5)                 # Shape (4, 5), dtype torch.float64

x3 = torch.ones(6, 7).to(x0)            # Shape (6, 7), dtype torch.float64)
```
- `zeros_like(x0)` 意味着和x0同样规模、同样数据类型的零矩阵
- `x0.new_zeros(m,n)` 意味着m、n大小的、和x0同样数据类型的零矩阵
- `torch.ones(m,n).to(x0)` 意味着m、n大小，和x0同样数据类型的全1矩阵
- `x = torch.arange(start,stop,step,dtype = None)` 输出序列
### **tensor切片**
    与list用法一致
    一些特殊用法：
```python
# [[ 1  2  3  4]
#  [ 5  6  7  8]
#  [ 9 10 11 12]]
# Get row 1, and all columns.
print('\nSingle row:')
print(a[1, :])
print(a[1])  # Gives the same result; we can omit : for trailing dimensions

print('\nSingle column:')
print(a[:, 1])

print('\nFirst two rows, last two columns:')
print(a[:2, -3:])
```

	 区分下面的代码
	row_r1 = a[1, :]   
	row_r2 = a[1:2, :] 
	 前者为[] 后者为[[]]
****
==可使用.clone() 来避免切片对原tensor的修改==

### **张量索引(indexing)**

索引类型只能为int、bool等 不能为float
可令`idx = torch.tensor([3,2,1,0])` 或者
`idx = [3,2,1,0]` 来实现某一tensor的倒置(以及更多操作)

![[Pasted image 20250303143209.png]]
即`a[idx0,idx1]` 取得是`a[idx0[0],idx1[0]] a[idx0[1],idx1[1]]` 这样的一阶tensor


### **浅拷贝和深拷贝**

直接通过索引来进行切片的一般都是浅拷贝 拷贝后修改切片矩阵会对原矩阵进行修改，除非使用.clone来避免这一操作；如果使用idx = \[1,2,3] 这种索引切片的话，则生成的是对原矩阵的副本 因此不会对原矩阵进行修改


### **布尔类型的使用**
`a = torch.tensor([[1,2], [3, 4], [5, 6]])`
`a[a>3]` 这个会列出所有>3的元素 并组成一个列表
`a>3` 这个会输出每一个元素与3比较的布尔值
	`a[a<=3] = 0` 让元素≤3的全部为0

### **view()**

改变矩阵的维度以及各维度的元素个数
`x0 = torch.tensor([[1, 2, 3, 4], [5, 6, 7, 8]])`
`x1 = x0.view(8)` 变成(8,)
`x2 = x1.view(1, 8)` 变成(1,8)
`x4 = x1.view(2, 2, 2)` 变成(2,2,2)

`x.view(-1)` 意味着展平为一阶元组
`x.view(1,-1)` 意味着展平为一阶矩阵
-1可以理解为所有元素个数除以其他维度确定的值

view() 是一种浅拷贝 会影响原张量的值

**torch.transpose**
	x1 = x0.transpose(1, 2) 让x0索引为1和2的维度值交换
**torch.permute**
	x2 = x0.permute(1, 2, 0) 维度值索引顺序变为 1 , 2 , 0 

### **计算**

```python
torch.add(x, y)
torch.sub(x, y)
torch.mul(x, y)
torch.div(x, y)
torch.pow(x, y)
torch.sqrt(x) == x.sqrt()
torch.sin(x) == x.sin()
torch.cos(x) == x.cos()
这些仅对x元素进行一对一的运算
```

```python
x = torch.tensor([[1, 2, 3],
                  [4, 5, 6]], dtype=torch.float32)
print(torch.sum(x, dim=0)) 削减维度0
```
```python 
x = torch.tensor([[2, 4, 3, 5], [3, 3, 5, 2]], dtype=torch.float32)
col_min_vals, col_min_idxs = x.min(dim=0) 前一个为具体数值 后一个为最小值取到的索引
若取keepdim = True 会让该维度削减为1 而不是 直接消失

```

### **矩阵的拼接**

`torch.stack(tensorA, tensorB, dim = N)` 代表插入在第N个维度之后
`torch.cat()`
### **矩阵运算**

`torch.dot` 向量和向量的内积
`torch.mm` 矩阵和矩阵的乘积
`torch.mv` 矩阵和向量的乘积
`torch.matmul` 
    包含上面两种dot & mm
    若前者为向量后者为矩阵 则向量变成(1,n)的矩阵
    反之，则变为矩阵和向量的简单乘积 输出一维向量
==特殊的矩阵运算（包含输入 三维）==
    `torch.bmm(input, mat2)` input和mat2都为三维张量
    若input（b\*n\*m） 、 mat2 (b\*m\*p) 则out为(b\*n\*p)
### **向量化计算**
显式循环会比torch内部运算要慢很多

### **广播(broadcasting) (减少循环)**

原则：
1. 如果张量的阶不同，则在较低阶数组的形状前面添加 1，直到两个形状的长度相同。
2. 如果两个张量在维度上具有相同的大小，或者其中一个张量在该维度上的大小为 1，则称这两个张量在维度上兼容。
3. 如果张量在所有维度上都兼容，则可以将它们一起广播。
4. 广播后，每个张量的行为就像其形状等于两个输入张量的形状的元素最大值一样。
5. 在任何维度中，如果一个张量的大小为 1，而另一个张量的大小大于 1，则第一个张量的行为就像是沿着该维度复制的

![[Pasted image 20250303173731.png]]
`torch.broadcas_tensors` 可以广播其中一个 或者两个一起
```python
x = torch.tensor([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]])
v = torch.tensor([1, 0, 1])
xx, vv = torch.broadcast_tensors(x, v)
```
![[Pasted image 20250303174239.png]]

一般来说 直接的元素运算(elementwise functions) 可以支持广播（+ - * /） 以及个别非元素运算 比如torch.matmul

### **in-place & Out-of-place**
注意两者区别 `z = x.add(y)` 和`x.add_(y)`
后者等同于 x+=y

### **在GPU上运行**

```python
import torch
if torch.cuda.is_available():
  print('PyTorch can use GPUs!')
else:
  print('PyTorch cannot use GPUs.')
```
.to('cuda') 就可以使用cuda


### **其他有用函数**

- `tensor.chunk(x)` 将tensor分成x份
- `tensor.cat`