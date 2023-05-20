# smol developer

100k的上下文窗口，它让每个开发拥有自己的小可爱开发者。
这是一个"初级开发者"代理原型(又名`smol dev`)。你给它一个产品说明它帮你搭建整个代码库。
不像一次特定的生成器，如`create-react-app`或者`create-nextjs-app`，它可以`create-anything-app`。
你可以通过smol dev不断的循环开发脚手架prompt。
工程师使用提示词，页不是提示工程师。
示例`prompt.md`展示了一种基于AI的可能性，但还是要以人为中心的开发流程:

* 人类写一个基础的应用提示词去创建
* `main.py`生成代码
* 粘贴错误信息去提示，就像在GitHub提issue
* 还可以使用`debugger.py`去读取整个代码库提出具体的修改意见

就这样不断的循环，AI只有能带来价值的时候才有用，如果不行的，还是要靠我们自己。

github: [https://github.com/smol-ai/developer](https://github.com/smol-ai/developer)