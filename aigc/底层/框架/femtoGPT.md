# femtoGPT

纯rust实现的一个小型生成式预训练Transformer.
一切从头开始实现。包含张量处理逻辑，使用小型的GPT架构训练/推断代码。
对于那些喜欢LLM并希望深入了解这些模型如何工作的人来说，femtoGPT是一个很好的开始。
femtoGPT只使用随机生成库 (rand/rand-distr),数据序列化库(serde/bincode 保存加载已经训练好的模型)，并行计算库(
serde/bincode).
femtoGPT非常慢，因为大多数基本操作(例如矩阵乘法)都是以最简单的方式实现的。
使用梯度检查方法检查梯度的正确性，尽管仍然很有可能某些层的实现是错误的。(例如，我不确定我的LayerNorm是否无bug ?)

github: [https://github.com/keyvank/femtoGPT](https://github.com/keyvank/femtoGPT)