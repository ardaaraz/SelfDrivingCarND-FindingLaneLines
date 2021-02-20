# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of six steps. First, imported image is converted to the grayscale. Then, the grayscale image is smoothed using Gaussian blur to reduce image noise and details of the image. Then, Canny edge detection algorithm is performed by determining the lower and upper thresholds of the function. Then, the region of interest is determined as a polygon and the part of the image which is marked with this polygon is masked. Then, the Hough transform is applied on the masked section of the image to detect subsections of the left and right lanes. Finally, two solid lines which are obtained by using line fitting technique are drawn on the original image. 

In order to draw a single line on the left and right lanes, draw_lines() function is modified. First of all, left and right lanes data are seperated according to slope of the Hough line segments. Then, line equations (i.e. x = a*y+b) are obtained by performing line fitting technique with left and right lane coordinates. By using region of interest definition, y-coordinates of the solid lane lines are predefined and their x-coordinates are determined by evaluating these equations at given y-coordinates. If there is no data for right or left lane, missing x-coordinates are estimated by using other lane x-coordinates with constant lane width assumption. Finally, the function draws the lines using two data points for each lane on the original image.

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be that the lane detection performance (especially for the right lanes) of the developed pipeline is decreasing when the road is very reflective.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to convert all of the yellow lanes in the region of interest to white before edge detection and then apply Hough transform in order to maximize number of detected line segments of the lanes.
