## Questions

**Q：Bagging与Boosting的区别**

1. 样本选择上：Bagging：训练集是在原始集中有放回选取的，从原始集中选出的各轮训练集之间是独立的。Boosting：每一轮的训练集不变，只是训练集中每个样例在分类器中的权重发生变化。而权值是根据上一轮的分类结果进行调整。
2. 样例权重：Bagging：使用均匀取样，每个样例的权重相等；Boosting：根据错误率不断调整样例的权值，错误率越大则权重越大。
3. 预测函数：Bagging：所有预测函数的权重相等。Boosting：每个弱分类器都有相应的权重，对于分类误差小的分类器会有更大的权重。
4. 并行计算：Bagging：各个预测函数可以并行生成。Boosting：各个预测函数只能顺序生成，因为后一个模型参数需要前一轮模型的结果。
5. bagging是减少variance，而boosting是减少bias

**Q：Bagging、Boosting、Stacking、Blending定义**

1. Bagging从训练集从进行子抽样组成每个基模型所需要的子训练集，对所有基模型预测的结果进行综合产生最终的预测结果。通常分类任务使用投票的方式集成，而回归任务通过平均的方式集成。
2. Boosting通过算法集合将弱学习器转换为强学习器。训练过程为阶梯状，基模型按次序一一进行训练（实现上可以做到并行），基模型的训练集按照某种策略每次都进行一定的转化。对所有基模型预测的结果进行线性综合产生最终的预测结果。
3. Stacking将训练好的所有基模型对训练集进行预测,第j个基模型对第i个训练样本的预测值将作为新的训练集中第i个样本的第j个特征值，最后基于新的训练集进行训练。
4. Blending与Stacking大致相同，只是Blending的主要区别在于训练集不是通过K-Fold的CV策略来获得预测值从而生成第二阶段模型的特征，而是建立一个Holdout集。
