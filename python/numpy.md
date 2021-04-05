```python
#注意为ipynb格式
import numpy as np

data = np.random.randn(2, 3)
data*10
data + data
data.shape
data.dtype

data1 = [6, 7.5, 8, 0, 1]
arr1 = np.array(data1)
data2 = [[1, 2, 3, 4], [5, 6, 7, 8]]
arr2 = np.array(data2)
arr2.dim
arr2.shape
np.zeros(10)
np.zeros(3, 6)
np.empty((2, 3, 2)) #
np.arange(15)

arr1 = np.array([1, 2, 3], dtype=np.float64)
arr2 = np.array([1, 2, 3], dtype=np.int32)
arr = np.array([1, 2, 3, 4, 5])
float_arr = arr.astype(np.float64)
numeric_strings = np.array(['1.25', '-9.6', '42'], dtype=np.string_)
numeric_strings.astype(float)

arr = np.array([[1., 2., 3.], [4., 5., 6.]])
arr * arr
arr - arr
1 / arr
arr ** 0.5
arr2 = np.array([[0., 4., 1.],[7., 2., 12.]])
arr2 > arr

arr = np.arange(10)
arr[5]
arr[5:8]
arr[5:8] = 12
arr_slice = arr[5:8]
arr_slice[1] = 12345 # 改变slice，原数组改变
arr_slice[:] = 64
arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
arr2d[2]
arr2d[0][2]
arr2d[0, 2] #二者等价
arr3d = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])
arr3d[0]
old_values = arr3d[0].copy()
arr3d[0] = 42
arr3d[0] = old_values
arr3d[1, 0]

arr2d[:2]
arr2d[:2, 1:]
arr2d[1, :2]
arr2d[:, :1]
arr2d[:2, 1:] = 0

names = np.array(['Bob', 'Joe', 'Will', 'Bob', 'Will', 'Joe', 'Joe'])
data = np.random.randn(7, 4)
names == 'Bob'
data[names == 'Bob']
data[names == 'Bob', 2:]
names != 'Bob'
data[~(names == 'Bob')]
cond = names == 'Bob'
data(~cond)
mask = (names == 'Bob') | (names == 'Will')
data[mask]
data[data < 0] = 0
data[names != 'Joe'] = 7

arr = np.empty((8, 4))
for i in range(8):
    arr[i] = i
arr[[4, 3, 0, 6]]
arr[[-3, -5, -7]]
arr = np.arange(32).reshape((8, 4))
arr[[1, 5, 7, 2],[0, 3, 1, 2]]
arr[[1, 5, 7, 2]][:, [0, 3, 1, 2]] #???

arr = np.arange(15).reshape((3, 5))
arr.T
arr = np.random.randn(6, 3)
np.dot(arr.T, arr)
arr = np.arange(16).reshape((2, 2, 4))
arr.transpose((1, 0, 2))
arr.swapaxes(1, 2)

arr = np.arange(10)
np.sqrt(arr)
np.exp(arr)
x = np.random.randn(8)
y = np.random.randn(8)
np.maximum(x, y)
arr = np.random.randn(7) * 5
remainder, whole_part = np.modf(arr)
np.sqrt(arr, arr)

points = np.arange(-5, 5, 0.01)
xs, ys = np.meshgrid(points, points)
z = np.sqrt(xs ** 2 + ys ** 2)

xarr = np.array([1.1, 1.2, 1.3, 1.4, 1.5])
yarr = np.array([2.1, 2.2, 2.3, 2.4, 2.5])
cond = np.array([True, False, True, True, False])
result = np.where(cond, xarr, yarr)
arr = np.random.randn(4, 4)
np.where(arr > 0, 2, -2)
np.where(arr > 0, 2, arr)

arr = np.random.randn(5, 4)
arr.mean()
np.mean(arr)
arr.sum()
arr.mean(axis=1)
arr.sum(axis=0)
arr = np.array([0, 1, 2, 3, 4, 5, 6, 7])
arr.cumsum()
arr = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
arr.cumsum(axis=0)
arr.cumprod(axis=1)

arr = np.random.randn(100)
(arr > 0).sum()
bools = np.array([False, False, True, False])
bools.any()
bools.all()

arr = np.random.randn(6)
arr.sort()
arr = np.random.randn(5, 3)
arr.sort(1)

names = np.array(['Bob', 'Joe', 'Will', 'Bob', 'Will', 'Joe', 'Joe'])
np.unique(names)
ints = np.array([3, 3, 3, 2, 2, 1, 1, 4, 4])
np.unique(ints)
values = np.array([6, 0, 0, 3, 2, 5, 6])
np.in1d(values, [2, 3, 6])

# 线性代数
x = np.array([[1., 2., 3.], [4., 5., 6.]])
y = np.array([[6., 23.], [-1, 7], [8, 9]])
x.dot(y)
np.dot(x, y)
np.dot(x, np.ones(3))
x @ np.ones(3)


from numpy.linalg import inv, qr

X = np.random.randn(5, 5)
mat = X.T.dot(X)
inv(mat)
mat.dot(inv(mat))
q, r = qr(mat)

# 伪随机数生成
samples = np.random.normal(size=(4, 4)) # 标准正态分布
np.random.seed(1234)
rng = np.random.RandomState(1234) # 创建一个与其它隔离的随机数生成器
rng.randn(10)
```

| 类型          | 类型代码 | 描述 |
| ------------- | -------- | ---- |
| int8，uint8   | i1，u1   |      |
| int16，uint16 | i2，u2   |      |
| int32，uint32 | i4，u4   |      |
| int64，uint64 | i8，u8   |      |
| float16       | f2       |      |
| float32       | f4       |      |
| float64       | f8       |      |
| float128      | f16      |      |
| bool          | ?        |      |
| object        | O        |      |
| string_       | S        |      |
| unicode       | U        |      |

