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

[image1]: ./Image/1.png


## [Rubric](https://review.udacity.com/#!/rubrics/1155/view) Points
---

#### 1. Explain each layer of the network architecture and the role that it plays in the overall network. 

#### 2. Explain their neural network parameters including the values selected and how these values were obtained.

#### 3. Demonstrate a clear understanding of 1 by 1 convolutions and where/when/how it should be used. 

#### 4. Identify the use of various reasons for encoding / decoding images, when it should be used, why it is useful, and any problems that may arise.

#### 5. Clearly articulate whether this model and data would work well for following another object (dog, cat, car, etc.) instead of a human and if not, what changes would be required. 

### Notebook Analysis
#### 1. Run the functions provided in the notebook on test images (first with the test data provided, next on data you have recorded). Add/modify functions to allow for color selection of obstacles and rock samples.

The test data provided.

![alt text][image1]
 * “Fully Convolutional Networks for Semantic Segmentation”, by Long, Shelhamer, and Darrell, all at UC Berkeley.


In the function `process_image()`: 
1. Call function `perspect_transform()` return warp and mask.
