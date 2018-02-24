# CarND-Lanelines-Submission

## **Finding Lane Lines on the Road** 

### This write-up contains a reflection of the algorithm in the first assignment used for lane detection, based on different methods of lane detection taught in the "Computer Vision Fundamentals" lesson 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work via this Readme


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe the pipeline. As part of the description, explain how you modified the draw_lines() function.

In the Jupyter notebook, a function called pipeline was created. This function takes in an image array as input, and outputs the final image from the pipeline, which is an image of the detected lane edges, as well as the extrapolated lane lines, superposed onto the original image. 

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

There are several shortcomings identified from this current pipeline. 

First, 

Second, 

### 3. Suggest possible improvements to your pipeline

In light of the shortcomings identified earlier, there are a couple of improvements that could be made to strengthen the robustness of the algorithm. 

First, 
Another potential improvement could be to ...
