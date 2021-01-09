学习笔记

## Numpy

* 深度学习中浮点型一般用float32，GPU对双精度支持不加。
* copy vs reference
```python
import numpy as np

x = np.random.randn(10,10)
```

* einops 
通过灵活而强大的张量操作符为你提供易读并可靠的代码。
支持 numpy、pytorch、tensorflow 以及其他框架

* Broadcast
    * 多维矩阵相乘（广义）
      看最后两个维度是否符合矩阵相乘规则：前一个的列 == 后一个的 行
      
* EinSum
 ijk, jkh -> ijh, x, y
  优先选Broadcast
  
* broadcast 一定能转 EinSum,反之不然。

## JAX
* jax提供了jit可以进行编译时优化。因此，if,loop等语句必须用jax.lax中的接口形式写。
* jax 中cond, scan 才能用到反向求导数。

## 后记
怎么学数学
* 不要强迫直观理解 
* 看证明：看他的思路、方法、为了解决什么问题

几个层次
* 熟悉的东西要做得对
* 新的东西知道其道理了要能做
* 不熟悉的东西要知道稍作思考才知道
* 能推导证明不熟悉的

