## Questions

**Q：TF中怎么实现判断语句？**

在tf中有一个函数是tf.cond，可以用来实现tf的条件判断。她的第一个参数是判断语句，第二个是判断为真的函数，第三个是判断为假时的函数。

**Q：Tensorflow常用的 Optimizer有哪些，简单说一下原理、超参数设置**

**Q：介绍一下tensorflow的计算图**

Tensorflow是一个通过计算图的形式来表述计算的编程系统。其中的Tensor,代表它的数据结构，而Flow代表它的计算模型。TensorFlow中的每一个计算都是计算图上的一个节点，而节点之间的线描述了计算之间的依赖关系。Tensorflow计算的过程就是利用的Tensor来建立一个计算图，然后使用Session会话来启动计算，最后得到结果的过程。

**Q：tensorflow的函数自动求导是如何实现的？**

链式法则。

## References
1. [TensorFlow计算模型—计算图](https://www.cnblogs.com/houjun/p/8824269.html)
2. [TensorFlow的自动求导具体是在哪部分代码里实现的？](https://www.zhihu.com/question/56443480)
3. [tensorflow的函数自动求导是如何实现的？](https://www.zhihu.com/question/54554389)
