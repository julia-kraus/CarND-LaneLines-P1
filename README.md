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
[20, 100, 100] and a high threshold of [30, 255, 255]. White things were easy to distinguish in RGB color space with a low threshold of and a high threshold of [220, 220, 220] and a high threshold of [255, 255, 255]. We combine the yellow and white mask bitwise to obtain the output , which is an image that is black except for its yellow and white patches. 

### Grayscaling
Next the output of the color selection to grayscale. This helps for a higher contrast of the lines in the otherwise black image. Moreover, we won't have to deal with three color channels anymore, which reduces complexity.

### Region of interest.
Next, I selected a region of interest around the lane lines. Therefore, we assume that the camera is centered, and the road has always about the same with. We select a triangular area and color in the grayscaled image everything outside this triangular area in black.

### Gaussian blur
Our next task is to extract the lane lines from the image. Gaussian blur 
A kernel size of three gave good results.

### 

Shortcomings
---
The lane detector works really well on the images, but not always well on the videos, especially when the lane lines are not continuous. When the detected lanes are too short, the gradient in the lane interpolation step is not always accurate and so the slope of the line is wrong

Possible Improvements
---
The above issue might be addressed by giving the algorithm memory. One can assume that subsequent frames in a video look about the same, i.e. have similar lane lines. If that is true, one could conclude from previous frames to following ones and use the previous lane line parameters again for averaging over the new frame's parameters.



We encourage using images in your writeup to demonstrate how your pipeline works.  

All that said, please be concise!  We're not looking for you to write a book here: just a brief description.
 



