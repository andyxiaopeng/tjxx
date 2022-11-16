# 手机定价区间分类

## 数据集说明

数据集是从kaggle下载下来的，一共有21个字段，2000条记录。

最后的字段是数据的标签，剩余20个字段是实际训练的数据。

这20个字段包括了电池的参数、蓝牙、双卡、内存的大小等等。

## 数据预处理

数据的预处理包括了对缺失值的处理和数据的正则化。

z分数（Z-score）标准化就是标准分数。它是一个数与平均数的差再除以标准差的过程。

把每一个数都转换成z分数，那么每一个z分数会以标准差为单位表示一个具体分数到平均数的距离或离差。

归根结底都是为了加快模型的训练速度。

然后根据3-7分为测试机和训练集。

## 模型选择

我在通过各个模型在训练集上的交叉验证得分来选出契合度更高的模型。

分别测试了4个模型，有k近邻、逻辑回归、随机森林、提升计策树。它们的准确度分别是64%、67%、86%、89%

因为提升决策树的交叉验证准度更高，所以选择提升决策树模型进行超参数优化。

## 超参数优化

我这里是使用了穷举网格搜索参数优化方式。实际操作就是你输入几个你想优化的参数和该参数的优化范围。然后它会从这个范围中，找到最好的参数值组合。

最后我使用优化好的参数在训练集上训练，之后对测试集进行验证准确率为92%

## 尚未完善部分

在这个数据集有非常多的特征，但是有些特征可能对模型的训练没有益处，通过特征工程，选择对模型训练最有用的特征可能会使得训练出来的模型得到更高的准度。