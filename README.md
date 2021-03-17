# **Advanced Lane Lines Finding**

[//]: # (Image References)
[im01]: ./camera_cal/calibration4.jpg "distored image"
[im02]: ./output_images/undistored_calibration4.jpg "Undistorted image"
[im03]: ./output_images/unwarped_image.jpg "original image"
[im04]: ./output_images/warped_image.jpg "Unwarped image"

[im05]: ./output_images/color-fit-lines.jpg "color-fit-lines"
[im06]: ./output_images/result_image.jpg "result image"
[im07]: ./output_images/curve_equation.jpg "color-fit-lines"


## **The Goal of this Project**
To wirte a software pipeline to identify the lane lines in videos

The goals / steps of this project are the following:

* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply a distortion correction to raw images.
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view").
* Detect lane pixels and fit to find the lane boundary.
* Determine the curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.
The goals and steps of this project are  the following:

## **rubric points** 

### **Camera Calibration**

find camera instrinsic parameter(distortion) by camera_cal folder's files
and save the result in output_image folder

Using the openCV library, and essential function is `findChessboardCorners`, `calibrateCamera` and `undistort`.

Check board size is 9x6 so, some zoom in image is not used for calibration
but all image's distortion is compensated 


* distored image smape
![alt text][im01]
* undistored image sample
![alt text][im02]

### **Estimate the image transform**

Find a transform matrix for bird eye's view
Using a straight line image 

* unwarped image
![alt text][im03]
* warped image
![alt text][im04]

### **Define the sobel threshold and Color thresold**

Using the Sobel threshold to a binary image, make gradient filtered image.
-Key factor are axis(x or y), magnitude, direction
Also, Color threshold to a binary image, make gradient filtered image.
-Key factor is changing a RGB colored image to a HLS image, filtered S channel

### **Find lane pixels and estimate fitting line**
Find lane pixel in warped binary image.
There are two methods 
1. find lane pixel in window area of image
2. find lane pixel in sliding on image y-axis
### **Estimate lane curvature and offset of lane's center**

Estimate lane curvature left/right lane by 2nd polynomial line
and, find a offset of camera center between lane
(when find a offset, using a meter per pixel scale values)
* curvature example
![alt text][im05]
* curvature equation
![alt text][im07]
### **Drawing the lane result and some information**
Finaly, Drawing the lane area on original image.
Drawing the lane curvature data and offset 
* result
![alt text][im06]


## **shortcomings**

- Shadow Area is too difficult for filtering
## **Next Improvements**

- `More `Advanced Lane Line finding
- study a smoothing and tracking algorithm
- `challenge_video.mp4` & `harder_challenge_video.mp4`


## How to write a README
A well written README file can enhance your project and portfolio.  Develop your abilities to create professional README files by completing [this free course](https://www.udacity.com/course/writing-readmes--ud777).

