# pandas

pandas用python编写的一个快速、强大、灵活且易于使用的开源数据分析和操作工具

主站: [https://pandas.pydata.org/](https://pandas.pydata.org/)
帮助文档: [http://pandas.pydata.org/docs/](http://pandas.pydata.org/docs/)

安装方式: `conda install pandas` 或 `pip install pandas`

## pandas介绍

* pandas处理表格数据，如电子表格或数据库数据。
  pandas帮你探索、清理和处理的数据，
  在pandas中，一个数据表被称为[DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html#pandas.DataFrame).
* pandas支持集成多种文件格式或外部数据源(csv,excel,sql,json,parquet,...)，通过方法前缀为`read_*`进行读取，`to_*`进行存储。
* 选择或过滤特定的行，根据条件过滤，方法切分，选择和抽取你需要的数据。
* pandas提供绘制数据开箱即用，你可以根据数据绘制如(散点图，柱状图，箱线图等)
* 不需要遍历所有行进行运算，可以进行列操作，在DataFrame中可以添加列根据已有的其它列。
* 支持基本的的统计算法(mean, median, min, max, counts…),这些或自定义的聚合可以用在整个数据集上，数据滑动窗口
  或group by分组. 后者也被称为分割-应用-组合方法。
* 修改数据表结构有多种方式。你可以[melt()](https://pandas.pydata.org/docs/reference/api/pandas.melt.html#pandas.melt)
  宽到长/整齐的表单
  或[pivot()](https://pandas.pydata.org/docs/reference/api/pandas.pivot.html#pandas.pivot)从长到宽的格式。
  通过内置聚合，可以用一条命令创建透视表。
* 多个表格可以类似数据库以列和以行进行join/merge进行操作，提供多表合并数据。
* 强力支持时序，有大量工具支持dates, times, and time-indexed数据.
  数据集不只支持数据，还提供各种函数支持干净的文本数据和抽取有用的信息。