# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goal for this project was to create a pipeline which could initially detect the lanes of both solid & dashed origin on a set of test images. The pipeline would then be adapted to run smoothly on a set of test videos.

---

### Reflection

### 1. Pipeline for this project 

My pipeline consisted of 6 main functions.

Step 1) Convert the image to grayscale using the **grayscale()** function.

Step 2) Blur the image using the **gaussian_blur()** function on the grayscale image

Step 3) Run Canny Edge detection on the on the blurred image to locate the edges for the given image/video frame using the **canny()** function

Step 4) Cut the image to focus on a main region, mainly the lower center half. The vertices are labeled in the vertices array and the image is cut using the **region_of_interest()** function.

Step 5) Generate a set of hough lines for the given region of the test image using the **hough_lines()** function.

Step 6) Using the generated set of hough lines found in the step above determine whether the slope is negative (right line) or positive (left line). Using the now split set average the slopes of these lines to create a single new line to fit the dashed or solid road lines. This functionality can be found in the **draw_lines()** function and the results are combined with an unedited image using the **weighted_image()** function.


### 2. Identify potential shortcomings with your current pipeline


Although the lines are fairly accurate for the 2 provided video samples the current program was unable to properly function on the challenge video. It does seem to generate a fairly accurate slope to be used (some outliers skew this at certain points) but the current method for finding a point to generate the line with is flawed because of detections outside of the cut image after performing the hough_lines() function.



### 3. Suggest possible improvements to your pipeline


A number of possible improvements can be made to this project though I'd hoped to implement them in addition to new concepts required for the advanced-lane finding project. As outlined above a few core edits would be removing outliers, determining a better way to generate the line's origin location, and possibly some smoothing by taking the previous few frames as an average for how much the line is able to change at any given point.

In addition color detection could be added to remove some of the misintepreted edges in the challenge video. 
