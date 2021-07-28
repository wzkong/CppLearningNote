# Numpy

[TOC]

## 基础知识

NumPy的主要对象是同构多维数组。所有类型都相同，由非负整数元组索引。在NumPy维度中称为 *轴* 。

NumPy的数组类被调用`ndarray`。它也被别名所知 `array`。

```python
#显示
np.set_printoptions(threshold=sys.maxsize) 
```

### 简单例子

```
>>> import numpy as np
>>> a = np.arange(15).reshape(3, 5)
>>> a
array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [10, 11, 12, 13, 14]])
>>> a.shape
(3, 5)
>>> a.ndim
2
>>> a.dtype.name
'int64'
>>> a.itemsize
8
>>> a.size
15
>>> type(a)
<type 'numpy.ndarray'>
#从list转换
>>> b = np.array([6, 7, 8])
>>> b
array([6, 7, 8])
>>> type(b)
<type 'numpy.ndarray'>
```



### 属性

```
#数组的轴（维度）的个数
ndarray.ndim

#数组的维度 (n,m)
ndarray.shape

#数组元素的总数
ndarray.size

#元素类型
ndarray.dtype

ndarray.itemsize
```

### 数组创建

```
#1
np.array() #列表或者元组
np.array( [ [1,2], [3,4] ], dtype=complex)

#2
np.zeros((3,4))
np.ones(())
np.empty(())
np.random.randint(5, size=(2, 4))

#3
整数
np.arange(5, 10, 5) #step
浮点数
np.linspace(0, 2, 9) #分成九等份
```

### 基本操作

+-*/ ** np.sin(a) 这是单个单个计算的

矩阵乘法A.dot(B)

```
#axis = 0对每个列就行这样的操作，axis =1是对行进行这样的操作
a.sum(axis=0)
a.min()
a.max()
b.cumsum(axis=1)  
```

### 通函数

```python
np.exp
np.sqrt
np.sin
```

### 索引、切片和迭代

一维的数组可以进行这样的操作

```
a[2:5]
a[:6:2]
a[ : :-1]

>>> def f(x,y):
...     return 10*x+y
...
>>> b = np.fromfunction(f,(5,4),dtype=int)
```

三个点（ `...` ）表示产生完整索引元组所需的冒号

- `x[1,2,...]` 相当于 `x[1,2,:,:,:]`

```python
for element in b.flat:
...     print(element)
```

## 形状操作

```
a.ravel() 

a.reshape(6,2)

a.T

#如果在 reshape 操作中将 size 指定为-1，则会自动计算其他的 size 大小：
a.reshape(3,-1)
```

### 堆叠在一起

```
np.vstack((a,b)) #上下叠加
np.hstack((a,b)) #左右叠加

a = np.array([4.,2.])
b = np.array([3.,8.])
np.column_stack((a,b)) #1D数组叠加竖着叠加在一起
array([[ 4., 3.],
       [ 2., 8.]])
```

### 拆分

```
np.hsplit(a,3)   # Split a into 3 水平分割
np.vsplit #竖着
```

## 拷贝和视图

### 完全不复制

```
b = a #li
```

### 视图或浅拷贝

```
c = a.view() #共享数据 但别的东西不一样
```

### 深拷贝

```
d = a.copy()
```

## 结构化数组

https://www.numpy.org.cn/user/basics/rec.html#%E7%BB%93%E6%9E%84%E5%8C%96%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B

每个元组都具有以下形式`（字段名称、数据类型、形状）`

```
np.dtype([('x', 'f4'), ('y', np.float32), ('z', 'f4', (2, 2))])
```

数据分配

```python
x = np.array([(1, 2, 3), (4, 5, 6)], dtype='i8, f4, f8')
```

索引

```python
x['foo']
a[['a', 'c']] #使用多字段索引分配数组会修改原始数组
```

### Recarray Helper 函数

* numpy.lib.recfunctions.**append_fields**(*base*, *names*, *data*, *dtypes=None*, *fill_value=-1*, *usemask=True*, *asrecarray=False*)

```python
```



* numpy.lib.recfunctions.**apply_along_fields**(*func*, *arr*)

```
>>> from numpy.lib import recfunctions as rfn
>>> b = np.array([(1, 2, 5), (4, 5, 7), (7, 8 ,11), (10, 11, 12)],
...              dtype=[('x', 'i4'), ('y', 'f4'), ('z', 'f8')])
>>> rfn.apply_along_fields(np.mean, b)
array([ 2.66666667,  5.33333333,  8.66666667, 11.        ])
>>> rfn.apply_along_fields(np.mean, b[['x', 'z']])
array([ 3. ,  5.5,  9. , 11. ])
```

* numpy.lib.recfunctions.**drop_fields**(*base*, *drop_names*, *usemask=True*, *asrecarray=False*)

```python
>>> from numpy.lib import recfunctions as rfn
>>> a = np.array([(1, (2, 3.0)), (4, (5, 6.0))],
...   dtype=[('a', np.int64), ('b', [('ba', np.double), ('bb', np.int64)])])
>>> rfn.drop_fields(a, 'a')
array([((2., 3),), ((5., 6),)],
      dtype=[('b', [('ba', '<f8'), ('bb', '<i8')])])
>>> rfn.drop_fields(a, 'ba')
array([(1, (3,)), (4, (6,))], dtype=[('a', '<i8'), ('b', [('bb', '<i8')])])
>>> rfn.drop_fields(a, ['ba', 'bb'])
array([(1,), (4,)], dtype=[('a', '<i8')])
```

* numpy.lib.recfunctions.**get_names**(*adtype*)

```python
>>> adtype = np.dtype([('a', int), ('b', [('ba', int), ('bb', int)])])
>>> rfn.get_names(adtype)
('a', ('b', ('ba', 'bb')))
```

* numpy.lib.recfunctions.**merge_arrays**(*seqarrays*, *fill_value=-1*, *flatten=False*, *usemask=False*, *asrecarray=False*)

```python
>>> rfn.merge_arrays((np.array([1, 2]).view([('a', np.int64)]),
...               np.array([10., 20., 30.])),
...              usemask=False, asrecarray=True)
rec.array([( 1, 10.), ( 2, 20.), (-1, 30.)],
          dtype=[('a', '<i8'), ('f1', '<f8')])
```

* 

