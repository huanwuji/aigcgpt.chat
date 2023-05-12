# NumPy

基于Python的机器学习基本库，
NumPy API被广泛使用在Pandas, SciPy, Matplotlib, scikit-learn, scikit-image和其它数据科学包中。
NumPy库包含多维数组和矩阵数据结构。

你可能听说过一维数组，二维数据，NumPy的 `ndarray`表示矩阵和向量，
向量是一个单维数组(行向量和列向量没有区别),而矩阵指的是二维数组,
三维或高维数组，术语也经常用张量`tensor`.

在NumPy中，维度被称为`axes`，比如一个二维数据:

```python
[[0., 0., 0.],
 [1., 1., 1.]]
```

第一个axis长度是2，第二个axis长度是3。

* 提供多维数组运算
    * 创建数组，zeros(num), ones(num), empty(num), arange(num), arange(start,end, step), linspace(0, 10, num=5),ones(2,
      dtype=np.int64)
    * 添加、删除、合并和排序数组
    * 数组相关属性
        * `ndarray.ndim`指数据的维度数或axes个数
        * `ndarray.size`指数据元素总数
        * `ndarray.shape`显示一个元组，沿数组每个维度数量，一个二维数组2行3列就是(2,3)