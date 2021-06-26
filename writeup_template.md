# **Finding Lane Lines on the Road** 

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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to complete this exercise, I implemented the following steps:

* Import the image

* Convert the selected image into grayscale

* Apply Gaussian smoothing and define a kernel size

* Define parameters for Canny

* Apply Canny to the image

* Define the Hough transform parameters to create a blank image to draw the lines on

* Run Hough on edge detected image

* Create a single left and Right line

* Group the lines into the correct left and right allocation

* Average the lines in each group to create a single left and single right line

* Draw the lines onto the original image 

![Initial image][sfiisk/CarND--LaneLines-P1/image_output/initial_img.png]
![Grayscale image][sfiisk/CarND--LaneLines-P1/image_output/grayscale.png]
![Canny image][sfiisk/CarND--LaneLines-P1/image_output/edges.png]
![Masked edges image][sfiisk/CarND--LaneLines-P1/image_output/masked_edges.png]
![Line image][sfiisk/CarND--LaneLines-P1/image_output/line_image.png]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by determining which points belong to the left and right side. 
From these points, we can determine whether the line is trending downwards or upwards. 
We then loop over the points that are detected and assign them based on their slope to the correct left/ right designation. 
With the points collected, the next task was to average the lines into a single line and draw them back to the image. 


For this particular function, I had to research further to understand how to implement the ability to group points and average out a single line from the results.
I found the code and the tutorial of how it works by Matt Hardwick, to be the best source available. 
Rather than copying the code and not truly understanding how it works, I was able to understand why each section works, thanks to the exceptional writeup he provided. 

draw_lines() code was used from - 
[Matt Hardwick](https://medium.com/@mrhwick/simple-lane-detection-with-opencv-bfeb6ae54ec0)






### 2. Identify potential shortcomings with your current pipeline

My current pipeline has the following shortcomings:

* Inability to distinguish lines when the are covered by a shadow
* Lines are hidden by other objects
* Lines change shape quickly



### 3. Suggest possible improvements to your pipeline

To solve some of the issues, I could implement the following:

* HSV color space to identify shadows, or to pick out yellow and white colors. 
* Previous frame averaging 
* Machine learning 
