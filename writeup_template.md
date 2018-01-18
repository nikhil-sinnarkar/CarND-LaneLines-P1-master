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

* The edges are detected using canny edge detection algorithm.

![canny](./md%20resources/solidWhiteRight_canny.jpg)

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
