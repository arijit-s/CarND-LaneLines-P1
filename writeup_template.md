# **Finding Lane Lines on the Road** 

## Project Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[cannyimage]: ./examples/cannyimage.jpg?raw=true "CannyImage"
[houghimage]: ./examples/houghimage.jpg?raw=true "HoughImage"
[finalimage]: ./examples/finalimage.jpg?raw=true "FinalImage"
---

### Reflection

### 1. Describing the pipeline. As part of the description, explain how you modified the draw_lines() function.

The goal of the pipeline is to detect lane lines and mark them. My pipeline consisted of 5 steps. First, I converted the images to grayscale as hough transform only works in grayscale, then I applied gaussian filter to remove any unwanted noise. After that I applied canny edge detection algorith to detect the edges in the image. The image with edges will look like below.

![Canny Edge][examples/cannyimage.jpg?raw=true]

Once all the edges have been detected in the image, I marked a region where the lane lines will possibly belong and I applied hough transform technique to detect straight lines from that particular region.

![Hough Transformation][houghimage]


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by identifying line segmentations from hough transformation, which lines belong to left side of the lane and which are right. I calculated the slope of the lines, if it is positive, then the line belongs to left lane, if slope is negative, it belong to right line.

After that I identified the minimum and maximum value of x and y and drew a line using cv2.line, connecting minimum point to maximum point for both the lanes. The final image will look like below.

![Lane lines][finalimage]



### 2. Identify potential shortcomings with the current pipeline


One potential shortcoming would be what would happen when the hough transform could not detect any lines in any particular image or image frame. 

Another shortcoming could be ...


### 3. Suggestion of possible improvements to the pipeline

A possible improvement would be to handle situation where there are shadows on the road or the lane lines are not perfectly visible.

Another potential improvement could be to detect lane lines which are curved.
