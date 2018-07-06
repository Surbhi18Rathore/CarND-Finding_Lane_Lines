
# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/solidWhiteCurve.png "original Image"
[image2]: ./examples/gray.png "Grayscale"
[image3]: ./examples/canny.png "cannyedge Ditection"
[image5]: ./examples/index.png "Transformed Image"




### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale,
then I use the output of the grayscale and find the canny edges in image. 
secondly, i used canny edge detected image and apply hough transform which identifies the straight line on the road in a perticular region(region of interest), these straight lines are nothing but lane lines.
Hough function internally uses draw_line function to extrapolate all the lines which are identified by it.
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
taking all the line points identified by the hough transform, find out all the points which belongs to
 the left line and which point belongs to the right line using the slope of the identfied line accordingly kept them in a separate list.
 Then i took the average of the points available in left and right line,found the slope of the average value. Based on this new slope i draw the left and right lane line in a image.

If you'd like to include images to show how the pipeline works, here is how to include an image: 
### Original Image
![alt text][image1]

### Grayscaled Image
![alt text][image2]

### Canny Edge ditected Image
![alt text][image3]

### Extrapolated Line
![alt text][image5]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen, 
identified lane line are flickering and getting deviated from the actual ones... 

Another shortcoming could be i am not maintaining the history of previous images thats why while having dashed lane
 line its
 considering upcoming dashed white/yellow line...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to to identify the accurate line points from the hough tranform so that lane line wont flicker.

Another potential improvement could be to maintain a history of previous images so that if we are not able to identify lane line for next few frames, lane line could be drawn.

