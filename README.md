# Hand Gesture Music Player

## Gesture Definition:
Based on the work, it is possible to define a general framework that considers gestures from the viewpoint of communication, control, and metaphor. 

- **Communication:** Gestures serve as vehicles of meaning in social interaction.
- **Control:** Gestures function as elements of a system, such as in the control of computational and interactive systems.
- **Metaphor:** Gestures act as concepts projecting physical movement, sound, or other types of perception to cultural topics.

The following section will present examples of gesture definitions.

## Command music player (for now only VLC) with simple hand gestures.

### Supported commands:
- Play
- Pause
- Next track
- Previous track
- Volume up (+10%)
- Volume down (-10%)

## Requirements:
- Python 3
- Run `pip install -r requirements.txt`
- Tkinter (usually comes with Python or as an additional package)
- Tested on Linux and Windows

## Image Processing Steps:

1. **Capture frames and convert to grayscale:**
   - Our Region of Interest (ROI) is the hand region, so we capture the image of the hand and convert them to grayscale.
   - Convert the color image to grayscale using `cv2.imread("image-name.png", 0)` or `cv2.IMREAD_GRAYSCALE`.
     
![Gesture Recognition](https://example.com/gesture-recognition.png)

2. **Blur image:**
   - Apply Gaussian Blurring on the original image for smoothing and noise reduction.
   - Use blurring to create a smooth transition from one color to another and reduce edge content.

3. **Thresholding:**
   - Use Otsu’s Binarization method for image segmentation.
   - Allow only particular color ranges to be highlighted as white while suppressing other colors.

4. **Draw contours:**
   - Find contours in the binary image.
   - Use contours to identify the shape of the hand.

5. **Find convex hull and convexity defects:**
   - Identify convex points (usually the fingertips) and convexity defects (deepest points of deviation on the contour).
   - Count the number of fingers extended.

6. **Convexity defects:**
   - Utilize `cv2.convexityDefects()` to find the convexity defects.
   - Visualize defects by drawing lines and circles on the image.

7. **Point polygon test:**
   - Find the shortest distance between a point in the image and a contour.
   - Determine whether the point is inside, outside, or on the contour.

8. **Match shapes:**
   - Use `cv2.matchShapes()` to compare two shapes or contours and determine their similarity based on Hu-moment values.

## OpenCV:
- OpenCV is a powerful computer vision library used for image operations.
- Used for image capture, processing, flipping, color space conversion, and more.

*Note: Ensure you have the required dependencies installed before running the code.*

