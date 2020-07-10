## Questions

**Q：batch gradient descent、stochastic mini-batch gradient descent 和 stochastic gradient descent有什么区别？**

1. batch gradient descent是指每次迭代用所有的训练样本来更新参数。它的优点是理想状态下经过足够多的迭代后可以达到全局最优。缺点是如果数据集非常大，没有办法一次性载入内存计算，而且因为每次迭代都要计算全部的样本，所以对于大数据量会非常的慢。所以BGD比较适合小样本。
2. stochastic gradient descent（最初）的思想是每次只训练一个样本去更新参数。它的优点是对大数据集可以使用，但是也存在缺点，因为每次只用一个样本来更新参数，会导致模型的不稳定性大些，不一定朝着最优的方向优化，可能会有震荡产生。
3. stochastic mini-batch gradient descent（现在SGD一般指的）这个，是batch gradient descent和stochastic gradient descent的折中方案，就是每次用batch_size数量的样本来更新参数。batch_size 通常设置为2的幂次方，因为设置成2的幂次方，更有利于GPU加速。

## References
1. [几种梯度下降方法对比](https://blog.csdn.net/u012328159/article/details/80252012)

