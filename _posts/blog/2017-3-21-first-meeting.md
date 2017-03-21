---
layout: post
title:  "Object Detection 综述"      
category: notes
author: "孟文霞"

---

**声明**：文中的内容主要是基于个人理解，难免有错误的地方，如有不当之处敬请指出，我的邮箱是[[mengwenxia16@mails.usac.ac.cn]](mengwenxia16@mails.usac.ac.cn)

## CNN卷积方式
神经网络的基础入门和卷积的基本方式参考台湾大学李宏毅教授的讲义：[[deep learning.pdf]](/images/blog/2017-3-21/deep learning.pdf)    
卷积的动态过程见cs231n的一个动态图：[[http://cs231n.github.io/assets/conv-demo/index.html]](http://cs231n.github.io/assets/conv-demo/index.html)    

### 注意
* 卷积过程中Filter的层数与原数据层数相同
* Polling的方式可以max、average or 自己设计其他的方式
* Filter的选取也经历了许多变化的过程，从Alexnet的11×11，到VGG、SSD的3×3。

## 常见的网络

## Alexnet
**原文**：[[ImageNet Classification with Deep Convolutional Neural Networks]](http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)      

**摘要**：We trained a large, deep convolutional neural network to classify the 1.2 million
high-resolution images in the ImageNet LSVRC-2010 contest into the 1000 different
classes. On the test data, we achieved top-1 and top-5 error rates of 37.5%
and 17.0% which is considerably better than the previous state-of-the-art. The
neural network, which has 60 million parameters and 650,000 neurons, consists
of five convolutional layers, some of which are followed by max-pooling layers,
and three fully-connected layers with a final 1000-way softmax. To make training
faster, we used non-saturating neurons and a very efficient GPU implementation
of the convolution operation. To reduce overfitting in the fully-connected
layers we employed a recently-developed regularization method called “dropout”
that proved to be very effective. We also entered a variant of this model in the
ILSVRC-2012 competition and achieved a winning top-5 test error rate of 15.3%,
compared to 26.2% achieved by the second-best entry.    


**特点**：使用了GPU和dropout，网络结构如下图：    
![alexnet](/images/blog/2017-3-21/2.jpg)

## VGG   
**原文**：[[VERY DEEP CONVOLUTIONAL NETWORKS FOR LARGE-SCALE IMAGE RECOGNITION]](https://arxiv.org/pdf/1409.1556.pdf)    
**摘要**：In this work we investigate the effect of the convolutional network depth on its
accuracy in the large-scale image recognition setting. Our main contribution is
a thorough evaluation of networks of increasing depth using an architecture with
very small (3×3) convolution filters, which shows that a significant improvement
on the prior-art configurations can be achieved by pushing the depth to 16–19
weight layers. These findings were the basis of our ImageNet Challenge 2014
submission, where our team secured the first and the second places in the localisation
and classification tracks respectively. We also show that our representations
generalise well to other datasets, where they achieve state-of-the-art results. We
have made our two best-performing ConvNet models publicly available to facilitate
further research on the use of deep visual representations in computer vision.     

**特点**：使用了3×3的Filter，卷积的层数增加到16-19。    
下图为VGG中用到的模型：       
![VGG](/images/blog/2017-3-21/VGG1.png)   
下图为VGG中的实验结果，其中16-19层的效果最好：
![VGG](/images/blog/2017-3-21/VGG2.png)   



## Roadmap
首先附上krosaen的GitHub上的Deep Learning Papers Reading Roadmap 中Object Detection部分:[[原文地址]](https://github.com/songrotek/Deep-Learning-Papers-Reading-Roadmap/blob/master/README.md)

**[1]** Szegedy, Christian, Alexander Toshev, and Dumitru Erhan. "**Deep neural networks for object detection**." Advances in Neural Information Processing Systems. 2013. [[pdf]](http://papers.nips.cc/paper/5207-deep-neural-networks-for-object-detection.pdf)   

**[2]** Girshick, Ross, et al. "**Rich feature hierarchies for accurate object detection and semantic segmentation**." Proceedings of the IEEE conference on computer vision and pattern recognition. 2014. [[pdf]](http://www.cv-foundation.org/openaccess/content_cvpr_2014/papers/Girshick_Rich_Feature_Hierarchies_2014_CVPR_paper.pdf) **(RCNN)**   

**[3]** He, Kaiming, et al. "**Spatial pyramid pooling in deep convolutional networks for visual recognition**." European Conference on Computer Vision. Springer International Publishing, 2014. [[pdf]](http://arxiv.org/pdf/1406.4729) **(SPPNet)**  

**[4]** Girshick, Ross. "**Fast r-cnn**." Proceedings of the IEEE International Conference on Computer Vision. 2015. [[pdf]](https://pdfs.semanticscholar.org/8f67/64a59f0d17081f2a2a9d06f4ed1cdea1a0ad.pdf)   
**[5]** Ren, Shaoqing, et al. "**Faster R-CNN: Towards real-time object detection with region proposal networks**." Advances in neural information processing systems. 2015. [[pdf]](http://papers.nips.cc/paper/5638-analysis-of-variational-bayesian-latent-dirichlet-allocation-weaker-sparsity-than-map.pdf)  

**[6]** Redmon, Joseph, et al. "**You only look once: Unified, real-time object detection**." arXiv preprint arXiv:1506.02640 (2015). [[pdf]](http://homes.cs.washington.edu/~ali/papers/YOLO.pdf) **(YOLO,Oustanding Work, really practical)**   

**[7]** Liu, Wei, et al. "**SSD: Single Shot MultiBox Detector**." arXiv preprint arXiv:1512.02325 (2015). [[pdf]](http://arxiv.org/pdf/1512.02325)   

**[8]** Dai, Jifeng, et al. "**R-FCN: Object Detection via
Region-based Fully Convolutional Networks**." arXiv preprint arXiv:1605.06409 (2016). [[pdf]](https://arxiv.org/abs/1605.06409)   


## Object Detection
Object Detection主要解决的问题是What and Where：   
![1](/images/blog/2017-3-21/1.png)

