## Questions
**Q: Transformer相比于RNN/LSTM，有什么优势？为什么？**

1. RNN是序列性的模型，当前状态的计算依赖于上一个状态，所以并行计算能力很差。而Transformer使用positional embedding保存单词的位置信息，使得Encoder对于输入序列是可以并行计算的。
2. 实验结果表明，Transformer在很多任务上特征抽取能力比RNN系列的模型要好。

**Q：Transformer是如何训练的？测试阶段如何进行测试呢？**

Transformer训练过程与seq2seq类似，使用Encoder端得到输入的表示，并将其输入到Decoder端进行解码，通过softmax来预测下一个单词(token)，然后根据softmax多分类的损失函数，将loss反向传播即可。需要注意的是，Encoder端可以并行计算，一次性将输入序列全部encoding出来，但Decoder端不是一次性把所有单词(token)预测出来的，而是像seq2seq一样一个接着一个预测出来的。

对于测试阶段，其与训练阶段唯一不同的是Decoder端最底层的输入。训练时输入的是groundtruth，测试时是上一个状态的输出。

**Q：self-attention公式中的归一化有什么作用？**

随着维度的增大，QK点积的结果也会变大，这样会将softmax函数推入梯度非常小的区域，使得收敛困难(可能出现梯度消失的情况)。

**Q：transformer为什么用Add不用concat**

1. concat会增加向量的维度。
2. 根据李宏毅的介绍，将两个向量concat，然后乘以一个权重矩阵，在线性代数技巧下，可以得到和相加一样的结果。

**Q：Transformer的decorder部分的mask和encorder部分的mask有什么不同**

**Q：Transformer输入长文本的改进**


## References
1. [Transformer详解](https://zhuanlan.zhihu.com/p/44121378)
2. [详解Transformer模型](https://www.cnblogs.com/jiangxinyang/p/10069330.html)
3. [为什么Transformer 需要进行 Multi-head Attention？](https://www.zhihu.com/question/341222779/answer/814111138)
4. [Transformer框架中的add&norm中的norm是什么样的归一化？](https://www.zhihu.com/question/309177367)
5. [一些关于Transformer的问题整理](https://www.nowcoder.com/discuss/258321?type=2)
6. [Transformer-XL](https://www.sohu.com/a/292688373_473283)


