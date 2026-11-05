


# NumPy 100 题

本练习集汇集了来自 NumPy 邮件列表、Stack Overflow 和 NumPy 文档的练习题，旨在为新老用户提供便捷的参考，同时为教学提供一套练习材料。

如果你发现错误，或认为某些题目有更好的解法，欢迎在 <https://github.com/rougier/numpy-100> 提交 issue。
本文件由程序自动生成。如需通过程序更新题目、解答或提示，请参阅项目文档。

#### 1. 以 `np` 为别名导入 NumPy 包 (★☆☆)
`提示： import … as`

```python
import numpy as np
```
#### 2. 打印 NumPy 的版本和配置信息 (★☆☆)
`提示： np.__version__, np.show_config)`

```python
print(np.__version__)
np.show_config()
```
#### 3. 创建一个长度为 10 的全零向量 (★☆☆)
`提示： np.zeros`

```python
Z = np.zeros(10)
print(Z)
```
#### 4. 如何计算任意数组占用的内存大小？ (★☆☆)
`提示： size, itemsize`

```python
Z = np.zeros((10,10))
print("%d bytes" % (Z.size * Z.itemsize))

# 更简单的方法
print("%d bytes" % Z.nbytes)
```
#### 5. 如何在命令行中查看 NumPy 的 add 函数文档？ (★☆☆)
`提示： np.info`

```python
!python -c "import numpy; numpy.info(numpy.add)"
```
#### 6. 创建一个长度为 10 的向量，除第 5 个元素为 1 外，其余元素均为 0 (★☆☆)
`提示： array[4]`

```python
Z = np.zeros(10)
Z[4] = 1
print(Z)
```
#### 7. 创建一个值从 10 到 49 的向量 (★☆☆)
`提示： arange`

```python
Z = np.arange(10,50)
print(Z)
```
#### 8. 反转一个向量（使第一个元素变为最后一个） (★☆☆)
`提示： array[::-1]`

```python
Z = np.arange(50)
Z = Z[::-1]
print(Z)
```
#### 9. 创建一个值从 0 到 8 的 3x3 矩阵 (★☆☆)
`提示： reshape`

```python
Z = np.arange(9).reshape(3, 3)
print(Z)
```
#### 10. 找出 [1,2,0,0,4,0] 中非零元素的索引 (★☆☆)
`提示： np.nonzero`

```python
nz = np.nonzero([1,2,0,0,4,0])
print(nz)
```
#### 11. 创建一个 3x3 单位矩阵 (★☆☆)
`提示： np.eye`

```python
Z = np.eye(3)
print(Z)
```
#### 12. 创建一个包含随机值的 3x3x3 数组 (★☆☆)
`提示： np.random.random`

```python
Z = np.random.random((3,3,3))
print(Z)
```
#### 13. 创建一个包含随机值的 10x10 数组，并找出其中的最小值和最大值 (★☆☆)
`提示： min, max`

```python
Z = np.random.random((10,10))
Zmin, Zmax = Z.min(), Z.max()
print(Zmin, Zmax)
```
#### 14. 创建一个长度为 30 的随机向量，并计算其均值 (★☆☆)
`提示： mean`

```python
Z = np.random.random(30)
m = Z.mean()
print(m)
```
#### 15. 创建一个边界为 1、内部为 0 的二维数组 (★☆☆)
`提示： array[1:-1, 1:-1]`

```python
Z = np.ones((10,10))
Z[1:-1,1:-1] = 0
print(Z)
```
#### 16. 如何在现有数组周围添加一圈用 0 填充的边界？ (★☆☆)
`提示： np.pad`

```python
Z = np.ones((5,5))
Z = np.pad(Z, pad_width=1, mode='constant', constant_values=0)
print(Z)

# 以下并非本题解答，但值得了解：使用花式索引进行原地修改
Z[:, [0, -1]] = 0
Z[[0, -1], :] = 0
print(Z)
```
#### 17. 下列表达式的结果是什么？ (★☆☆)
```python
0 * np.nan
np.nan == np.nan
np.inf > np.nan
np.nan - np.nan
np.nan in set([np.nan])
0.3 == 3 * 0.1
```
`提示： NaN = 非数值，inf = 无穷大`

```python
print(0 * np.nan)
print(np.nan == np.nan)
print(np.inf > np.nan)
print(np.nan - np.nan)
print(np.nan in set([np.nan]))
print(0.3 == 3 * 0.1)
```
#### 18. 创建一个 5x5 矩阵，在主对角线正下方的对角线上依次填入 1、2、3、4 (★☆☆)
`提示： np.diag`

```python
Z = np.diag(1+np.arange(4),k=-1)
print(Z)
```
#### 19. 创建一个 8x8 矩阵，并将其填充为棋盘图案 (★☆☆)
`提示： array[::2]`

```python
Z = np.zeros((8,8),dtype=int)
Z[1::2,::2] = 1
Z[::2,1::2] = 1
print(Z)
```
#### 20. 对于一个形状为 (6,7,8) 的数组，第 100 个元素的索引 (x,y,z) 是什么？ (★☆☆)
`提示： np.unravel_index`

```python
print(np.unravel_index(99,(6,7,8)))
```
#### 21. 使用 tile 函数创建一个棋盘图案的 8x8 矩阵 (★☆☆)
`提示： np.tile`

```python
Z = np.tile( np.array([[0,1],[1,0]]), (4,4))
print(Z)
```
#### 22. 对一个 5x5 随机矩阵进行标准化 (★☆☆)
`提示： (x -mean)/std`

```python
Z = np.random.random((5,5))
Z = (Z - np.mean (Z)) / (np.std (Z))
print(Z)
```
#### 23. 创建一个自定义 dtype，用四个无符号字节描述颜色（RGBA） (★☆☆)
`提示： np.dtype`

```python
color = np.dtype([("r", np.ubyte),
                  ("g", np.ubyte),
                  ("b", np.ubyte),
                  ("a", np.ubyte)])
```
#### 24. 将一个 5x3 矩阵与一个 3x2 矩阵相乘（矩阵乘法） (★☆☆)
`提示：`

```python
Z = np.matmul(np.ones((5, 3)), np.ones((3, 2)))
print(Z)

# 另一种解法，适用于 Python 3.5 及以上版本
Z = np.ones((5,3)) @ np.ones((3,2))
print(Z)
```
#### 25. 给定一个一维数组，将其中大于 3 且小于 8 的元素原地取负 (★☆☆)
`提示： >, <`

```python
# 作者： Evgeni Burovski

Z = np.arange(11)
Z[(3 < Z) & (Z < 8)] *= -1
print(Z)
```
#### 26. 下列脚本的输出是什么？ (★☆☆)
```python
# 作者： Jake VanderPlas

print(sum(range(5),-1))
from numpy import *
print(sum(range(5),-1))
```
`提示： np.sum`

```python
# 作者： Jake VanderPlas

print(sum(range(5),-1))
from numpy import *
print(sum(range(5),-1))
```
#### 27. 对于一个整数向量 Z，下列表达式中哪些是合法的？ (★☆☆)
```python
Z**Z
2 << Z >> 2
Z <- Z
1j*Z
Z/1/1
Z<Z>Z
```
`暂无提示。`

```python
Z**Z
2 << Z >> 2
Z <- Z
1j*Z
Z/1/1
Z<Z>Z
```
#### 28. 下列表达式的结果是什么？ (★☆☆)
```python
np.array(0) / np.array(0)
np.array(0) // np.array(0)
np.array([np.nan]).astype(int).astype(float)
```
`暂无提示。`

```python
print(np.array(0) / np.array(0))
print(np.array(0) // np.array(0))
print(np.array([np.nan]).astype(int).astype(float))
```
#### 29. 如何将浮点数数组中的元素沿远离零的方向取整？ (★☆☆)
`提示： np.uniform, np.copysign, np.ceil, np.abs, np.where`

```python
# 作者： Charles R Harris

Z = np.random.uniform(-10,+10,10)
print(np.copysign(np.ceil(np.abs(Z)), Z))

# 可读性更好，但效率较低
print(np.where(Z>0, np.ceil(Z), np.floor(Z)))
```
#### 30. 如何找出两个数组中的共同值？ (★☆☆)
`提示： np.intersect1d`

```python
Z1 = np.random.randint(0,10,10)
Z2 = np.random.randint(0,10,10)
print(np.intersect1d(Z1,Z2))
```
#### 31. 如何忽略 NumPy 的所有警告（不推荐）？ (★☆☆)
`提示： np.seterr, np.errstate`

```python
# 开启忽略所有浮点错误的模式
defaults = np.seterr(all="ignore")
Z = np.ones(1) / 0

# 恢复原有的错误处理设置
_ = np.seterr(**defaults)

# 使用上下文管理器实现相同效果
with np.errstate(all="ignore"):
    np.arange(3) / 0
```
#### 32. 下列表达式的结果是否为真？ (★☆☆)
```python
np.sqrt(-1) == np.emath.sqrt(-1)
```
`提示：虚数`

```python
np.sqrt(-1) == np.emath.sqrt(-1)
```
#### 33. 如何获取昨天、今天和明天的日期？ (★☆☆)
`提示： np.datetime64, np.timedelta64`

```python
yesterday = np.datetime64('today') - np.timedelta64(1, 'D')
today     = np.datetime64('today')
tomorrow  = np.datetime64('today') + np.timedelta64(1, 'D')
```
#### 34. 如何获取 2016 年 7 月的所有日期？ (★★☆)
`提示： np.arange(dtype=datetime64['D'])`

```python
Z = np.arange('2016-07', '2016-08', dtype='datetime64[D]')
print(Z)
```
#### 35. 如何原地计算 ((A+B)*(-A/2))（不创建副本）？ (★★☆)
`提示： np.add(out=), np.negative(out=), np.multiply(out=), np.divide(out=)`

```python
A = np.ones(3)*1
B = np.ones(3)*2
np.add(A,B,out=B)
np.divide(A,2,out=A)
np.negative(A,out=A)
np.multiply(A,B,out=A)
```
#### 36. 使用 4 种不同的方法提取一个随机正数数组的整数部分 (★★☆)
`提示： %, np.floor, astype, np.trunc`

```python
Z = np.random.uniform(0,10,10)

print(Z - Z%1)
print(Z // 1)
print(np.floor(Z))
print(Z.astype(int))
print(np.trunc(Z))
```
#### 37. 创建一个 5x5 矩阵，使每一行的值均从 0 到 4 (★★☆)
`提示： np.arange`

```python
Z = np.zeros((5,5))
Z += np.arange(5)
print(Z)

# 不使用广播
Z = np.tile(np.arange(0, 5), (5,1))
print(Z)
```
#### 38. 使用一个生成 10 个整数的生成器函数来构建数组 (★☆☆)
`提示： np.fromiter`

```python
def generate():
    for x in range(10):
        yield x
Z = np.fromiter(generate(),dtype=float,count=-1)
print(Z)
```
#### 39. 创建一个长度为 10、值介于 0 和 1 之间的向量，不包含两个端点 (★★☆)
`提示： np.linspace`

```python
Z = np.linspace(0,1,11,endpoint=False)[1:]
print(Z)
```
#### 40. 创建一个长度为 10 的随机向量，并对其排序 (★★☆)
`提示： sort`

```python
Z = np.random.random(10)
Z.sort()
print(Z)
```
#### 41. 如何以比 np.sum 更快的方式对小数组求和？ (★★☆)
`提示： np.add.reduce`

```python
# 作者： Evgeni Burovski

Z = np.arange(10)
np.add.reduce(Z)
```
#### 42. 给定两个随机数组 A 和 B，检查它们是否相等 (★★☆)
`提示： np.allclose, np.array_equal`

```python
A = np.random.randint(0,2,5)
B = np.random.randint(0,2,5)

# 假设数组形状相同，并允许数值比较存在一定误差
equal = np.allclose(A,B)
print(equal)

# 同时检查形状和元素值，不允许误差（值必须完全相等）
equal = np.array_equal(A,B)
print(equal)
```
#### 43. 将一个数组设为不可修改（只读） (★★☆)
`提示： flags.writeable`

```python
Z = np.zeros(10)
Z.flags.writeable = False
Z[0] = 1
```
#### 44. 给定一个表示笛卡尔坐标的随机 10x2 矩阵，将其转换为极坐标 (★★☆)
`提示： np.sqrt, np.arctan2`

```python
Z = np.random.random((10,2))
X,Y = Z[:,0], Z[:,1]
R = np.sqrt(X**2+Y**2)
T = np.arctan2(Y,X)
print(R)
print(T)
```
#### 45. 创建一个长度为 10 的随机向量，并将最大值替换为 0 (★★☆)
`提示： argmax`

```python
Z = np.random.random(10)
Z[Z.argmax()] = 0
print(Z)
```
#### 46. 创建一个结构化数组，其 `x` 和 `y` 坐标覆盖 [0,1]x[0,1] 区域 (★★☆)
`提示： np.meshgrid`

```python
Z = np.zeros((5,5), [('x',float),('y',float)])
Z['x'], Z['y'] = np.meshgrid(np.linspace(0,1,5),
                             np.linspace(0,1,5))
print(Z)
```
#### 47. 给定两个数组 X 和 Y，构造柯西矩阵 C（Cij =1/(xi - yj)） (★★☆)
`提示： np.subtract.outer`

```python
# 作者： Evgeni Burovski

X = np.arange(8)
Y = X + 0.5
C = 1.0 / np.subtract.outer(X, Y)
print(np.linalg.det(C))
```
#### 48. 打印 NumPy 各种标量类型可表示的最小值和最大值 (★★☆)
`提示： np.iinfo, np.finfo, eps`

```python
for dtype in [np.int8, np.int32, np.int64]:
   print(np.iinfo(dtype).min)
   print(np.iinfo(dtype).max)
for dtype in [np.float32, np.float64]:
   print(np.finfo(dtype).min)
   print(np.finfo(dtype).max)
   print(np.finfo(dtype).eps)
```
#### 49. 如何打印数组中的所有值？ (★★☆)
`提示： np.set_printoptions`

```python
np.set_printoptions(threshold=float("inf"))
Z = np.zeros((40,40))
print(Z)
```
#### 50. 如何在向量中找出最接近给定标量的值？ (★★☆)
`提示： argmin`

```python
Z = np.arange(100)
v = np.random.uniform(0,100)
index = (np.abs(Z-v)).argmin()
print(Z[index])
```
#### 51. 创建一个表示位置 (x,y) 和颜色 (r,g,b) 的结构化数组 (★★☆)
`提示： dtype`

```python
Z = np.zeros(10, [ ('position', [ ('x', float),
                                  ('y', float)]),
                   ('color',    [ ('r', float),
                                  ('g', float),
                                  ('b', float)])])
print(Z)
```
#### 52. 给定一个形状为 (100,2)、表示坐标的随机数组，计算各点之间的两两距离 (★★☆)
`提示： np.atleast_2d, T, np.sqrt`

```python
Z = np.random.random((100,2))
X,Y = np.atleast_2d(Z[:,0], Z[:,1])
D = np.sqrt( (X-X.T)**2 + (Y-Y.T)**2)
print(D)

# 使用 SciPy 可以快得多
import scipy
# 感谢 Gavin Heverly-Coulson (#issue 1)
import scipy.spatial

Z = np.random.random((100,2))
D = scipy.spatial.distance.cdist(Z,Z)
print(D)
```
#### 53. 如何将一个 32 位浮点数数组原地转换为 32 位整数数组？
`提示：view 和 [:] =`

```python
# 感谢 Vikas (https://stackoverflow.com/a/10622758/5989906)
# 以及 unutbu (https://stackoverflow.com/a/4396247/5989906)
Z = (np.random.rand(10)*100).astype(np.float32)
Y = Z.view(np.int32)
Y[:] = Z
print(Y)
```
#### 54. 如何读取下列文件？ (★★☆)
```
1, 2, 3, 4, 5
6,  ,  , 7, 8
 ,  , 9,10,11
```
`提示： np.genfromtxt`

```python
from io import StringIO

# 模拟文件
s = StringIO('''1, 2, 3, 4, 5

                6,  ,  , 7, 8

                 ,  , 9,10,11
''')
Z = np.genfromtxt(s, delimiter=",", dtype = int, filling_values = 0)
print(Z)
```
#### 55. 对于 NumPy 数组，什么方法相当于 enumerate？ (★★☆)
`提示： np.ndenumerate, np.ndindex`

```python
Z = np.arange(9).reshape(3,3)
for index, value in np.ndenumerate(Z):
    print(index, value)
for index in np.ndindex(Z.shape):
    print(index, Z[index])
```
#### 56. 生成一个通用的二维类高斯数组 (★★☆)
`提示： np.meshgrid, np.exp`

```python
X, Y = np.meshgrid(np.linspace(-1, 1, 10), np.linspace(-1, 1, 10))
sigma, mu = 1.0, 0.0
G = np.exp(-((X - mu) ** 2 + (Y - mu) ** 2) / (2.0 * sigma**2))
print(G)

# 另一种解法，利用二维高斯函数的可分离性
# 作者： Nin17
x = np.linspace(-1, 1, 10)
y = np.linspace(-1, 1, 10)
gx = np.exp(-((x - mu) ** 2 / (2.0 * sigma**2)))
gy = np.exp(-((y - mu) ** 2 / (2.0 * sigma**2)))
G = gy[:, None] * gx[None, :]
print(G)
```
#### 57. 如何在二维数组中随机放置 p 个元素？ (★★☆)
`提示： np.put, np.random.choice`

```python
# 作者： Divakar

n = 10
p = 3
Z = np.zeros((n,n))
np.put(Z, np.random.choice(range(n*n), p, replace=False),1)
print(Z)
```
#### 58. 将矩阵每一行的元素减去该行的均值 (★★☆)
`提示： mean(axis=,keepdims=)`

```python
# 作者： Warren Weckesser

X = np.random.rand(5, 10)

# 较新版本的 NumPy
Y = X - X.mean(axis=1, keepdims=True)

# 较旧版本的 NumPy
Y = X - X.mean(axis=1).reshape(-1, 1)

print(Y)
```
#### 59. 如何按第 n 列对数组进行排序？ (★★☆)
`提示： argsort`

```python
# 作者： Steve Tjoa

Z = np.random.randint(0,10,(3,3))
print(Z)
print(Z[Z[:,1].argsort()])
```
#### 60. 如何判断给定的二维数组中是否存在空值列？ (★★☆)
`提示： any, ~`

```python
# 作者： Warren Weckesser

# 空值：0
Z = np.random.randint(0,3,(3,10))
print((~Z.any(axis=0)).any())

# 空值：np.nan
Z=np.array([
    [0,1,np.nan],
    [1,2,np.nan],
    [4,5,np.nan]
])
print(np.isnan(Z).all(axis=0))
```
#### 61. 在数组中找出最接近给定值的值 (★★☆)
`提示： np.abs, argmin, flat`

```python
Z = np.random.uniform(0,1,10)
z = 0.5
m = Z.flat[np.abs(Z - z).argmin()]
print(m)
```
#### 62. 给定两个形状分别为 (1,3) 和 (3,1) 的数组，如何使用迭代器计算它们的和？ (★★☆)
`提示： np.nditer`

```python
A = np.arange(3).reshape(3,1)
B = np.arange(3).reshape(1,3)
it = np.nditer([A,B,None])
for x,y,z in it: z[...] = x + y
print(it.operands[2])
```
#### 63. 创建一个具有 name 属性的数组类 (★★☆)
`提示：类方法`

```python
class NamedArray(np.ndarray):
    def __new__(cls, array, name="no name"):
        obj = np.asarray(array).view(cls)
        obj.name = name
        return obj
    def __array_finalize__(self, obj):
        if obj is None: return
        self.name = getattr(obj, 'name', "no name")

Z = NamedArray(np.arange(10), "range_10")
print (Z.name)
```
#### 64. 给定一个向量，如何将第二个向量所指定索引处的元素各加 1（注意重复索引）？ (★★★)
`提示： np.bincount | np.add.at`

```python
# 作者： Brett Olsen

Z = np.ones(10)
I = np.random.randint(0,len(Z),20)
Z += np.bincount(I, minlength=len(Z))
print(Z)

# 另一种解法
# 作者： Bartosz Telenczuk
np.add.at(Z, I, 1)
print(Z)
```
#### 65. 如何根据索引列表 (I)，将向量 (X) 中的元素累加到数组 (F) 中？ (★★★)
`提示： np.bincount`

```python
# 作者： Alan G Isaac

X = [1,2,3,4,5,6]
I = [1,3,9,3,4,1]
F = np.bincount(I,X)
print(F)
```
#### 66. 给定一个形状为 (w,h,3)、数据类型为 ubyte 的图像，计算其中不同颜色的数量 (★★☆)
`提示： np.unique`

```python
# 作者： Fisher Wang

w, h = 256, 256
I = np.random.randint(0, 4, (h, w, 3)).astype(np.ubyte)
colors = np.unique(I.reshape(-1, 3), axis=0)
n = len(colors)
print(n)

# 更快的版本
# 作者： Mark Setchell
# https://stackoverflow.com/a/59671950/2836621

w, h = 256, 256
I = np.random.randint(0,4,(h,w,3), dtype=np.uint8)

# 将每个像素视为一个 24 位整数，而非三个 8 位字节
I24 = np.dot(I.astype(np.uint32),[1,256,65536])

# 统计不同颜色的数量
n = len(np.unique(I24))
print(n)
```
#### 67. 给定一个四维数组，如何一次性沿最后两个轴求和？ (★★★)
`提示： sum(axis=(-2,-1))`

```python
A = np.random.randint(0,10,(3,4,3,4))
# 传入轴元组的解法（自 NumPy 1.7.0 引入）
sum = A.sum(axis=(-2,-1))
print(sum)
# 将最后两个维度展平为一个维度的解法
# （适用于 axis 参数不接受元组的函数）
sum = A.reshape(A.shape[:-2] + (-1,)).sum(axis=-1)
print(sum)
```
#### 68. 给定一个一维向量 D，以及一个长度相同、表示各元素所属子集索引的向量 S，如何计算 D 中各子集的均值？ (★★★)
`提示： np.bincount`

```python
# 作者： Jaime Fernández del Río

D = np.random.uniform(0,1,100)
S = np.random.randint(0,10,100)
D_sums = np.bincount(S, weights=D)
D_counts = np.bincount(S)
D_means = D_sums / D_counts
print(D_means)

# Pandas 解法的代码更直观，可供参考
import pandas as pd
print(pd.Series(D).groupby(S).mean())
```
#### 69. 如何获取矩阵乘积的对角线元素？ (★★★)
`提示： np.diag`

```python
# 作者： Mathieu Blondel

A = np.random.uniform(0,1,(5,5))
B = np.random.uniform(0,1,(5,5))

# 较慢的版本
np.diag(np.dot(A, B))

# 较快的版本
np.sum(A * B.T, axis=1)

# 更快的版本
np.einsum("ij,ji->i", A, B)
```
#### 70. 给定向量 [1, 2, 3, 4, 5]，如何构建一个新向量，在每两个相邻值之间插入 3 个连续的零？ (★★★)
`提示： array[::4]`

```python
# 作者： Warren Weckesser

Z = np.array([1,2,3,4,5])
nz = 3
Z0 = np.zeros(len(Z) + (len(Z)-1)*(nz))
Z0[::nz+1] = Z
print(Z0)
```
#### 71. 给定一个形状为 (5,5,3) 的数组，如何将其与一个形状为 (5,5) 的数组相乘？ (★★★)
`提示： array[:, :, None]`

```python
A = np.ones((5,5,3))
B = 2*np.ones((5,5))
print(A * B[:,:,None])
```
#### 72. 如何交换数组中的两行？ (★★★)
`提示： array[[]] = array[[]]`

```python
# 作者： Eelco Hoogendoorn

A = np.arange(25).reshape(5,5)
A[[0,1]] = A[[1,0]]
print(A)
```
#### 73. 给定 10 个三元组，分别描述 10 个三角形（顶点可以共享），找出构成这些三角形的所有不重复线段 (★★★)
`提示： repeat, np.roll, np.sort, view, np.unique`

```python
# 作者： Nicolas P. Rougier

faces = np.random.randint(0,100,(10,3))
F = np.roll(faces.repeat(2,axis=1),-1,axis=1)
F = F.reshape(len(F)*3,2)
F = np.sort(F,axis=1)
G = F.view( dtype=[('p0',F.dtype),('p1',F.dtype)] )
G = np.unique(G)
print(G)
```
#### 74. 给定一个对应于 bincount 结果的有序数组 C，如何生成数组 A，使得 np.bincount(A) == C？ (★★★)
`提示： np.repeat`

```python
# 作者： Jaime Fernández del Río

C = np.bincount([1,1,2,3,4,4,6])
A = np.repeat(np.arange(len(C)), C)
print(A)
```
#### 75. 如何使用滑动窗口计算数组的移动平均值？ (★★★)
`提示： np.cumsum, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# 作者： Jaime Fernández del Río

def moving_average(a, n=3) :
    ret = np.cumsum(a, dtype=float)
    ret[n:] = ret[n:] - ret[:-n]
    return ret[n - 1:] / n
Z = np.arange(20)
print(moving_average(Z, n=3))

# 作者： Jeff Luo (@Jeff1999)
# 请确保 NumPy 版本 >= 1.20.0

from numpy.lib.stride_tricks import sliding_window_view

Z = np.arange(20)
print(sliding_window_view(Z, window_shape=3).mean(axis=-1))
```
#### 76. 给定一个一维数组 Z，构建一个二维数组，其第一行为 (Z[0],Z[1],Z[2])，后续每一行向后移动一个元素，最后一行为 (Z[-3],Z[-2],Z[-1]) (★★★)
`提示： from numpy.lib import stride_tricks, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# 作者： Joe Kington / Erik Rigtorp
from numpy.lib import stride_tricks

def rolling(a, window):
    shape = (a.size - window + 1, window)
    strides = (a.strides[0], a.strides[0])
    return stride_tricks.as_strided(a, shape=shape, strides=strides)
Z = rolling(np.arange(10), 3)
print(Z)

# 作者： Jeff Luo (@Jeff1999)

Z = np.arange(10)
print(sliding_window_view(Z, window_shape=3))
```
#### 77. 如何原地对布尔值取反，或对浮点数取负？ (★★★)
`提示： np.logical_not, np.negative`

```python
# 作者： Nathaniel J. Smith

Z = np.random.randint(0,2,100)
np.logical_not(Z, out=Z)

Z = np.random.uniform(-1.0,1.0,100)
np.negative(Z, out=Z)
```
#### 78. 给定两组点 P0、P1 来描述二维平面中的直线，以及一个点 p，如何计算 p 到每条直线 i（P0[i],P1[i]）的距离？ (★★★)
`暂无提示。`

```python
P0 = np.random.uniform(-10,10,(10,2))
P1 = np.random.uniform(-10,10,(10,2))
p  = np.random.uniform(-10,10,( 1,2))

def distance_faster(P0,P1,p):
    #作者： Hemanth Pasupuleti
    #参考： https://mathworld.wolfram.com/Point-LineDistance2-Dimensional.html

    v = P1- P0 
    v[:,[0,1]] = v[:,[1,0]]
    v[:,1]*=-1 
    norm = np.linalg.norm(v,axis=1)   
    r = P0 - p
    d = np.abs(np.einsum("ij,ij->i",r,v)) / norm 

    return d

print(distance_faster(P0, P1, p))

##--------------- 或 ---------------##
def distance_slower(P0, P1, p):
    T = P1 - P0
    L = (T**2).sum(axis=1)
    U = -((P0[:,0]-p[...,0])*T[:,0] + (P0[:,1]-p[...,1])*T[:,1]) / L
    U = U.reshape(len(U),1)
    D = P0 + U*T - p
    return np.sqrt((D**2).sum(axis=1))

print(distance_slower(P0, P1, p))
```
#### 79. 给定两组点 P0、P1 来描述二维平面中的直线，以及一组点 P，如何计算每个点 j（P[j]）到每条直线 i（P0[i],P1[i]）的距离？ (★★★)
`暂无提示。`

```python
# 作者： Italmassov Kuanysh

# 基于上一题的距离函数
P0 = np.random.uniform(-10, 10, (10,2))
P1 = np.random.uniform(-10,10,(10,2))
p = np.random.uniform(-10, 10, (10,2))
print(np.array([distance_slower(P0,P1,p_i) for p_i in p]))

# 作者： Yang Wu（广播）
def distance_points_to_lines(p: np.ndarray, p_1: np.ndarray, p_2: np.ndarray) -> np.ndarray:
    x_0, y_0 = p.T  # 形状 -> (n 个点, )
    x_1, y_1 = p_1.T  # 形状 -> (n 条直线, )
    x_2, y_2 = p_2.T  # 形状 -> (n 条直线, )

    # 从 p_1 到 p_2 的位移向量坐标
    dx = x_2 - x_1  # 形状 -> (n 条直线, )
    dy = y_2 - y_1  # 形状 -> (n 条直线, )

    # “叉积”项
    cross_term = x_2 * y_1 - y_2 * x_1  # 形状 -> (n 条直线, )

    # 广播 x_0、y_0（点数, 1）和 dx、dy、cross_term（1, 直线数）->（点数, 直线数）
    numerator = np.abs(
        dy[np.newaxis, :] * x_0[:, np.newaxis]
        - dx[np.newaxis, :] * y_0[:, np.newaxis]
        + cross_term[np.newaxis, :]
    )
    denominator = np.sqrt(dx**2 + dy**2)  # 形状 -> (n 条直线, )

    # 形状（点数, 直线数）/（1, 直线数）->（点数, 直线数）
    return numerator / denominator[np.newaxis, :]

distance_points_to_lines(p, P0, P1)
```
#### 80. 给定任意数组，编写一个函数，以指定元素为中心提取固定形状的子数组（必要时用 `fill` 值填充） (★★★)
`提示： minimum maximum`

```python
# 作者： Nicolas Rougier

Z = np.random.randint(0,10,(10,10))
shape = (5,5)
fill  = 0
position = (1,1)

R = np.ones(shape, dtype=Z.dtype)*fill
P  = np.array(list(position)).astype(int)
Rs = np.array(list(R.shape)).astype(int)
Zs = np.array(list(Z.shape)).astype(int)

R_start = np.zeros((len(shape),)).astype(int)
R_stop  = np.array(list(shape)).astype(int)
Z_start = (P-Rs//2)
Z_stop  = (P+Rs//2)+Rs%2

R_start = (R_start - np.minimum(Z_start,0)).tolist()
Z_start = (np.maximum(Z_start,0)).tolist()
R_stop = np.maximum(R_start, (R_stop - np.maximum(Z_stop-Zs,0))).tolist()
Z_stop = (np.minimum(Z_stop,Zs)).tolist()

r = tuple([slice(start,stop) for start,stop in zip(R_start,R_stop)])
z = tuple([slice(start,stop) for start,stop in zip(Z_start,Z_stop)])
R[r] = Z[z]
print(Z)
print(R)
```
#### 81. 给定数组 Z = [1,2,3,4,5,6,7,8,9,10,11,12,13,14]，如何生成数组 R = [[1,2,3,4], [2,3,4,5], [3,4,5,6], ..., [11,12,13,14]]？ (★★★)
`提示： stride_tricks.as_strided, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# 作者： Stefan van der Walt

Z = np.arange(1,15,dtype=np.uint32)
R = stride_tricks.as_strided(Z,(11,4),(4,4))
print(R)

# 作者： Jeff Luo (@Jeff1999)

Z = np.arange(1, 15, dtype=np.uint32)
print(sliding_window_view(Z, window_shape=4))
```
#### 82. 计算矩阵的秩 (★★★)
`提示： np.linalg.svd, np.linalg.matrix_rank`

```python
# 作者： Stefan van der Walt

Z = np.random.uniform(0,1,(10,10))
U, S, V = np.linalg.svd(Z) # 奇异值分解
threshold = len(S) * S.max() * np.finfo(S.dtype).eps
rank = np.sum(S > threshold)
print(rank)

# 另一种解法：
# 作者： Jeff Luo (@Jeff1999)

rank = np.linalg.matrix_rank(Z)
print(rank)
```
#### 83. 如何找出数组中出现次数最多的值？
`提示： np.bincount, argmax`

```python
Z = np.random.randint(0,10,50)
print(np.bincount(Z).argmax())
```
#### 84. 从一个随机的 10x10 矩阵中提取所有连续的 3x3 子块 (★★★)
`提示： stride_tricks.as_strided, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# 作者： Chris Barker

Z = np.random.randint(0,5,(10,10))
n = 3
i = 1 + (Z.shape[0]-3)
j = 1 + (Z.shape[1]-3)
C = stride_tricks.as_strided(Z, shape=(i, j, n, n), strides=Z.strides + Z.strides)
print(C)

# 作者： Jeff Luo (@Jeff1999)

Z = np.random.randint(0,5,(10,10))
print(sliding_window_view(Z, window_shape=(3, 3)))
```
#### 85. 创建一个二维数组子类，使其满足 Z[i,j] == Z[j,i] (★★★)
`提示：类方法`

```python
# 作者： Eric O. Lebigot
# 注意：仅适用于二维数组，且需通过索引赋值

class Symetric(np.ndarray):
    def __setitem__(self, index, value):
        i,j = index
        super(Symetric, self).__setitem__((i,j), value)
        super(Symetric, self).__setitem__((j,i), value)

def symetric(Z):
    return np.asarray(Z + Z.T - np.diag(Z.diagonal())).view(Symetric)

S = symetric(np.random.randint(0,10,(5,5)))
S[2,3] = 42
print(S)
```
#### 86. 给定 p 个形状为 (n,n) 的矩阵和 p 个形状为 (n,1) 的向量，如何一次性计算这 p 组矩阵与向量乘积的总和（结果形状为 (n,1)）？ (★★★)
`提示： np.tensordot`

```python
# 作者： Stefan van der Walt

p, n = 10, 20
M = np.ones((p,n,n))
V = np.ones((p,n,1))
S = np.tensordot(M, V, axes=[[0, 2], [0, 1]])
print(S)

# 其原理如下：
# M 的形状为 (p,n,n)
# V 的形状为 (p,n,1)
# 因此，对 M 和 V 的第 0 轴与第 0 轴配对求和，
# 再对第 2 轴与第 1 轴配对求和，得到形状为 (n,1) 的向量。
```
#### 87. 给定一个 16x16 数组，如何对每个 4x4 子块分别求和？ (★★★)
`提示： np.add.reduceat, from numpy.lib.stride_tricks import sliding_window_view (np>=1.20.0)`

```python
# 作者： Robert Kern

Z = np.ones((16,16))
k = 4
S = np.add.reduceat(np.add.reduceat(Z, np.arange(0, Z.shape[0], k), axis=0),
                                       np.arange(0, Z.shape[1], k), axis=1)
print(S)

# 另一种解法：
# 作者： Sebastian Wallkötter (@FirefoxMetzger)

Z = np.ones((16,16))
k = 4

windows = np.lib.stride_tricks.sliding_window_view(Z, (k, k))
S = windows[::k, ::k, ...].sum(axis=(-2, -1))

# 另一种解法（由 @Gattocrucco 提供）
S = Z.reshape(4, 4, 4, 4).sum((1, 3))
```
#### 88. 如何使用 NumPy 数组实现生命游戏？ (★★★)
`暂无提示。`

```python
# 作者： Nicolas Rougier

def iterate(Z):
    # 统计相邻细胞的数量
    N = (Z[0:-2,0:-2] + Z[0:-2,1:-1] + Z[0:-2,2:] +
         Z[1:-1,0:-2]                + Z[1:-1,2:] +
         Z[2:  ,0:-2] + Z[2:  ,1:-1] + Z[2:  ,2:])

    # 应用规则
    birth = (N==3) & (Z[1:-1,1:-1]==0)
    survive = ((N==2) | (N==3)) & (Z[1:-1,1:-1]==1)
    Z[...] = 0
    Z[1:-1,1:-1][birth | survive] = 1
    return Z

Z = np.random.randint(0,2,(50,50))
for i in range(100): Z = iterate(Z)
print(Z)
```
#### 89. 如何获取数组中最大的 n 个值？ (★★★)
`提示： np.argsort | np.argpartition`

```python
Z = np.arange(10000)
np.random.shuffle(Z)
n = 5

# 较慢
print (Z[np.argsort(Z)[-n:]])

# 较快
print (Z[np.argpartition(-Z,n)[:n]])
```
#### 90. 给定任意数量的向量，构建它们的笛卡尔积（各向量元素的所有组合） (★★★)
`提示： np.indices`

```python
# 作者： Stefan Van der Walt

def cartesian(arrays):
    arrays = [np.asarray(a) for a in arrays]
    shape = (len(x) for x in arrays)

    ix = np.indices(shape, dtype=int)
    ix = ix.reshape(len(arrays), -1).T

    for n, arr in enumerate(arrays):
        ix[:, n] = arrays[n][ix[:, n]]

    return ix

print (cartesian(([1, 2, 3], [4, 5], [6, 7])))
```
#### 91. 如何从普通数组创建记录数组？ (★★★)
`提示： np.core.records.fromarrays`

```python
Z = np.array([("Hello", 2.5, 3),
              ("World", 3.6, 2)])
R = np.core.records.fromarrays(Z.T,
                               names='col1, col2, col3',
                               formats = 'S8, f8, i8')
print(R)
```
#### 92. 给定一个大向量 Z，使用 3 种不同的方法计算 Z 的三次方 (★★★)
`提示： np.power, *, np.einsum`

```python
# 作者： Ryan G.

x = np.random.rand(int(5e7))

%timeit np.power(x,3)
%timeit x*x*x
%timeit np.einsum('i,i,i->i',x,x,x)
```
#### 93. 给定两个形状分别为 (8,3) 和 (2,2) 的数组 A 和 B，如何找出 A 中这样的行：对于 B 的每一行，该行都至少包含其中的一个元素，且不考虑 B 中元素的顺序？
`提示： np.where`

```python
# 作者： Gabe Schwartz

A = np.random.randint(0,5,(8,3))
B = np.random.randint(0,5,(2,2))

C = (A[..., np.newaxis, np.newaxis] == B)
rows = np.where(C.any((3,1)).all(1))[0]
print(rows)
```
#### 94. 给定一个 10x3 矩阵，提取元素不全相等的行（例如 [2,2,3]） (★★★)
`暂无提示。`

```python
# 作者： Robert Kern

Z = np.random.randint(0,5,(10,3))
print(Z)
# 适用于所有 dtype 数组的解法（包括字符串数组和记录数组）
E = np.all(Z[:,1:] == Z[:,:-1], axis=1)
U = Z[~E]
print(U)
# 仅适用于数值数组的解法，Z 的列数不限
U = Z[Z.max(axis=1) != Z.min(axis=1),:]
print(U)
```
#### 95. 将一个整数向量转换为二进制表示矩阵 (★★★)
`提示： np.unpackbits`

```python
# 作者： Warren Weckesser

I = np.array([0, 1, 2, 3, 15, 16, 32, 64, 128])
B = ((I.reshape(-1,1) & (2**np.arange(8))) != 0).astype(int)
print(B[:,::-1])

# 作者： Daniel T. McDonald

I = np.array([0, 1, 2, 3, 15, 16, 32, 64, 128], dtype=np.uint8)
print(np.unpackbits(I[:, np.newaxis], axis=1))
```
#### 96. 给定一个二维数组，如何提取其中不重复的行？ (★★★)
`提示： np.ascontiguousarray | np.unique`

```python
# 作者： Jaime Fernández del Río

Z = np.random.randint(0,2,(6,3))
T = np.ascontiguousarray(Z).view(np.dtype((np.void, Z.dtype.itemsize * Z.shape[1])))
_, idx = np.unique(T, return_index=True)
uZ = Z[idx]
print(uZ)

# 作者： Andreas Kouzelis
# NumPy >= 1.13
uZ = np.unique(Z, axis=0)
print(uZ)
```
#### 97. 给定两个向量 A 和 B，使用 einsum 写出与 inner、outer、sum 和 mul 函数等价的表达式 (★★★)
`提示： np.einsum`

```python
# 作者： Alex Riley
# 请务必阅读： http://ajcr.net/Basic-guide-to-einsum/

A = np.random.uniform(0,1,10)
B = np.random.uniform(0,1,10)

np.einsum('i->', A)       # np.sum(A)
np.einsum('i,i->i', A, B) # A * B
np.einsum('i,i', A, B)    # np.inner(A, B)
np.einsum('i,j->ij', A, B)    # np.outer(A, B)
```
#### 98. 给定由两个向量 (X,Y) 描述的路径，如何沿路径进行等距采样？ (★★★)
`提示： np.cumsum, np.interp`

```python
# 作者： Bas Swinckels

phi = np.arange(0, 10*np.pi, 0.1)
a = 1
x = a*phi*np.cos(phi)
y = a*phi*np.sin(phi)

dr = (np.diff(x)**2 + np.diff(y)**2)**.5 # 各线段的长度
r = np.zeros_like(x)
r[1:] = np.cumsum(dr)                # 累加路径长度
r_int = np.linspace(0, r.max(), 200) # 等距采样的路径
x_int = np.interp(r_int, r, x)       # 对路径进行插值
y_int = np.interp(r_int, r, y)
```
#### 99. 给定一个整数 n 和一个二维数组 X，从 X 中选出可视为 n 次试验的多项分布抽样结果的行，即仅包含整数且元素之和为 n 的行 (★★★)
`提示： np.logical_and.reduce, np.mod`

```python
# 作者： Evgeni Burovski

X = np.asarray([[1.0, 0.0, 3.0, 8.0],
                [2.0, 0.0, 1.0, 1.0],
                [1.5, 2.5, 1.0, 0.0]])
n = 4
M = np.logical_and.reduce(np.mod(X, 1) == 0, axis=-1)
M &= (X.sum(axis=-1) == n)
print(X[M])
```
#### 100. 计算一维数组 X 的均值的 95% 自助法置信区间（即对数组元素进行 N 次有放回重采样，计算每次样本的均值，然后计算这些均值的百分位数） (★★★)
`提示： np.percentile`

```python
# 作者： Jessica B. Hamrick

X = np.random.randn(100) # 随机一维数组
N = 1000 # 自助法重采样次数
idx = np.random.randint(0, X.size, (N, X.size))
means = X[idx].mean(axis=1)
confint = np.percentile(means, [2.5, 97.5])
print(confint)
```