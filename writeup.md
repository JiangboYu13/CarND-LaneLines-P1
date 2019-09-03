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
To better filter out unwanted colored pixels from image, the original image is first converted to HSL (Hue Saturation and Value) color domain. Then extract white (with high Value and low Saturation) and yellow (with high Value and Hue between 20 and 30) colored pixels; Binarize image by setting successfully passed pixel to (255, 255, 255) and the rest t0 (0, 0, 0)

* Convert image to grayscale;

![grayscale][grayscale]


* Apply Gaussian filter with kernle size 5;

![gaussian][gaussian]

* Apply Canny edge filter withlow_threshold 50 and high_threshold 150;

![canny][canny]

* Apply Region of Interest filter (the vertices of ROI are based on ratios of height and width rather than fixed values);

![roi][roi]

* Apply Hough lane detection algorithm with rho=1, theta=pi/180, threshold = 30, min_line_length = 20,  max_line_gap = 5;

![hough][hough]

* Filter out unwanted lines and average and/or extrapolate the line segments; (This part is what I've done for modifying draw_lines)
	1. The theta and rho of each found lines are calculated
	2. Remove lines of unwanted theta value (vertical and horizontal line for example)
	3. average the theta and rho of similar line segements;
	4. calculate the x-coordinates for two end of each line (wiith y-coordinates take value of height and upper boundary of ROI)
![fused][fused]

* Final Result

![weighted_overlap][weighted_overlap]


### 2. Identify potential shortcomings with your current pipeline

When choose parameters for algorithm, I have to trade-off between the identification rate and identification precision. For example, by increasing the *threshold* of hough algorithm, there will be less probability to take other objects other than traffic lanes as lanes. However, it increases the probability of missing traffic lanes. My implementation has a reasonable performance on *solidWhiteRight.mp4* and *solidYellowLeft.mp4* but occasionally will miss lanes in *challenge.mp4*, especially these frames taken under tree shadows.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to implement a generalized hough transform for lane detection. Traditional hough transform can deal with straight line but not curve lines, which is common on road;

