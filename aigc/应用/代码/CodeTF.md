# CodeTF

最先进的LLM代码，一站式Transformer库。
CodeTF是一个使用Python编写的的基于transformer的一站式库，用于代码大型语言模型(code LLM)和代码智能，
为代码智能任务(如代码汇总、翻译、代码生成等)的训练和推理提供了无缝接口。
它旨在促进将SOTA CodeLLMs轻松集成到实际应用程序中。

除了LLM的核心代码功能外，CodeTF还提供了跨各种语言的代码操作实用程序，
包括轻松提取代码属性。使用tree-sitter作为其核心AST解析器，它支持解析函数名、注释和变量名等属性。
为许多语言提供了预构建的库，从而消除了复杂的解析器设置的需要。
因此，CodeTF为代码智能任务提供了一个用户友好且可访问的环境。

github: [https://github.com/salesforce/CodeTF](https://github.com/salesforce/CodeTF)