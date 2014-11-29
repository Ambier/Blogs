# Very Deep Convolutional Networks for Large-Scale Image Recognition



 考察在参数总数基本不变的情况下，CNN随着层数的增加，其效果的变化。
 论文中的方法在ILSVRC-2014比赛中获得第二名。
 	+ ILSVRC——ImageNet Large-Scale Visual Recongnition Challenge



 Use smaller receptive window size and smaller stride of the first convolutional layer.
 Training and testing the networks densely over the whole image and over multiple scales.

 CNN的输入都是224×224×3的图片。
 输入前唯一的预处理是减去均值。
 1×1的核可以被看成是输入通道的线性变换。
 使用较多的卷积核大小为3×3。
 Max-Pooling 一般在2×2的像素窗口上做，with stride 2。
 除了最后一层全连接的分类层外，其他层都需要使用rectification non-linearity(RELU)。
 不需要添加Local Response Normalization(LRN)，因为它不提升效果反而会带来计算花费和内存花费，增加计算时间。

 卷积层的通道数目（宽度）从64，每过一个max-pooling层翻倍，到512为止。
 Use filters with 3×3 size throughout the whole net, because a stack of two 3×3 conv layers (without spatial pooling in between) has an effective receptive of 5×5, and three a stack of 3×3 conv layers has a receptive of 7×7, and so on.
 为甚么使用三层3×3代替一层7×7？ 
 使用1*1的卷积核可以在不影响视野域的情况下增加判别函数的非线性。该核可以用于“Network in Network”网络结构，可以参考论文的参考文献12。

 图1是论文中实验使用的神经网络结构，可以看到，CNN的层数从11层到19层，结构符合上面的总结的点。图2则是各个CNN的参数总数，可以看到，虽然深度变化了，但是参数数目变化不大。 





 除了使用multiple scale之外，论文[1]实验基本都follow论文[2]的设置。batch size是256，momentum是0.9，正则化系数是5×10e-4，前两层全连接的dropout参数设置为0.5，学习步长初始化为10e-2，且当验证集结果不再上升时步长除以10，除三次为止。学习了370K迭代(74 epochs)时停止。
 论文推测，本文的网络比原来的网络要更容易收敛，原因有二：
 224×224输入的获得，将原始图片等比例缩放，保证短边大于224，然后随机选择224×224的窗口，为了进一步data augment，还要考虑随机的水平仿射和RGB通道切换。
 Multi-scale Training， 多尺度的意义在于图片中的物体的尺度有变化，多尺度可以更好的识别物体。有两种方法进行多尺度训练。


 首先进行等比例缩放，短边长度Q大于224，Q的意义与S相同，不过S是训练集中的，Q是测试集中的参数。Q不必等于S，相反的，对于一个S，使用多个Q值进行测试，然后去平均会使效果变好。
 然后，按照本文参考文献16的方式对测试数据进行测试。

 使用C++ Caffe toolbox实现










