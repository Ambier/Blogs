# Deep Learning Face Representation by Joint Identification-Verification






































 考察目标函数融合参数lambda的效果，包括最终效果分析、方差分析、PCA降至2维时的数据分析。
 考察信息量的影响，即通过变换训练集的大小（32指数增长到8192），查看效果。
 改变用于验证的目标函数即Verif的距离计算方法后的实验效果。考察了一阶范数、余弦距离等。
 选取了七组不同的特征集合，然后将模型使用svm进行融合，得到最终结果99.15%。

