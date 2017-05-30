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

* When the lane color is not white, the lane segment detected is broken on a solid lane
* When the first detected line segment is far from the camera, the line detection is a little off. (0:06 in solidWhite video)
* Does not adapt the region of interest according to the picture. The left and right line detection will go wrong if the region of interest is much smaller because the road changes direction (see the output of the challenge video) 
* When the background color of the road is close to white, the lane detection using this pipeline fails. (See 0:04 in the challenge video)
* This could potentially fail if the car is in middle lanes where both left and right lines are not solid.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to sort the line group by the absolute value of aggregate slope (more slope = closer to center)

Another potential improvement could be to determine the region of interest based on the curvature of the road

This can also be improved by determine the threshold of Canny Edge Detection based on the background color of the road
