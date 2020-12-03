# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Gaussian smoothing to the grayscale image. Second, Canny Edge Detection Algorithm was used to identify the high gradient in color (grayscale) change. Third, a polygon was applied to mask the region of interest. Fourth, the Hough Transformation was used to identify possible line segments in the region of interest. Fifth, the identified line segments was added to the orginal image as transparent red lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by storing the slope of each line segments and separate them into groups of positive and negative slopes. For each group, the average slope and intercept were calculated. Finally, the single line on the left and right lanes was drawn based on the average slope and intercept within the y range of the region of interest. One trick I did was to throw exceptions when there is no line segment identified for either left or right lanes. This makes the code more robust and keep going if there are some image that is hard to process. This trick was not triggered by the homework video but by the challange video.


### 2. Identify potential shortcomings with your current pipeline

Obviously, the challenge is too challengable for my code. In the challenge video, the curve of the line makes my code hard to follow the real curve, but lines that identified. 

Thus, the first shortcoming with the current pipeline is that it is designed to identify straight lines instead of curved lines.

The second shortcoming is that the code is not generic. The parameters was tuned based on the given video, but not for other new videos. I believe there are ways to create parameter tuning algorithm that can make the parameters adaptive to different scenarios.



### 3. Suggest possible improvements to your pipeline

This section will be according to the shortcomings. The curve lines identification will involve changes in Hough Transformation as well as line drawing. Hough Transformation of points of a smooth continous curved line should form a continous curve in the Hough coordinate as the slope and intercept of the smooth curved line is continuously changing. New algorithm needs to be adopted to make the curve line identification work. In addition, parameter tuning algorithm can be applied to make the code more robust.

