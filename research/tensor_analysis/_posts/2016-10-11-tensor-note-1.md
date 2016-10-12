---
layout: post
header: just_img_header
title: Tensor Decomposition is a Feature Learning Method

header_image: tensor.png
abstract: Notes and ideas
---

There are no good python libraries for tensor analysis, see [this Quora post](https://www.quora.com/What-are-the-good-open-source-libraries-in-Python-or-R-for-Tensor-methods-Does-your-team-maintain-any).

TensorFlow has some basic operations on Tensors, see [this introduction](https://www.tensorflow.org/versions/r0.11/resources/dims_types.html)

I haven't tried TensorFlow nor [tensor-analysis](https://pypi.python.org/pypi/tensor-analysis), nor [TensorLib by CMU](https://code.google.com/archive/p/pytensor/downloads). The last one was developped in 2009 and there is no more updates. 

I used [scikit-tensor](https://github.com/mnick/scikit-tensor) to analysis a sensory bread data. The description of the data is as follows:

> The data are arranged in a three-way array (10 breads × 11 attributes × 8 judges). Also available is the salt content of the ten samples. A PARAFAC model can be seen as a reasonable approximate model incorporating saliencies for each assessor, but there is no hard theory stating the nature of the data. The data are quite noisy compared to, e.g., spectral data. The data are usually centered across the sample mode before fitting the model. This centering removes the assessor specific offsets on the attribute scales. Scaling of the data is an issue where no consensus has yet been achieved.

The code is :

{% highlight python %}

import logging
from scipy.io.matlab import loadmat
from sktensor import dtensor, cp_als

logging.basicConfig(level=logging.DEBUG)

mat = loadmat('brod.mat')
T = dtensor(mat['X'])

P, fit, itr, exectimes = cp_als(T, 3, init='random')
P.U[0].shape
P.U[1].shape
P.shape
# (10, 88)

{% endhighlight %}


This [slide](http://www.slideshare.net/panisson/exploring-temporal-graph-data-with-python-a-study-on-tensor-decomposition-of-wearable-sensor-data) has a good introduction on tensors with python code. It also explains the tensor rank. 

![tensor1](/image/tensor_decomposition1.png)

![tensor2](/image/tensor_decomposition3.png)

This formulation is very similar to sparse coding, which is a feature learning algorithm. So I think the tensor decomposition is a feature learning method.

