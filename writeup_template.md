# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I run a gausian blur with a kernal size of 5. This is followed by running a canny transform with a low threshold of 50 and a high threshold of 150. The region of interest (ROI) is defined and a hough transform is used to detect the lane lines. The lane lines are then overlaid onto the orignal image 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calualting the slope of the lines. Using the slope I discarded lines that did not fall into a cretain range and used it to filter the lines into right and left lines depending on if they had positive or negative slope. The remaining lines were then average to create average right and left lines, these lines are then extrapolated so they intersect with the ROI. These two lines are then returned.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lane lines are too curved to be detected by the range defined in draw lines. 

Another shortcoming could be the tracking of the yellow lane line in the challange video.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to try fitting the lane lines to a polynomial rather than a simple straight line.

Another potential improvement could be to apply a mask to the image before processing to increase the contrast between the yellow pixels and the surroundings.
