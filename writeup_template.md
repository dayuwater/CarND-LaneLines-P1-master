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
    * Assign the first detected line into a group
    * For all subsequent lines, if the slope of that line is within 0.1 of the first line in a line group, assign that line into the group. Otherwise, add the line into a new line group
    * Each line can only be in 1 line group
* Sort the line groups from the group with the largest total line length to the group with the shortest total line length
* Calculate the aggregated slope using linear regression (np.polyfit)
* Start from the first element in the sorted group, choose 2 lines that fulfills the following criteria:
    * The absolute value of slope is between 0.5 and 0.85
    * The slopes of the two lines must be in different sign
* Calculate the intercept of two selected lines. Draw them on the picture/video



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
