## Project: Deep Learning Project, Follow-Me 
---


**The goals / steps of this project are the following:**  

**Steps to complete the project:**

* 1.Clone the project repo here

* 2.Fill out the TODO's in the project code as mentioned here

* 3.Optimize your network and hyper-parameters.

* 4.Train your network and achieve an accuracy of 40% (0.40) using the Intersection over Union IoU metric which is final_grade_score at the bottom of your notebook.

* 5.Make a brief writeup report summarizing why you made the choices you did in building the network.


[//]: # (Image References)

[image1]: ./Image/11.png
[image1]: ./Image/2.png
[image1]: ./Image/3.png
[image1]: ./Image/4.png


## [Rubric](https://review.udacity.com/#!/rubrics/1155/view) Points
---

#### 1. Explain each layer of the network architecture and the role that it plays in the overall network. 
FCNs use convolutional layers to classify each pixel in the image to preserve the spatial information throughout the entire network.
All of FCNs layers are convolutional layers, contrast to a classic Convolution Network which are fully-connected layers at the end.

![alt text][image1]

The FCN created in this project contains : 

(1)Encoder Block
  A series of convolutional layers to extract features from the image.

(2)Decoder Block
  Up-scale the output of the encoder such that it's the same size as the original image.
  
#### 2. Explain their neural network parameters including the values selected and how these values were obtained.

#### 3. Demonstrate a clear understanding of 1 by 1 convolutions and where/when/how it should be used. 
To preserve the spatial information, replacing a fully connected layer with one by one convolutional layers which output value with the tensor and remain 4D instead of flattening to 2D.

![alt text][image3]

The number of kernels is equivalent the number of outputs in a fully connected layer. The number of weights in each kernel is equivalent to the number of inputs in the fully connected layer. It acts like a fully connected layer where the number of kernels is equivalent to the number of outputs of a fully connected layer. This turns convolutions into a matrix multiplication with spatial information and works for different input sizes.

#### 4. Identify the use of various reasons for encoding / decoding images, when it should be used, why it is useful, and any problems that may arise.

![alt text][image2]


FCN take advantage of three special techniques :
1. Replace fully connected layers with one by one convolutional layers.
2. Up-sampling through the use of transposed convolutional layers which is a reverse convolution and swap the order of forward and backward passes,
3. The encoding narrow down the scope of picture  thus lost information even if decode it back to the original image size. Skip connections which allow the network to use information from multiple resolution scales and retain the information then the network is able to make more precise segmentation decisions.

![alt text][image4]

As a result the network is able to make more precise segmentation decisions.

FCNs may still lost some detail of the image and it ignore the relationship between pixels and lost consistent with the image.

#### 5. Clearly articulate whether this model and data would work well for following another object (dog, cat, car, etc.) instead of a human and if not, what changes would be required. 



