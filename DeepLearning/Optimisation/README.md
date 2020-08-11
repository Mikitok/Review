## Questions

**Q：batch gradient descent、stochastic mini-batch gradient descent 和 stochastic gradient descent有什么区别？**

1. batch gradient descent是指每次迭代用所有的训练样本来更新参数。它的优点是理想状态下经过足够多的迭代后可以达到全局最优。缺点是如果数据集非常大，没有办法一次性载入内存计算，而且因为每次迭代都要计算全部的样本，所以对于大数据量会非常的慢。所以BGD比较适合小样本。
2. stochastic gradient descent（最初）的思想是每次只训练一个样本去更新参数。它的优点是对大数据集可以使用，但是也存在缺点，因为每次只用一个样本来更新参数，会导致模型的不稳定性大些，不一定朝着最优的方向优化，可能会有震荡产生。
3. stochastic mini-batch gradient descent（现在SGD一般指的）这个，是batch gradient descent和stochastic gradient descent的折中方案，就是每次用batch_size数量的样本来更新参数。batch_size 通常设置为2的幂次方，因为设置成2的幂次方，更有利于GPU加速。

**Q：SGD有什么缺点？**
1.	选择合适的learning rate比较困难
2.	对所有的参数更新使用同样的learning rate。对于稀疏数据或者特征，有时我们可能想更新快一些对于不经常出现的特征，对于常出现的特征更新慢一些，这时候SGD就不太能满足要求了
3.	SGD容易收敛到局部最优

**Q：总结**
1.	SGD方法是最基础的优化方法。
2.	Momentum方法通过添加动量，提高收敛速度；
3.	Nesterov方法在进行当前更新前，先进行一次预演，从而找到一个更加适合当前情况的梯度方向和幅度；
4.	Adagrad让不同的参数拥有不同的学习率，并且通过引入梯度的平方和作为衰减项，而在训练过程中自动降低学习率；
5.	AdaDelta则对Adagrad进行改进，让模型在训练后期也能够有较为适合的学习率。
6.	Adam对于每个参数，其不仅仅有自己的学习率，还有自己的Momentum量。

**Q：BatchNorm能缓解梯度消失么？为什么？**

BatchNorm能缓解梯度。因为随着网络深度加深或者在训练过程中，其分布逐渐发生偏移或者变动，整体分布逐渐往非线性函数的取值区间的上下限两端靠近，对于Sigmoid函数来说，意味着激活输入值WU+B是大的负值或正值，所以这导致后向传播时低层神经网络的梯度消失。而BN把逐渐向非线性函数映射后向取值区间极限饱和区靠拢的输入分布强制拉回到均值为0方差为1的比较标准的正态分布，使得非线性变换函数的输入值落入对输入比较敏感的区域，以此避免梯度消失问题。

## References
1. [几种梯度下降方法对比](https://blog.csdn.net/u012328159/article/details/80252012)
2. [最优化方法系列](https://blog.csdn.net/bvl10101111/article/details/72615621)
3. [神经网络中的各种优化方法](https://blog.csdn.net/autocyz/article/details/83114245)
4. [深度学习最全优化方法总结比较](https://blog.csdn.net/u012759136/article/details/52302426/)

