

[//]: # (Image References)

[image1]: ./test_images/copy_3.png "Lane detection"



### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of several steps described in step below.

1. Convert the image to grayscale
2. Performed a gaussian smoothing on the grayscale image
3. Performed a edge detection on the smoothed image using canny edge detection.
4. Marked a region of the picture that was of interest.
5. Used hough lines to do detection of lanes in the region of interest in the caddy edge picture. 

The draw_lines function was modified in order to draw one consistent line for each lane, this is described in detail below:

	- Defined a maximum slope of the lines detected in hough lines. Lines with a slope of absolute value higher then the maximum slope were filtred out because those kinds of lines are considered horizontal rather then vertical.
	
	- Then determined the slope of the line x = ky + m lines generated and by doing that also classifying if the line belongs to the left or right lane.
	- Then calculated the average k and m values for all of the x = ky + m lines belonging to the left and right lane
	
	- Then one lane is drawn for the left lane and one for the right lane. The line drawn gets values from the average x = ky + m line, calculating the x value when y is somewhere in the middle of the picture and at the bottom of the picture.

Se picture below for an example result

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

Two potential shortcomings with my current pipeline are desribed in the list below:

	- I make a lot of assumptions in my code for example that the lanes always inside my ROI, when for example making a lane change this my code could possibly miss lanes.
	- It does not handle curvaed lanes well since I draw one long line at the moment.


### 3. Suggest possible improvements to your pipeline

I believe I could improve my pipelines by drawing multiple x = kx +m lines instead of just one long one, this could possibly be able to draw curved lanes.

The pipeline is currently only looking at one frame at a time not taking in consideration information gained from previous frames. Using previous known information the lane detection could become smoother and possible to filter out information that seems un-realistic for example a big delta of lane slope between two frames.

