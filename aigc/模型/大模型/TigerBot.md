# TigerBot

国人开源的大语言模型。
一个多语言多任务的大规模语言模型(LLM)。根据 OpenAI InstructGPT 论文在公开 NLP 数据集上的自动评测，TigerBot-7B 达到 OpenAI
同样大小模型的综合表现的 96%，并且这只是我们的 MVP，在此我们将如下探索成果开源：

模型：TigerBot-7B, TigerBot-7B-base，TigerBot-180B (research version)，
代码：基本训练和推理代码，包括双卡推理 180B 模型的量化和推理代码，
数据：预训练 100G，从 2TB 过滤后的数据中经过去噪去重清洗而得；监督微调 1G 或 100 万条数据，按比例涵盖用户指令常见的 10 大类
120 小类任务，
API: chat, plugin, finetune, 让用户能在半小时内无代码的训练和使用专属于自己的大模型和数据，
领域数据：涵盖金融，法律，百科，广邀大模型应用开发者，一起打造中国的世界级的应用。

github: [https://github.com/TigerResearch/TigerBot](https://github.com/TigerResearch/TigerBot)