## Questions

**Q：介绍一下朴素贝叶斯的核心思想**

朴素贝叶斯是基于概率论的分类算法。于给定的训练数据集，首先基于特征条件独立假设学习输入/输出的联合概率分布；然后基于此模型，对给定的输入x ，利用贝叶斯定理求出后验概率最大的输出y。

**Q：朴素贝叶斯名字中的“朴素”是什么意思？**

朴素贝叶斯有两个假设。第一个假设是特征之间是互相独立的，第二个假设是所有特征同等重要。

**Q：举个例子说明假设特征独立的作用**

假设每个特征需要N个样本才能得到好的分布，一共有T个特征，若特征之间不独立则需要N^T个样本，但是如果特征之间互相独立，样本数量就减少到了N*T。

**Q：简单介绍一下朴素贝叶斯的算法流程**

1. 根据训练数据求得标签的先验概率和条件概率
2. 根据先验改论和条件概率计算得到后验概率
3. 确定后验概率最大的标签是x的类别

**Q：在朴素贝叶斯实现过程中有什么可以改进的地方？**

1. 朴素贝叶斯在计算后验概率的时候是概率的连乘，所以如果有一个概率为0最后的结果就为0。所以在求先验概率和条件概率的时候会在频数上进行拉普拉斯平滑，即在频数上加一个正数，这样概率就不会是0了。
2. 而且概率的连乘可能会来数值的下溢，所以可以把连乘转为log的求和。

**Q：朴素贝叶斯的优点**

1. 朴素贝叶斯模型发源于古典数学理论，有稳定的分类效率。
2. 对大数量训练和查询时具有较高的速度。即使使用超大规模的训练集，针对每个项目通常也只会有相对较少的特征数，并且对项目的训练和分类也仅仅是特征概率的数学运算而已。
3. 对小规模的数据表现很好，能个处理多分类任务，适合增量式训练，尤其是数据量超出内存时，我们可以一批批的去增量训练。
4. 对缺失数据不太敏感，算法也比较简单，常用于文本分类。
5. 朴素贝叶斯对结果解释容易理解。

**Q：朴素贝叶斯的缺点**

1. 朴素贝叶斯有两个假设。首先它假设属性之间相互独立，这个假设在实际应用中往往是不成立的，在属性个数比较多或者属性之间相关性较大时，分类效果不好。而在属性相关性较小时，朴素贝叶斯性能最为良好。对于这一点，有半朴素贝叶斯之类的算法通过考虑部分关联性适度改进。
2. 需要知道先验概率，且先验概率很多时候取决于假设，假设的模型可以有很多种，因此在某些时候会由于假设的先验模型的原因导致预测效果不佳。
3. 由于我们是通过先验和数据来决定后验的概率从而决定分类，所以分类决策存在一定的错误率。

**Q：写一下朴素贝叶斯的原理的公式**

**Q：朴素贝叶斯的公式推导过程**

参见《统计学习方法》

**Q：朴素贝叶斯的算法实现**

如果是NLP的话，统计词频，可以用0/1表示也可以用bag-of-words，然后按照流程算（机器学习方法实战有）。

**Q：如何利用朴素贝叶斯进行文本分类**

如上

## References
1. (朴素贝叶斯算法的理解与实现)[https://www.cnblogs.com/lliuye/p/9178090.html]