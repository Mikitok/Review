## Questions
**Q: word2vec训练时如何加速？**

1. 负采样
2. 层级softmax

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

## References
1. [cs224n](https://www.bilibili.com/video/BV1pt411h7aT)

