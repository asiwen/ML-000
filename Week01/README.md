学习笔记
# 课前准备
## 环境准备
* git&github 
* anaconda3 & jupyter
  建议使用python3.7(训练营中使用)， 可以使用使用如下命令安装需要的环境：
```bash
conda create -n py37 && conda install python=3.7 
```
注意：使用等号(=)则选择该版本下的最新子版本。用恒定号(==)则表示精确匹配一个子版本好。
* R安装
```bash
conda install r
```
注意：建议在python的同一个环境下用conda安装R.
R kernel for jupyter notebook
参考：https://github.com/IRkernel/IRkernel，在 conda创建的虚拟环境中启动R命令并输入如下命令
```bash
install.packages('IRkernel')
IRkernel::installspec()  # to register the kernel in the current R installation
```

* ide (pycharm/vscode)

# Python基础
## 基本语法
* 函数定义中形参类型提示
``` python
def myfunc(a:float, *args, **kwargs) -> str:
    return str(a)
```
× try...except

× 默认参数陷阱

  请始终用非可变对象来作为默认参数的值。详细见 GhostBus案例。

## 高级用法
* 列表推导式/生成器表达式
  
* Magic Functions
  ```
  __str__, __repr__, __sub__, __mul__, __abs__, __bool__, __lt__, ...
  ```
* monad
  
  函数式编程中异常处理模式，__作用解决函数式编程中非纯函数的副作用__。一些例子： 
  
  × [Monad in Python](https://pythoninformer.com/programming-techniques/functional-programming/monads/)
  
  × [A Java Example for monad](https://zhuanlan.zhihu.com/p/139239510)
  
  × [Another Java Example for monad](https://www.jdon.com/idea/java8-monad.html)
  
* 装饰器decorator

  用来修饰一个函数的函数。（与闭包有些类似）

* dataclass
  
  python3.7中引入的一个装饰器

# R简介
## 有了Python为什么需要R
* 操作方便：例如 dplyr 包当中可以实现迅速的数据探索性分析。
* 很多统计性常用的包：例如使用多重填充后用，
GLM+ 样条 +L1 损失构造变量，这种特征构造对于和
线性模型有关的（例如深度学习）有很大关系。注意
R 当中不需要考虑模型不收敛问题，解决这个问题用
C（python 速度过慢）来写大概需要 1000 行（并且还
没考虑缺失值问题）
* 非预测性建模问题(__见加餐__)  
* 常用模块
```
caret -- Classification and Regression Training
dbplyr -- dbplyr is the database backend for dplyr. It allows you to use remote database tables as if they are in-memory data frames by automatically converting dplyr code into SQL.
```

# C/C++ 环境搭建
VSCode+CMake+Gcc on Ubuntu: https://zhuanlan.zhihu.com/p/157362239
