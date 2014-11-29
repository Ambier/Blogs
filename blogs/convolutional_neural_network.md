# 卷积神经网络


 第一点，在学习Deep learning和CNN之前，总以为它们是很了不得的知识，总以为它们能解决很多问题，学习了之后，才知道它们不过与其他机器学习算法如svm等相似，仍然可以把它当做一个分类器，仍然可以像使用一个黑盒子那样使用它。

 第二点，Deep Learning强大的地方就是可以利用网络中间某一层的输出当做是数据的另一种表达，从而可以将其认为是经过网络学习到的特征。基于该特征，可以进行进一步的相似度比较等。

 第三点，Deep Learning算法能够有效的关键其实是大规模的数据，这一点原因在于每个DL都有众多的参数，少量数据无法将参数训练充分。























![equal](https://raw.githubusercontent.com/stdcoutzyx/Paper_Read/master/blogs/imgs/8.png)

![equal](https://raw.githubusercontent.com/stdcoutzyx/Paper_Read/master/blogs/imgs/9.png)











 输入：224×224大小的图片，3通道
 第一层卷积：5×5大小的卷积核96个，每个GPU上48个。
 第一层max-pooling：2×2的核。
 第二层卷积：3×3卷积核256个，每个GPU上128个。
 第二层max-pooling：2×2的核。
 第三层卷积：与上一层是全连接，3*3的卷积核384个。分到两个GPU上个192个。
 第四层卷积：3×3的卷积核384个，两个GPU各192个。该层与上一层连接没有经过pooling层。
 第五层卷积：3×3的卷积核256个，两个GPU上个128个。
 第五层max-pooling：2×2的核。
 第一层全连接：4096维，将第五层max-pooling的输出连接成为一个一维向量，作为该层的输入。
 第二层全连接：4096维
 Softmax层：输出为1000，输出的每一维都是图片属于该类别的概率。






 [1] 	http://deeplearning.stanford.edu/wiki/index.php/UFLDL%E6%95%99%E7%A8%8B 栀子花对Stanford深度学习研究团队的深度学习教程的翻译
 [2] 	http://blog.csdn.net/zouxy09/article/details/14222605 csdn博主zouxy09深度学习教程系列
 [3] 	http://deeplearning.net/tutorial/ theano实现deep learning
 [4] 	Krizhevsky A, Sutskever I, Hinton G E. Imagenet classification with deep convolutional neural networks[C]//Advances in neural information processing systems. 2012: 1097-1105.
 [5] 	Sun Y, Wang X, Tang X. Deep learning face representation from predicting 10,000 classes[C]//Computer Vision and Pattern Recognition (CVPR), 2014 IEEE Conference on. IEEE, 2014: 1891-1898.