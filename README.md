# Advanced_Lane_Finding

In this project, the goal is to write a software pipeline to identify the lane boundaries in a video from a front-facing camera on a car. 

The steps of this project are the following:

Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
Apply a distortion correction to raw images.
Use color transforms, gradients, etc., to create a thresholded binary image.
Apply a perspective transform to rectify binary image ("birds-eye view").
Detect lane pixels and fit to 2nd order polynomial.
Determine the curvature of the lane from the left and right polynomials and vehicle position with respect to center.
If it is a bad frame (curvature is not in the reasonable range), use the measurement from the previous frame
Smooth the measurement by taking an average over past few measurements to obtain to lane positions and curvature.
Warp the detected lane boundaries back onto the original image.
Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

The details of the pipeline are included in ADLane_Finding.ipynb.  The video output is captured at project_video_output.mp4. 

Though this pipeline is pretty robust, in some situation it would likely fail.  If camera is not mounted in the middle of the car, if a large percentage of the lane markers are missing or faded, or if the lane marker is not visable in bad weather, etc,in all these situation, the pipeline will likely fail.


