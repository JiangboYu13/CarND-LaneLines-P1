# **Finding Lane Lines on the Road** 



**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[color_filter]: ./test_images_output_color_filtered/solidYellowCurve2.jpg 
[grayscale]: ./test_images_output_gray/solidYellowCurve2.jpg 
[gaussian]: ./test_images_output_gauss/solidYellowCurve2.jpg 
[canny]: ./test_images_output_canny/solidYellowCurve2.jpg 
[roi]: ./test_images_output_roi/solidYellowCurve2.jpg 
[hough]: ./test_images_output_seg/solidYellowCurve2.jpg
[fused]: ./test_images_output_final/solidYellowCurve2.jpg
[weighted_overlap]: ./test_images_output/solidYellowCurve2.jpg
---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My algorithm consists of the following steps: 

* Apply color filter to extract white and yellow color;

![color_filter][color_filter]

* Convert image to grayscale;

![grayscale][grayscale]

* Apply Gaussian filter;

![gaussian][gaussian]

* Apply Canny edge filter;

![canny][canny]

* Apply Region of Interest filter;

![roi][roi]

* Apply Hough lane detection algorithm;

![hough][hough]

* Filter out unwanted lines and average and/or extrapolate the line segments;

![fused][fused]

* Final Result

![weighted_overlap][weighted_overlap]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
