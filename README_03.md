## Project: Deep Learning Project, Follow-Me 
---


**The goals / steps of this project are the following:**  

**Training / Calibration**  

* Download the simulator and take data in "Training Mode"

**Steps to complete the project:**

* 1.Clone the project repo here

* 2.Fill out the TODO's in the project code as mentioned here

* 3.Optimize your network and hyper-parameters.

* 4.Train your network and achieve an accuracy of 40% (0.40) using the Intersection over Union IoU metric which is final_grade_score at the bottom of your notebook.

* 5.Make a brief writeup report summarizing why you made the choices you did in building the network.


[//]: # (Image References)

[image1]: ./output/test_mapping.jpg


## [Rubric](https://review.udacity.com/#!/rubrics/1155/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  

### Notebook Analysis
#### 1. Run the functions provided in the notebook on test images (first with the test data provided, next on data you have recorded). Add/modify functions to allow for color selection of obstacles and rock samples.

The test data provided.

![alt text][image1]



In the function `process_image()`: 
1. Call function `perspect_transform()` return warp and mask.
