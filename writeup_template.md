# **Finding Lane Lines on the Road** 
## Steps to implement lane detection
1. Identify a lane thresholding strategy
2. Apply edge detection algorithm
3. Detect lines by using hough transform
4. Seperate the lanes as left and right using their slopes
5. Extrapolate lanes based on average slope and y-intercepsts of left and right lanes

---

## Identify a lane thresholding strategy
In my project, I had explored RGB color space. we need to detect white and yellow lines on the road.Ideally, White RGB values are (255,255,255) where yellow has RGB values as (255,255,0). I explored diferent thresholds values and and finally settled with (210,201,150) to accomidate for intensenty variation due to lighting conditions. Resuls for this approch are visbile below.
[image1]:https://github.com/willofdiamond/CarND-LaneLines-P1/blob/master/test_images_output/rgb_threshold.png "rgb threshold image"
[image2]:https://github.com/willofdiamond/CarND-LaneLines-P1/blob/master/test_images_output/rgb_threshold_avge_slopeandintercept.png "rgb threshold avge slopeandintercept image"
![alt text][image1]
![alt text][image2]

After furture more anlaysis I felt confident that red channel will do just fine or much better the RGB. I had selected 150 threshold for Red channel image. Have to explore other color spaces yet.

## Apply edge detection algorithm
Before applying edge detection it is a good practice to average the image as it removes noise in the images. I had used canny edge detection for detecting edges. I had selected low threshold as 30 and high threshold as 120.

## Detect lines by using hough transform
Hough is the most populare line detection used in computer vision problems. This can be used to detect line segment and its end points

## Seperate the lanes as left and right using their slope
1. Line end points from hough transform can be used to find slope.
2. Right lane should have negative slope while left lane should have positive slope. It is common sense to ignore horizantal lines and line with slope near to 0. 
3. Average slope and Y- intercept of the right and left lane are detected.

## Extrapolate lanes based on average slope and y-intercepsts of left and right lanes
Average slope and Y- intercept of the right and left lane are used to extrapolate the new lanes



---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline
As I rely on the RGB space. Bright light reflection on the road makes lane detection hard.


### 3. Suggest possible improvements to your pipeline
I would like to check the thresholding in other color spaces and test the algorithm on more sample videos
