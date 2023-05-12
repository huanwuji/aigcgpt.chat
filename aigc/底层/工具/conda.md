# conda

支持Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, FORTRAN等语言的包、依赖和环境管理工具

文档: [https://conda.io/](https://conda.io/)

安装文档: [https://conda.io/projects/conda/en/latest/user-guide/install/index.html#](https://conda.io/projects/conda/en/latest/user-guide/install/index.html#)
或者直接安装: https://www.anaconda.com/

使用命令:

* conda更新: `conda update conda`
* 命名`snowflakes`并安装biopython: conda create --name snowflakes biopython
* 环境:
    * 如安装管理Python: `conda create --name snakes python=3.9`
    * 激活环境: `conda activate snakes`
    * 删除环境： `conda env remove snakes`
    * 查看所有环境: `conda info --envs`
* 安装包: `conda install beautifulsoup4`
* 卸载包: `conda remove beautifulsoup4`
* 查找软件包: `conda search java`
* 查看已有包:
    * `conda list`
    * 查看`myenv`环境下的已有包: `conda list -n myenv`
    * 查看py开头的已有包: `conda list ^py`

在IDEA使用时，新建项目时，环境 -> 现有 -> 添加解释器 -> 添加本地解释器, 然后选择已有的conda环境，否则会新建新的

详细命令文档: [https://docs.conda.io/projects/conda/en/stable/commands.html](https://docs.conda.io/projects/conda/en/stable/commands.html)