# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. 1.	Describe pipeline. As part of the description, explain how you modified file.
First, I converted the color image to a grayscale image. I then removed noise in the image by applying the Gaussian Blur function. After that, I passed the image through Canny Edge Detector and masked the region of interest by using cv2.fillPoly(). Then I defined the Hough Transform Parameters on the masked image and drew lines.  

Slope(m) = tan(theta)

Theta is the angle associated with the x axis. The left lane is less than 90 degrees and therefore the slope will have a positive value. Also, I only accepted lines with a slope between 25 and 40. The right lane (theta) will be greater than 90 degrees and therefore the slope will have a negative value. I averaged the line segments and combined the line image with the original image to check my line segments for accuracy. I checked the video to insure the lanes were detected.

### 2. Identify potential shortcomings with your current pipeline

The challenge video included medians, shadows and lanes not detected. In the solid yellow video, outliers a couple seconds in to the video appear hence making this pipeline not ideal for an actual pipeline.

### 3. Suggest possible improvements to your pipeline

The left and right lane lines annotations are noisy/rough. I would like for them to be smoother in order to feel more secure in a moving vehicle that I do not control. 
I could take the filtered/extrapolated/averaged segments of all frames in order to get smoother lines with less exterior noise. I would like to mask moving shadows, highlights and/or barriers on the video to make the curves of the lane easier to detect. I would not feel safe inside this vehicle!
