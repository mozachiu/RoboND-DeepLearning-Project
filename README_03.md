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
[image2]: ./Image/2.png
[image3]: ./Image/3.png
[image4]: ./Image/4.png
[image5]: ./Image/3ll.png
[image6]: ./Image/4ll.png
[image7]: ./Image/13.png
[image8]: ./Image/3l0.png
[image9]: ./Image/3l.png
[image10]: ./Image/4l0.png
[image11]: ./Image/4l.png
[image12]: ./Image/4l1.png
[image13]: ./Image/3l1.png
[image14]: ./Image/lr001.png
[image15]: ./Image/lr001_1.png
[image16]: ./Image/lr001_s.png
[image17]: ./Image/bs01.png
[image18]: ./Image/bs02.png
[image19]: ./Image/bs03.png
[image20]: ./Image/ne1_1.png
[image21]: ./Image/ne1_2.png
[image22]: ./Image/ne1_3.png
[image23]: ./Image/ne2_1.png
[image24]: ./Image/ne2_2.png
[image25]: ./Image/ne2_3.png
[image26]: ./Image/FCN1.png


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

(3)Detailed diagram of all the layers

![alt text][image26]  

C1 – C7 : separable convolution layers

U1 – U3 : upsampling layers

U1 upsample the L4 layer and combine it with the input of the L3 layer C3.
U2 upsample the L5 layer and combine it with the input of the L2 layer C2.
U3 upsample the L6 layer and combine it with the input of the L1 layer C1.
  
#### 2. Explain their neural network parameters including the values selected and how these values were obtained.
I have tried different setting to observe the result of score.

(1)Pair of encoder/decoder block:

Using the Hyperparameters as below:

![alt text][image7]

3 Pair of encoder/decoder block:

![alt text][image5]

![alt text][image8]

![alt text][image13]

![alt text][image9]

4 Pair of encoder/decoder block:

![alt text][image6]

![alt text][image10]

![alt text][image11]

![alt text][image12]

So 3 pair of encoder/decoder block is better then 4 pair of encoder/decoder block.

(2)Learning Rate


![alt text][image14]

![alt text][image15]

![alt text][image16]

So learning rate of 0.01 is better then learning rate of 0.001.

(3)Batch Size And Number of Epochs

![alt text][image17]

![alt text][image18]

![alt text][image19]

It will take more time to get the result for each step.I may choose lower batch size and didn't impact the final result too much.

![alt text][image20]

![alt text][image21]

![alt text][image22]

![alt text][image23]

![alt text][image24]

![alt text][image25]

The larger epochs would let the model start to overfit and get bad performance in the validation set. Tuning the best balance between batch size number of epochs may get better score.

(4)Dicuss more hyperparameters as below:

**Learning Rate**

The learning rate defines how quickly a network updates its parameters.
Low learning rate slows down the learning process but converges smoothly. Larger learning rate speeds up the learning but may not converge.

Usually a decaying Learning rate is preferred.

**Number of epochs**

Number of epochs is the number of times the whole training data is shown to the network while training.
One forward pass and one backward pass of all the training examples

Increase the number of epochs until the validation accuracy starts decreasing even when training accuracy is increasing(overfitting).

**Batch size**

Batch size is the number of training examples in one forward/backward pass. The higher the batch size, the more memory space you'll need.

**Number of Workers**

Number of Workers is the Number of executors to a Spark job in distributed deep neural network training. Split the data  to each worker and  let them process fewer records. Adding more workers will result in a diminishing return on investment, in terms if accuracy obtainable per unit time for training.

**Validation Set Size**

The validation set is the sample of data used to evaluate a model which provide an unbiased evaluation fit on the training dataset. Using a validation set is a good way to avoid the model from learning from the test set. People tend to set more than 30,000 example for validation that make accuracy have enough resolution to see small improvements.

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


The model was trained with labeled examples only target person and other people, any other object (dog, cat, car, etc.) instead of a human would not work well. It is necessary to label different object and train it as new model again.

#### 6. Future Enhancement

(1) Add Regularization:

Add  regularization will help to prevent overfitting and reduce the error in the network. Training neural network is a high variance problem such that need more reliable training data. Sometimes it’s hard to do this. By adding  regularization such as L2  regularization to the logistic regression is good at such time.

(2) Add Dropout:

Add Dropout is the other way to  prevent overfitting when training neural network. To do this, go through each of the layer of the network add some probability of eliminating a node in  neural network.
