# Gesture-Control
Gesture Volume Control project using OpenCV and MediaPipe framework provided by Google.
## Software Requirements
1. opencv-python
2. mediapipe
3. comtypes
4. numpy
5. pycaw
### MEDIAPIPE
**Hand Landmark Model**
After the palm detection over the whole image our subsequent hand landmark model performs precise keypoint localization of 21 3D hand-knuckle coordinates inside the detected hand regions via regression, that is direct coordinate prediction. The model learns a consistent internal hand pose representation and is robust even to partially visible hands and self-occlusions.

To obtain ground truth data, we have manually annotated ~30K real-world images with 21 3D coordinates, as shown below (we take Z-value from image depth map, if it exists per corresponding coordinate). To better cover the possible hand poses and provide additional supervision on the nature of hand geometry, we also render a high-quality synthetic hand model over various backgrounds and map it to the corresponding 3D coordinates.

**Solution APIs**

Configuration Options:

* Naming style and availability may differ slightly across platforms/languages.

* STATIC_IMAGE_MODE
If set to false, the solution treats the input images as a video stream. It will try to detect hands in the first input images, and upon a successful detection further localizes the hand landmarks. In subsequent images, once all max_num_hands hands are detected and the corresponding hand landmarks are localized, it simply tracks those landmarks without invoking another detection until it loses track of any of the hands. This reduces latency and is ideal for processing video frames. If set to true, hand detection runs on every input image, ideal for processing a batch of static, possibly unrelated, images. Default to false.

* MAX_NUM_HANDS
Maximum number of hands to detect. Default to 2.

* MODEL_COMPLEXITY
Complexity of the hand landmark model: 0 or 1. Landmark accuracy as well as inference latency generally go up with the model complexity. Default to 1.

* MIN_DETECTION_CONFIDENCE
Minimum confidence value ([0.0, 1.0]) from the hand detection model for the detection to be considered successful. Default to 0.5.

* MIN_TRACKING_CONFIDENCE:
Minimum confidence value ([0.0, 1.0]) from the landmark-tracking model for the hand landmarks to be considered tracked successfully, or otherwise hand detection will be invoked automatically on the next input image. Setting it to a higher value can increase robustness of the solution, at the expense of a higher latency. Ignored if static_image_mode is true, where hand detection simply runs on every image. Default to 0.5.

#### **References**

[MediaPipe Hand Solutions](https://google.github.io/mediapipe/solutions/hands#python-solution-api)

![image](https://user-images.githubusercontent.com/93963622/187082050-d3244116-ba94-493d-af1c-6f180e010dda.png)

![image](https://user-images.githubusercontent.com/93963622/187082068-0b6e4b76-68b7-45ca-a185-19303d86c269.png)


