# Matplotlib

Matplotlib是一个用于在Python中创建静态、动画和交互式可视化的综合库，

主站: [https://matplotlib.org/](https://matplotlib.org/)

***tips: 首页的代码需要安装最新的环境运行，包括Python版本，可以使用conda进行安装***

*官方首页demo, 可以直接生成图表:*

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 2 * np.pi, 200)
y = np.sin(x)

fig, ax = plt.subplots()
ax.plot(x, y)
plt.show()
```