## Questions
**Q: word2vec训练时如何加速？**

1. 负采样
2. 层级softmax

**Q：h-softmax有什么问题？**

1. 在batch size训练的时候速度会下降
2. h-softmax的哈夫曼树是在数据集统计数据的基础上建立的，如果扩展新的数据集，这棵树要要重建

**Q: OOV问题怎么解决？**

1. 使用UNK，设置一个额外的embedding
2. 使用word pieces，用sub-word embedding组合出word embedding
3. 对于翻译问题，可以用同音词或直接拷贝。

**Q: word2vec，fasttext区别**

word2vec是单词级别的，fasttext是ngrams级别的，涉及到了更细粒度的特征

**Q: fasttext是怎么减小ngrams的内存占用的？**

1. 过滤掉出现次数少的单词
2. 使用hash存储，将映射到一个hash_value的embedding用一个值
3. 由采用字粒度变化为采用词粒度

**Q：Word2vec与LDA的区别**

1. Word2vec是用“上下文-单词”的矩阵进行学习
2. LDA使用文档中的单词的共现关系进行学习

**Q：主题模型和词嵌入模型的区别**

1. 主题模型是一种基于概率图模型的生成式的模型，它的似然函数可以写成若干条件概率连乘的形式，其中包括需要推测的隐变量。
2. 词嵌入模型一般表达为神经网络的形式，似然函数定义在网络的输出之上，需要通过学习网络的权重以得到单词的稠密向量表示。

## References
1. [cs224n](https://www.bilibili.com/video/BV1pt411h7aT)

