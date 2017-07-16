
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps; gray, gaussian, canny_img, region, hough_img and results.

First, I converted the images to grayscale, to return the image with only one color channel, this way we can focus on the white road markings.<br>
Secondly I applied a gaussian blur to blur the image so it can smooth the image, as this will reduce image noise and reduce detail therefore enhance image structure.<br>
Thirdly, a Canny edge transform is applied to the image, to pick up most of the edges in the image, this is done by picking up the drastic changes in the gradient across the image.<br>
Fourthly, a image mask is applied to the region we are interested in which would be the traingle it forms from both bottom corners of the image to the middle, i.e. road lanes.<br>
Next a Hough transform is applied to find lines in the images, this will also detect the lane lines, which are later extrapolated and drawn using the draw_lines() function.<br>
Finally results takes the lane lines weight and makes it to easily view the lane lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by taking the array of hough lines and separates them by positive and negative slopes which represents right and left lane line respectively. Once I gather all the points for each side of the line, i would find an average by using np.mean and find a mean gradient and intercept, which later helps get the new coordinates for the line as y1 and y2 are known to be the in the middle of the image and bottom of the image. A problem I was facing were NaN values where the line might be vertical creating gradient, infinity or a horizontal line creating a gradient, 0. To ensure no NaN values pass through a try case was put in place to get rid of any values creating error.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when car is changing lane, as this will effect the gradients to detect the lane lines, also in poor lit conditions is where the car would struggle to pick up the lines. This could be picked up by fine-tuning the low thresholds, however this causes us to overfit and make it a specific senario case.

Another shortcoming could be if you get too close to the car infront it would block lines, or if block lines where missing it wouldnt detect anything in the given region.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to create a store previous value system for the lane lines, so if there is a nan value, it would resort to the previous lane line instead of creating this 'blink effect'.

Another potential improvement could be to create a better system to find optimal parameters depending on the input video.
