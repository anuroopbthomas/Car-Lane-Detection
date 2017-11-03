# **Finding Lane Lines on the Road**

## Anuroop Thomas's Submission

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/lines-solidWhiteCurve.jpg "Final"
[image2]: ./test_images/lines-solidWhiteCurve "Original"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of several steps that essentially gave the image the corrected vision of the proper image.

This is the original image that I will be using.
![alt text][image2]

These steps were all contained within the process_image function which took the image as input. The first step in this was making the picture grayscale by putting it in the grayscale function. The next step was to get a gaussian blur with a kernel size of 5. Next, I got the edges of the highlighted lines. by using canny with a low threshold of 50 and a high threshold of 150. Next, I defined a shape as the object imshape.

In the next section of my code in the function, I defined the vertices of the region of interest quadrilateral and applied this region to the image.

Then in the next section, I called my hough lines function which I added a lot of features to. Specifically what happens in the hough_lines function is that it takes in the image, the rho, theta, threshold, the minimum line length, and maximum line length (If you'd like to learn more about hough lines since they are a somewhat complex concept use this link https://docs.opencv.org/2.4/doc/tutorials/imgproc/imgtrans/hough_lines/hough_lines.html). It creates two objects, one is lines which uses cv2.HoughLinesP to create some valid lines for the image. The second object line_img returns an array all with zeros in it to get ready to fill in which values should be lines.

The function draw_lines is called and I also added a lot to this function. Essentially, a basic summary of this code is that it takes averages of points and determines slopes and outputs these lines in red onto the image.

Back to the process_image function, the final result is given from the function, weighted_image which basically is the final output with all lines drawn and such drawn on the image.

Then outside of the pipeline it runs through all of the files in test_images and creates images in the existing directory test_images_output with all lines drawn on.

This is the final product.

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

Within the pipeline there are actually some major shortcomings.

The pipeline does not work on the challenge video because it requires a straight line and the curved lane in the image doesn't work as that probably would have to graphed as some sort of exponential function.

Another issue is that sometimes some specific line markings are not picked up in blue which was also what my program did, so this is an issue.


### 3. Suggest possible improvements to your pipeline

A possible improvement to this pipeline would be incorporating exponential lines to make a curved lane. And of course having a better detection of lane markings would hopefully improve the image a lot better.
