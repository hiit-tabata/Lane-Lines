**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[solidWhiteCurve]: ./test_images/solidWhiteCurve.jpg "solidWhiteCurve"
[solidWhiteCurve_result]: ./test_images/exported_solidWhiteCurve.png "solidWhiteCurve_result"
[carBackground]: ./carBackground.png "carBackground"

---

### Reflection
My pipeline consisted of 5 steps.
1. Transform to grayscale
2. Aply gaussian blur
3. Find Region of interest (Roi)
4. Apply Hough transform and connect lines with high intersection point
5. Merage the line image to the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by increase kernal to 7, in order to reduce the noise. I also increase min_line_length, it can reduce the noise line in the result. Finally also incraese max_line_gap, which cna help to link lines.

The image size might not three channel, it can inculde alpha channel in the image, image[:, :, :3] can ensure the image put into weighted_img() must be 3 channel.

The below image is the finsih result.
###### Before
![alt text][solidWhiteCurve]
###### After
![alt text][solidWhiteCurve_result]


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when there are shadow in the road and the road color not in constant color, Hough transform will create lots of lines in those transection.

Another shortcoming could be the camera position, bottom of the Optional Challenge video include some of the car, which makes Hough transform create lots of noise line at the bottom of the movie.

![alt text][carBackground]


### 3. Suggest possible improvements to your pipeline

One of possible solusion to handle constnat enviroment object is sue first frame as reference, remove constant object in future frame by and operation. It can a mask to ignore those area.
