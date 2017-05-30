# **Finding Lane Lines on the Road** 



---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report




### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
* First, I converted the images to grayscale.
* I used Gaussian blur with a kernel size of 5. 
* Used Canny edge detection with a min threshold of 60 and max threshold of 100
* Defined a region of interest using a trapezoid covers the bottom of the image/video
* Hough Line detection with min line length of 8.

In order to draw the the left and right lines
* Separate lines detected into different groups:
    * 1
    * 2



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
