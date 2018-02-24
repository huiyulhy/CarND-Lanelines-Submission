# CarND-Lanelines-Submission

## **Finding Lane Lines on the Road** 

This write-up contains a reflection of the algorithm in the first assignment used for lane detection, based on different methods of lane detection taught in the "Computer Vision Fundamentals" lesson 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work via this Readme

---

### Reflection

### 1. Describe the pipeline. As part of the description, explain how you modified the draw_lines() function.

In the Jupyter notebook, a function called pipeline was created. This function takes in an image array as input, and outputs the final image from the pipeline, which is an image of the detected lane edges, as well as the extrapolated lane lines, superposed onto the original image. 

My pipeline consisted of 5 steps:

1. Apply a colored mask to filter possible colors of the lane, and output this image for the next step
2. Apply a region mask to localize the areas in which a lane could be detected 
3. Convert the output from Step 1 to grayscale, then ...
4. 
5. 
6. Using the output from draw_lines() and the modified image with the detected lane images, I then used the weighted_image function to obtain the superposed image, which was the final output of the pipeline. 

### 2. Identify potential shortcomings with your current pipeline

There are several shortcomings identified from this current pipeline. 

First, as the basis of this pipeline was a color mask, this would limit t

Second, as a region filter was used, this would reduce the robustness of the detection algorithm during the lane change, the relative position of the lanes to the image would shift when the driver is performing the lane change. As a result, the position of lanes could be mis-identified. 

Third, cracks on the road surface were also identified as lane lines, due to the contrast/edges observed in cracks. This resulted in noise from the neighboring 

### 3. Suggest possible improvements to your pipeline

In light of the shortcomings identified earlier, there are a couple of improvements that could be made to strengthen the robustness of the algorithm. 

First, 
Another potential improvement could be to ...
