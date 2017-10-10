# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 
1. I convert the original colorful image to gray image for the next Canny Edge detection.
2. Before implementing Canny Edge detection, I use gaussian smoothing to eliminate some noise points and makes the edge clearer.
3. Now canny edge detection comes into picture. I carefully find the suitable two
parameters low_threshold=50 and high_threshold=150, which depends on lots of trying. 
4. Only part of visual field we should care for my Line Edge Detection. So I carefully designed trapezoid vertices to mask with the reults of Canny Edge Detection.
5. Based on detected edges, I use Hough Transformation to find the real left line and right line. Also, I pay much attention on the parameters fine-tuning so that I could get a considerable result. 
6. Then I visulize the orginal image and the detected edges. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 2 steps:

1. I calculate the slope to judge which group the segmented line should belong, i.e. 
left line Group or right line Group.
2. Then for each group, let the left line group be an example, I find two key points. Onhe
point has the minimum value of X coordinate, and another the maximum value of X coordinate.
3. After finding these two points, I draw a line using the detected two points as the end points.

<!--
[alt text][image1]
-->


### 2. Identify potential shortcomings with your current pipeline


1. One potential vital shortcoming would be what would happen when there is no left line group or right line group is detected, my codes cannot run and alert an error. 

2. I use a pre-designed trapezoid region which is very suitble for the test images and videos. But it fully failed on the challenge duet to the road line is not in the pre-designed trapezoid.



### 3. Suggest possible improvements to your pipeline

1. Improve the robust of the shape pre-designed region, mayebe it should be adaptive.


