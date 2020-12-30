# Python程序优化
## 原则
* 要找准全流程中性能的瓶颈点(最影响整体效率的)，不要单纯为了技术优化而优化。
* 找到hotspot后，能优化则优化，超出能力范围。则看能否换工具、方向。

## 瓶颈分析工具
* cProfile (Function profiler)
```bash
python -m profile myscript.py
```
* Line Profiler (没有特别好的)

## Cython
对性能要求高的代码建议采用cython来写。
Cython是Python的超集，编写较直接C/C++（python C/C++ api)简单。

### 参考：
* 官方 https://cython.readthedocs.io/en/latest/index.html
  * 语法 https://cython.readthedocs.io/en/latest/src/userguide/language_basics.html#language-basics
* 简明教材 https://www.cnblogs.com/traditional/p/13289069.html

### 常用类型定义符号
* cdef 定义的对象在其他纯Python模块中不可见
* cpdef 定义的对象在其他纯Python模块中可见
* Python functions vs. C functions

### setuptools vs. cython
* 建议编写setup.py 来进行一键式构建cython扩展。
* setuptools默认采用C来构建cython.下列两处地方可以修改语言类型:
  
  hello.pyx 文件头部说明符合
```python
    # distutils: language=c++
    import numpy as np
    cimport numpy as np
    
    def say_hello_to(name):
        print("Hello %s!" % name)
```
setup.py文件中
```python
from distutils.core import setup, Extension
from Cython.Build import cythonize
import numpy

compile_flags = ['-std=c11',  '-fopenmp', '-DNPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION']
linker_flags = ['-fopenmp']

module = Extension('hello',
                   ['hello.pyx'],
                   language='c++',
                   include_dirs=[numpy.get_include()], # This helps to create numpy
                   extra_compile_args=compile_flags,
                   extra_link_args=linker_flags)

```
__注意__: .pyx文件头部设置的 language 优先级高于setup.py中的设置（当然只针对本模块而言）。
  
* 大项目中建议优先选择C++, 得益于STL可以直接在Cython中使用。
