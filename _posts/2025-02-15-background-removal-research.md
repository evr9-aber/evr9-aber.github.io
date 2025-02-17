## Object Detection vs Background Subtraction

### Object Detection
Looking at Mediapipe's object detection model, it certainly is able to detect a person but does so with a bounding box. It is not immediately clear if it is able to outline the person without major changes to the code.

#### Mediapipe code from:
https://colab.research.google.com/github/googlesamples/mediapipe/blob/main/examples/object_detection/python/object_detector.ipynb#scrollTo=TUfAcER1oUS6

### Background subtraction
Attempted MoD approach and KNN approach, it outlines the video okay but definitely will require tweeking as it still picks up noise in the background and misses parts of my person. Perhaps this is is due to my webcam but we should not assume that a classroom will have a camera of quality and thus this should still be fixed.<br/>
Using the basic background removal examples from Machine Learning lecture produces interesting but not useful outcomes. For even a consideration they need to be heavily tweaked.