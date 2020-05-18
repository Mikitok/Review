## Questions
**Q: LSTM相比普通RNN有哪些优点？**

1. 添加了三个门操作和cell memory，可以更好地建模长距离依赖
2. 可以有效降低梯度爆炸和梯度消失的问题

**Q: LSTM如何解决梯度消失问题？**

因为在LSTM中，各个时间步之间的权重是共享的，所以最终的梯度为各个时间步的梯度之和。LSTM的梯度传播有很多条路径，最主要的是细胞状态更新这一条，该过程中只有逐元素的相乘和相加操作，梯度流最稳定，因此基本不会发生梯度消失。即便其他远距离路径梯度消失了，只要保证有一条路径梯度不消失，总的远距离梯度就不会消失。

**Q: LSTM可否解决梯度爆炸问题？**

LSTM可以将都梯度爆炸的概率。传统的RNN网络因为循环乘以同一个权重，当权重特征值有大于1，就会产生梯度爆炸。而LSTM中最主要的是细胞状态更新这一条，该过程中只有逐元素的相乘和相加操作，梯度流最稳定。而其他路径非常崎岖，和普通 RNN 相比多经过了很多次激活函数（导数都小于 1），因此 LSTM 发生梯度爆炸的频率要低得多。

**Q: LSTM为什么要选择sigmoid和tanh作为激活函数？**

1. 首先，对于门操作，激活函数的值域应在0~1之间，且应为单调函数，sigmoid为很直接的方法。
2. 在求值时，选取tanh为激活函数，因为tanh的求值范围为-1~1，与大部分情况下特征中心为0相吻合。而且tanh在输入为0近似值时比sigmoid有更大梯度，模型手链更快。
3. 另外这两个函数都是饱和的，即输入值满足一定条件，输出不会有很大变化了。

**Q：LSTM的参数量有多少？**

（权重+偏置）* 4

**Q：LSTM的参数量有多少？**

（权重+偏置）* 4

**Q：长短期记忆作用到GRU门上的表现是什么？**

1. 对于倾向于获得短期记忆的单元，reset gate激活频率更高。
2. 对于倾向于获得长期记忆的单元，update gate激活频率更高。

**Q：为什么tf里面forget_bias默认是1？**

在训练初期，让forget gate大一些，减少遗忘。因为LSTM依靠多个时间步的共享来避免梯度消失和减小梯度爆炸的概率。


## References
1. [LSTM梯度](https://www.zhihu.com/question/34878706)
2. [LSTM激活函数](https://www.zhihu.com/question/46197687?sort=created)
1. [LSTM理解](https://www.cnblogs.com/mj-selina/p/12463265.html)
2. [人人都能看懂的GRU](https://zhuanlan.zhihu.com/p/32481747)
3. [LSTM 和GRU的区别](https://blog.csdn.net/u012223913/article/details/77724621)
1. [TextCNN模型原理和实现](https://www.cnblogs.com/bymo/p/9675654.html)
2. [文本分类算法TextCNN原理详解（一）](https://www.cnblogs.com/ModifyRong/p/11319301.html)
