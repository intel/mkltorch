DISCONTINUATION OF PROJECT.

This project will no longer be maintained by Intel.

Intel has ceased development and contributions including, but not limited to, maintenance, bug fixes, new releases, or updates, to this project. 

Intel no longer accepts patches to this project.

If you have an ongoing need to use this project, are interested in independently developing it, or would like to maintain patches for the open source software community, please create your own fork of this project. 
**mkltorch**
=================
MKLDNN library is designed to accelerate Deep Neural Network(DNN) 
computation on CPU, in particular Intel® Xeon processors (HSW, 
BDW, Xeon Phi). The repo of mkltorch provides mklTensor to be called
 in MKLDNN library in [Torch7](http://torch.ch) for convenience .
# Relation with torch
__Torch__ is the main package in [Torch7](https://github.com/torch/torch7) where data structures for 
multi-dimensional tensors and mathematical operationsover these are 
defined. Additionally, it provides many utilities for accessing files,
 serializing objects of arbitrary types and other useful utilities.

__mklTorch__ wraps the data structure of tensor which is provided by
__Torch__ to offer a new tensor which is named as mklTensor. It is 
necessary to convert the regular tensor to mklTensor if you want to 
use MKLDNN to boost your neural networksi computation.

If there is a regular tensor variable named as a, you can call its mkl() 
method and you will get the corresponding mklTensor. It is not very hard.
```lua
require 'mkltorch'
a = torch.FloatTensor(2,3)
b = a:mkl()
```   
Accordingly, it is easy to convert a mklTensor to a regular tensor just 
by using th() method. Just like:
```lua
require 'mkltorch'
a = torch.FloatTensor(2,3)
b = a:mkl()
c = b:th()
```   
__NOTE:__ 

  * mklTensor doesn't provide any basic mathematical operations. You can 
transfer it to a regular tensor first then operate it if necessary.
  * Any convertions only occur between the two types tensors which have
 same data type.In other word, a regular tensor with float type only can 
be converted to MKLFloatTensor. It is impossible to convert it to a MKLDoubleTensor.
  * There are only two type data structures of mklTensor(float and double)
 currently.   

## mklTensor Library ##
It offers mklTensor some basic operations to create, copy, convert or query some infos.
   * new()               
     create a new mklTensor and return it.
   * th()                
     convert a mklTensor to the regular tensor and return the regular tensor. 
   * float()             
     convert a MKLFloatTensor to the regular float tensor and return the regular float tensor.
   * double()            
     convert a MKLDoubleTensor to the regular double tensor and return the regular double tensor.
   * MKL2TH(A)           
     convert a mklTensor to the regular tensor and return the regular tensor. And also assigned it to A
   * TH2MKL(A)           
     convert a regular tensor A to the mklTensor and return the mklTensor. 
   * nElement()          
     Return the ammount of the mklTensor.
   * directTH()          
     fetch the tensor from a MKLFloatTensor. It is __NOT__ recommended to use this method by user
     in order to avoid potential problems.
   * size([dim])         
     Returns the size of the specified dimension dim or the sizes of all dimensions if param dim is ignored.        


The package also provide a regular tensor conversion methods to get the corresponding mklTensor.
   * mkl()               
     convert a regular tensor to the mklTensor and return the mklTensor.
   * mklFloat()          
     convert a regular float tensor to the MKLFloatTensor and return the MKLFloatTensor.
   * mklDouble()         
     convert a regular double tensor to the MKLDoubleTensor and return the MKLDoubleTensor.

__NOTE:__
 
 If you have any confusion about these repo, please contact us and help us improve this readme. 
## How to contribute to these repo
You should have confidence that the gap of performance between CPU and GPU is not that huge exaggeratively.
join us and let your CPU speedup. You can pull request to the repo to help us improve it.


