## Advanced Lane Finding
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)
![Lanes Image](./examples/example_output.jpg)

In this project, your goal is to write a software pipeline to identify the lane boundaries in a video, but the main output or product we want you to create is a detailed writeup of the project.  Check out the [writeup template](https://github.com/udacity/CarND-Advanced-Lane-Lines/blob/master/writeup_template.md) for this project and use it as a starting point for creating your own writeup.  

Creating a great writeup:
---
A great writeup should include the rubric points as well as your description of how you addressed each point.  You should include a detailed description of the code used in each step (with line-number references and code snippets where necessary), and links to other supporting documents or external references.  You should include images in your writeup to demonstrate how your code works with examples.  

All that said, please be concise!  We're not looking for you to write a book here, just a brief description of how you passed each rubric point, and references to the relevant code :). 

You're not required to use markdown for your writeup.  If you use another method please just submit a pdf of your writeup.

The Project
---

The steps of this project are the following:

1) Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
2) Apply a distortion correction to raw images.
3) Use color transforms, gradients, etc., to create a thresholded binary image.
4) Apply a perspective transform to rectify binary image ("birds-eye view").
5) Detect lane pixels and fit to find the lane boundary.
6) Determine the curvature of the lane and vehicle position with respect to center.
7) Warp the detected lane boundaries back onto the original image.
8) Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

The images for camera calibration are stored in the folder called `camera_cal`.  The images in `test_images` are for testing your pipeline on single frames.

Output: In the folder `cam_params` are the camera parameters saved. The output of the camera calibration Process is stored under `output_images/camera_cal`. And all the other images for developing the pipeline are saved in `output_images`.

The `challenge_video.mp4` video is an extra (and optional) challenge for you if you want to test your pipeline under somewhat trickier conditions.  The `harder_challenge.mp4` video is another optional challenge and is brutal, therefore a deep learning is recomened!

## 1) Compute the camera calibration
This part start with converting the chess board image to grayscale to reduce the image information. With `cv2.findChessboardCorners` the Corners are getting detected and with `cv2.drawChessboardCorners` drawn to the input image. 
In the next step the chessboard get warped. For this the four source points `src` the mark the transformed area and the destination points (must be listed in the same order as src points!) `dst`, the points where it should be transformed to a defined. With `cv2.getPerspectiveTransform()` the trasformation Matrix `M` is computed and applied with `cv2.warpPerspective()` to wrap the image.

<figure>
 <img src="./output_images/material_for_readme/CameraCalibration.png" width="760" alt="Camera_Calibration" />
 <figcaption>
 <p></p> 
 <p style="text-align: center;"> Fig. 1.1: Camera calibration prozess. Left the orginal chess board image. In the middel the draw detected cornes. On the right the unwraped chessboard using the transformation Matrix.</p> 
 </figcaption>
</figure>
 <p></p>



