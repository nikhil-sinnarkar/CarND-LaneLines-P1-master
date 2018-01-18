# **Finding Lane Lines on the Road** 

## Writeup

### This is a writeup for the project to find lane lines on the road and highlight them.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on the work in a written report


[//]: # (Image References)

[gray]: ./md%20resources/solidWhiteRight_gray.jpg

---

### Reflection

### 1. Pipeline description.

The pipeline I have developed consists of 6 steps.

* First I read the image and converted it to grayscale.

![alt text][gray]

* Gaussian blur is applied to grayscaled image.

* The edges are detected using canny edge detection algorithm. The result is an image with only edges.

![canny](./md%20resources/solidWhiteRight_canny.jpg)

* Next I created a region of interest and applied it over the image shown above. In the output I got an image with only the necessary information i.e. lane lines.

![masked](./md%20resources/solidWhiteRight_masked.jpg)

* In order to find out the all the x,y coordinates that belong to the lane lines I took a hough transform of this image. The hough transform provided the coordinates of start & end point of all the lines that are detected in the image. 
Lines corresponding to left and right lanes are identified and drawn (more info on drawing lines below). 
The output is as shown here.

![hough](./md%20resources/solidWhiteRight_hough.jpg)

* This image is overlayed on top of original image to highlight the lanes which are detected. :smiley: The result is :

![final](./md%20resources/solidWhiteRight.jpg)


#### Modifications to draw_lines() function
This is how I modified the draw_lines() function in order to draw a single line on the left and right lanes.

First I seperated the points into 2 groups, one for points on left lane and other for points on right lane.

Next, using `polyfit()`, I found the cofficients of a first order polynomial equation that would fit all the points for each lane.
Using these cofficients I was able to model a single line for both left and right lanes as  
**y = Ax + B**

In this equation I put the y coordinates of my Region of interest to obtain x values. I pass these values to `cv2.line()` to draw a single lane line.


### 2. Potential shortcomings with the current pipeline


The threshold values for canny edge detection and hough transform are set manually so the pipeline may not be able to identify lanes under different lighting conditions.

The boundaries of Region of interest are also set manually. These may not work for 
  1. Images having different resolution (width, height) and  
  2. Changes in camera orientation. For eg. if camera is pointed slightly upwards.

### 3. Possible improvements to the pipeline

To modify the pipeline to also detect curved lane lines.

To smooth out the lane detection by averaging the values detected in previous frames of the video.
