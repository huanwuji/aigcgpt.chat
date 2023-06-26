# embedchain

embedchain是一个框架，可以在任何数据集上轻松创建基于LLM的机器人。
它抽象了加载数据集、分块、创建嵌入然后存储在矢量数据库中的整个过程。
您可以使用.add和.add本地函数添加单个或多个数据集，然后使用.query函数从添加的数据集中查找答案
如果你想创建一个Naval Ravikant机器人，它有1个youtube视频，1本书和2个博客文章，
以及你提供的问题和答案，
你所需要做的就是添加视频，pdf和博客文章的链接，QnA对和embedchain将为你创建一个机器人。

github: [https://github.com/embedchain/embedchain](https://github.com/embedchain/embedchain)