# **Finding Lane Lines on the Road**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)
<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Identifying lanes on the road is a common task performed by all human drivers to ensure their vehicles are within lane constraints when driving, so as to make sure traffic is smooth and minimize chances of collisions with other cars due to lane misalignment.

Similarly, it is a critical task for an autonomous vehicle to perform. It turns out that recognizing lane markings on roads is possible using well known computer vision techniques. Some of those techniques will be covered below.

The goal of this project, the first Term 1 of the Udacity Self Driving Car Engineer Nanodegree, is to create a pipeline that finds lane lines on the road.

Setup
---

Udacity provided sample images of size 960 x 540 pixels for training our pipeline. There are pictures with yellow and white lane lines. Below, you can see two example pictures


To meet specifications in the project, take a look at the requirements in the [project rubric](https://review.udacity.com/#!/rubrics/322/view)

Lane Detection Pipeline
---
The pipeline defined in the function `detect lane line` consisted of the following steps:
1. Color selection
  1. Yellow -> convert picture to HSV color space
  1. White -> select white patches in RGB color space
1. Grayscaling
1. Select triangular region of interest
1. Gaussian Blur
1. Canny Edge Detection
1. Hough Transformation
1. Lane line interpolation:
  1. Separate left and right lines
  1. Create average, continuous lane out of Hough lines using linear Regression

### Color Selection
In the first step I isolated yellow and white regions from the image. It was hard to detect yellow regions in RGB color space, so I converted the picture into the HSV color space. There I could distinguish yellow things with a low threshold of 
[20, 100, 100] and a high threshold of [30, 255, 255]. White things were easy to distinguish in H

### Grayscaling
Next, 

Creating a Great Writeup
---
For this project, a great writeup should provide a detailed response to the "Reflection" section of the [project rubric](https://review.udacity.com/#!/rubrics/322/view). There are three parts to the reflection:

1. Describe the pipeline

2. Identify any shortcomings

3. Suggest possible improvements

We encourage using images in your writeup to demonstrate how your pipeline works.  

All that said, please be concise!  We're not looking for you to write a book here: just a brief description.

You're not required to use markdown for your writeup.  If you use another method please just submit a pdf of your writeup. Here is a link to a [writeup template file](https://github.com/udacity/CarND-LaneLines-P1/blob/master/writeup_template.md). 



