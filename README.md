# CarND-Lanelines-Submission

## **Finding Lane Lines on the Road** 

This write-up contains a reflection of the algorithm in the first assignment used for lane detection, based on different methods of lane detection taught in the "Computer Vision Fundamentals" lesson. 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work via this Readme

---

### Reflection

### 1. Description of Approach

#### Pipeline Description ####
In the Jupyter notebook, a function called pipeline was created. This function takes in an image array as input, and outputs the final image from the pipeline, which is an image of the detected lane edges, as well as the extrapolated lane lines, superposed onto the original image. The base code for the functions were modified from code taught during the quizzes during the lesson on Computer Vision Fundamentals, while the main function definitions were part of the skeleton code that was provided for this assignment. 

My pipeline consisted of 7 steps:

1. Apply a colored mask to filter possible colors of the lane, and output this image for the next step. For this pipeline, the RGB threshold used was  [0, 120, 120]. Hence, lane colors ranging from red to white could be detected, which is approximately the range of lane colors that are being used. Pixels whose RGB values do not meet either of these thresholds would be masked as black. 
2. Apply a region mask to localize the areas in which a lane could be detected onto the result from Step 1. A triangular region was used, to try to localize the regon in which the lane lines would likely be found. Pixels out of this region would be masked as black. 
3. Convert the output from Step 2 to grayscale, then apply a Gaussian filter with a kernel size of 5
4. Use the Canny function to identify the edges in the remaining image. 
5. Use the Hough transform to identify lines in the result from Step 4
6. On the original image, we will annotate the Canny edges. On a separate blank (black) image, we will try to identify the center of lanes and the slope, and attempt to extrapolate the posiiton of the lanes. 
7. Using the 2 separate images from Step 7, I then used the weighted_image function to obtain the superposed image, which was the final output of the pipeline. 

#### Additional/Modified Functions 
##### Draw_edges

This function replaces the initial draw_line function, intended to annotate the identified Canny edges, and superpose to the original image from the camera. 

##### Draw_lines 
This function takes in the set of lines identified from the Hough Transform.

For every line in the set, we:

1. Calculate the gradient of the line
2. Calculate the center of the line 
3. Identify if the line should be a left lane or right lane. Left lanes have negative gradients, while right lanes have a positive gradient. A minimum and maximum magnitude of gradient is also imposed to reduce the noise, such as vertical or horizontal lines. 

After iterating through the set, we average the gradient and center to obtain a linear Cartesian equation for both left and right lines. We then extrapolate the line based on the calculated lane center. 

The function then draws the extrapolated left and right lane onto a blank (black) image,to be combined with thue output from draw_edges in Step 7 of the procedure. 

### 2. Potential Shortcomings of the Current Pipeline

There are several shortcomings identified from this current pipeline. 

First, as the basis of this pipeline was in grayscale, this could result in mis-identification of lanes as lane color is one of the filter criteria in lane identification. For example, cracks on the road surface were also identified as lane lines, due to the contrast/edges observed in cracks. 

Second, as a region filter was used, this would reduce the robustness of the detection algorithm during the lane change, the relative position of the lanes to the image would shift when the driver is performing the lane change. As a result, the position of lanes could be mis-identified. 


### 3. Possible Improvements

In light of the shortcomings identified earlier, there are a couple of improvements that could be made to strengthen the robustness of the algorithm. 

First, it might be better to convert colors that are not dropped in the filter to a certain threshold value in terms of grayscale, so they would not be dropped in the Canny edges identification.  

Another potential improvement would be to identify lanes by shape, as while the relative position may change, the shape of the lines as viewed by the driver would not change. 
