# guidance

微软提供的用于控制大型语言模型的指导语言。
通过引导使您能够比传统的提示或链接更有效地控制现代语言模型
将生成、提示和逻辑控制放在一个连续流的匹配中，与语言模型实际处理文本的方式相匹配
简单的输出结构，如Chain of Thought及其许多变体(如ART, Auto-CoT等)。
已经被证明可以提高LLM的表现，像GPT-4这样更强大的llm的出现允许更丰富的结构，并且引导使结构更容易和更简单。

它像一个模板语言，你可以修改变量，(如 `{{proverb}}`)和逻辑控制。
但不像一个标准的模板语言。它定义了一个良好的执行顺序。直接对应于语言模型处理的token顺序。
这意味着在执行过程中的任何时候，都可以使用语言模型来生成文本(使用`{{gen}}`命令)或做出逻辑控制流决策.
这种生成和提示的交错允许产生清晰可解析结果的精确输出结构。

示例:

```python
# we use LLaMA here, but any GPT-style model will do
llama = guidance.llms.Transformers("your_path/llama-7b", device=0)

# we can pre-define valid option sets
valid_weapons = ["sword", "axe", "mace", "spear", "bow", "crossbow"]

# define the prompt
character_maker = guidance("""The following is a character profile for an RPG game in JSON format.
```json
{
    "id": "{{id}}",
    "description": "{{description}}",
    "name": "{{gen 'name'}}",
    "age": {{gen 'age' pattern='[0-9]+' stop=','}},
    "armor": "{{#select 'armor'}}leather{{or}}chainmail{{or}}plate{{/select}}",
    "weapon": "{{select 'weapon' options=valid_weapons}}",
    "class": "{{gen 'class'}}",
    "mantra": "{{gen 'mantra' temperature=0.7}}",
    "strength": {{gen 'strength' pattern='[0-9]+' stop=','}},
    "items": [{{#geneach 'items' num_iterations=5 join=', '}}"{{gen 'this' temperature=0.7}}"{{/geneach}}]
}```""")

# generate a character
character_maker(
    id="e1f491f7-7ab8-4dac-8c20-c92b5e7d883d",
    description="A quick and nimble fighter.",
    valid_weapons=valid_weapons, llm=llama
)
```

github: [https://github.com/microsoft/guidance](https://github.com/microsoft/guidance)