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

The details of the pipeline including the technqiques are included in ADLane_Finding.ipynb.  The video output is captured at project_video_output.mp4. 

The major problem that I faced is the "shadow" issue-- Where there is a shadow, the lane pixels are deviated.  To overcome this problem, I used lightness channel threshold on top of Saturation threshold.  
There are several improvement that I could do in order to make it more robust:
1. Make the threshold value programmable instead of hard code.  There are quite a few hard coded threshold I used throughout this project, if they are be automated /programmable , that will be improve the performance.
2. In order to smooth over the measurement, I used several frames to average the curvature value.  If there is a suddent change of curvature, such as right/left sharp turn, then this smooth method would likely lead to a delay in reporting the real value.
3. Make the src and dst points programmable when doing the perspective transform.  In my code, they are hardcoded, if they are programmable according to the image size, etc, that will make the pipeline more robust.

Though this pipeline is pretty robust, in some situation it would likely fail.  If camera is not mounted in the middle of the car, if a large percentage of the lane markers are missing or faded, or if the lane marker is not visable in bad weather, etc,in all these situation, the pipeline will likely fail.


