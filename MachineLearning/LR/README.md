## Questions

**Q：LR损失，推导，并且求导**

**Q：LR如何进行并行计算**

1. 按行并行。即将样本拆分，分布式的计算梯度，然后归并求和再求其平均。
2. 按列并行。同一样本的特征也进行拆分，对第i维的梯度计算梯度计算公式仅与当前样本的第i维相关，所以可以分别计算wi的梯度，然后再合为整体的W。

**Q：LR与SVM在实际业务中如何选择？**

1. 如果需要输出概率水平大小，要选用LR，因为svm只输出类别
2. 在训练集较小时，SVM比较适合，LR需要较多的样本。
3. LR对异常值敏感，SVM对异常值不敏感。

Andrew NG有提到说，
1. 如果特征数相对于样本数差不多，则使用LR算法或者不带核函数的SVM（线性核函数）
2. 如果特征数很小，样本数适中，使用带有核函数的SVM算法。一般使用高斯核
3、如果特征数很小，样本数很大，手动增加更多的feature然后使用LR算法或者不带核函数的SVM（变成第一种情况）。

**Q：LR与FM有什么区别？**
1. 对于LR模型来说，它只能捕捉到特征之间线性的组合信息，然后用权重加以区分它们的重要程度。
2. FM模型是LR模型在特征组合方面的扩展，可以自动捕捉特征与特征之间高阶的联系因素。
3. LR学习的是组合特征需要预先定义，但是FM是自动捕捉的。 

**Q：LR优缺点**
1. 优点：计算代价不高，易于理解和实现
2. 缺点：容易欠拟合，分类精度可能不高。

## References
1. [lr与svm如何选择](https://blog.csdn.net/ningyanggege/article/details/84950961)
2. [由Logistic Regression所联想到的...](https://mp.weixin.qq.com/s?__biz=MzA4NTUxNTE4Ng==&mid=2247483830&idx=1&sn=3399777a45d168e5d8d58f57306cfad7&chksm=9fd78f6ba8a0067dd677c85ff0831bb83ffdfd6b281fc79e91b0d246cc21a1847ebce520980e&scene=21#wechat_redirect)
