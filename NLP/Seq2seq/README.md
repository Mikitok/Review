## Questions
**Q: Seq2Seq在训练时期和测试时期有什么差异？**

1. 在训练和测试的时候，模型获得的输入的分布是不同的。训练的时候是数据集的分布，而测试的时候是预测结果的分布。实际来讲，训练的时候，在decoder中输入的是训练集句子的单词，而测试的时候，decoder输入的是上个时刻预测的单词。
2. 训练和测试采用的评估方式不同。训练的时候通常采用交叉熵，而测试的时候通常使用BLUE等评估标准。

**Q: Seq2Seq有哪些解码机制?

根据任务的不同，可以将seq2seq分为两大类：一类是non-open-ended（如机器翻译），一类是open-ended（如故事生成）。对于non-open-ended任务，目标句子是比较确切的，这个时候greedy和BS最常用。对于open-ended任务，希望生成句子具有随机性，所以会使用一些设计随机采样的解码方法，如（1）完全的随机；（2）用temperature控制大概率的词语以更大概率输出，以避免长尾词出现太多；（3）是在top k高概率词里面采样。

**Q: Beam search与Viterbi的关

BS与Viterbi计算过程十分相似，但是BS保留了top K个节点的结果，但Viterbi保留了全部的结果。Viterbi可以求得全局最优解，BS只能求得局部最优解。

**Q: BLEU作为一个基于precision的指标，如何解决生成重复n-gram的问题？

在计算分子的count的时候如果值超过了ground-truth里面的计数，就停止计数，所以重复的话只会增加分母，对分子无益，然后就变小了。

**Q: BLEU的缺点 
1. 不考虑语法的正确性
2. 没有考虑相似表达，导致合理翻译被否定
3. 易收到常用词干扰（无论翻译是否正确，常用词基本都会存在）
4. 短句得分有时较高

## References
1. [Seq2Seq简介](https://github.com/NLP-LOVE/ML-NLP/tree/master/NLP/16.5%20seq2seq)
2. [BLEU](https://www.cnblogs.com/jiangxinyang/p/10523585.html)

