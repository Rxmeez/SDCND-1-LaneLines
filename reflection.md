
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

First, I converted the images to grayscale, to return the image with only one color channel, this way we can focus on the white road markings.
Secondly I applied a gaussian blur to blur the image so it can smooth the image, as this will reduce image noise and reduce detail therefore enhance image structure.
Thirdly, a Canny edge transform is applied to the image, to pick up most of the edges in the image, this is done by picking up the drastic changes in the gradient across the image.
Fourthly, a image mask is applied to the region we are interested in which would be the traingle it forms from both bottom corners of the image to the middle, i.e. road lanes.
Next a Hough transform is applied to find lines in the images, this will also detect the lane lines, which are later extrapolated and drawn using the draw_lines() function.
Finally results takes the lane lines weight and makes it to easily view the lane lines.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I ....

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image:

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ...

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
