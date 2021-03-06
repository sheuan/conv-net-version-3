#conv-net-version-3.0
=====================

Newly implemented convnet (C++ / OpenCV).

This is an **EARLY ADOPTERS EDITION**, which is still buggy, I'll post formal version in days.

To run this code, you should have 
* a cifar-10 dataset( put "cifar-10-batches-bin" where this .md file is, you can get it from [HERE](http://www.cs.toronto.edu/~kriz/cifar.html), make sure to download the binary version which suitable for C programs);
* OpenCV.

##Compile & Run

* Compile: "cmake CMakeLists.txt" and then "make" 
 
* Run: "./conv" 

* Clean log files: "./conv clean_log"

##Updates 

* 3-channels images supported.
* Add Dropout;
* In conv layers, one can use either 3-channel conv kernels or single-chanel conv kernels (that is to say, whether share weights).
* Local Response Normalization supported.
* Use log files dig deeper.
* Use second order derivative back-prop to alter learning rate (unfinished).

##File description 

* **channel_3.h & channel_3.cc** - functions dealing with 3-channels matrices

* **convolution.h & convolution.cc** - convolution / pooling / local response normalization implementations

* **cost_gradient.h & cost_gradient.cc** - function which calculates the cost function and gradients given data and weights of each layer

* **gradient_checking.h & gradient_checking.cc** - gradient checking functions. (You may want to disable dropout during gradient checking.)

* **helper.h & helper.cc** - tiny helper functions

* **matrix_maths.h & matrix_maths.cc** - matrix maths functions, such as conv2() and rot90()

* **read_data.h & read_data.cc** - this read_data supports only CIFAR-10 dataset

* **get_sample.h & get_sample.cc** - sample from cv::Mat or vector<Mat> data

* **result_predict.h & result_predict.cc** - functions for result predict

* **save_weights.h & save_weights.cc** - save weights into .txt file

* **string_proc.h & string_proc.cc** - I'm using unordered_map<string, Mat>, so here are the tedious string processing functions

* **train_network.h & train_network.cc** - using sgd with momentum method

* **weight_init.h & weight_init.cc** - initialize weights of the whole network

* **read_config.h & read_config.cc** - read config file for config parameters, see config file part below

* **general_settings.h** - general settings

* **data_structure.h** - data structure definition of network

* **sample.cc** - main() inside :)

##Config Files

####General Parameters Config
* if is gradient checking
* use or not use log (for debugging, should be faster if not using it)
* batch size
* pooling method
* non-linearity method
* training epochs
* iteration per epoch
* learning rate decay
* learning rate for weight matrices
* learning rate for bias

####Layers Config
* kernel size (in **Convolutional** layers)
* kernel amount (in **Convolutional** layers)
* weight decay (in **Convolutional** layers, **Full-Connected** Layers, **Softmax** Layer)
* pooling dimension (in **Convolutional** layers)
* if to use 3-channel kernel (in **Convolutional** layers)
* if to use local response normalization (in **Convolutional** layers)
* amount of hidden neurons (in **Full-Connected** Layers)
* dropout rate (in **Full-Connected** Layers)
* amount of output classes (in **Softmax** Layer)

####Multi-Layer
If you are using multiple of same kind of layer, just write layer config one after another. There's [an example config file](https://github.com/xingdi-eric-yuan/conv-net-version-3/blob/master/config.txt) inside.

##Structure and Algorithm
See my several posts about CNNs at [my tech-blog](http://eric-yuan.me).

The MIT License (MIT)
------------------

Copyright (c) 2014 Xingdi (Eric) Yuan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.