## Model Analysis
After now exploring Mediapipe's body segmentation model, I can make some decisions for how the application will handle the background removal.

### Basic Background Removal
I used the basic background removal example from the Computer Vision workshop to test the simplest form of background removal, using the first frame, using it as the background then subtracting subsequent frames from the background. This example has a "ghosting" effect and is very susceptable to noise and camera movements. If you knock the camera even a little, it messes up the whole removal process. These issues can be worked around using averages and filters but overall, at base, it is competent but too basic for a project like this.

#### Basic Background Removal Example

![Basic Background Removal](/docs/assets/images/basic-bgsubtract-test.png)

### MoG and KNN Approach

These approaches instead create masks that are applied to create a foreground. These masks work but, without further processing, these masks have too much noise to be useful to users. Though KNN seems to be marginally better.

#### MoG Background Removal Example
![MoG Background Removal](/docs/assets/images/mog-bgsubtract-test.png)

#### kNN Background Removal Example
![KNN Background Removal](/docs/assets/images/knn-bgsubtract-test.png)

### Body Segmentation
This uses Mediapipe's model, pose landmarker, and training data in order to detect different parts of the body. I can use this data to create a mask and apply it to isolate the detected person. This worked quite accurately, producing a satisfactory outline of the subject. This still needs further cleanup but provides the most clear starting point. This will likely be what I will use going forward and will be what I use for the demonstration today. The drawback is that it requires a person and needs to recognise a person. This does not always work and students may want to use more than a person (e.g. a teddy bear or toy). It makes the most sense that this will be the default and one of the other background removal options will need to be further developed as a backup (likely KNN). <br/>
Example code taken from here [https://colab.research.google.com/github/googlesamples/mediapipe/blob/main/examples/pose_landmarker/python/](https://colab.research.google.com/github/googlesamples/mediapipe/blob/main/examples/pose_landmarker/python/)

#### Body Segmentation Example
![Body Segmentation Background Removal](/docs/assets/images/mediapipe-test.png)

### Demonstration
Now that I have decided which I will use for this week's demonstration, I will have to edit the application to include the model and edit the code so that the removed background is transparent (rather than black as it currently is). This can be done by converting it to a rgba file and applying an alpha mask using numpy.<br/>
As I already had some image processing code, it clashed with how the example code from mediapipe handles their image data. At the moment I do not know enough about mediapipe to be able to cleanly convert between the two. For the demonstration I just need the code working so I used a temp.png file to save the file and then read it back in as I know how to do that for both image processing code snippets I have so it provides a temporary solution. This is to be changed but will be fine for the demonstration.

### To Do:
* Read up on Mediapipe to better understand the code so I can write my own rather than adapting the example code like I currently am.
* Better learn how to handle the image data to not need the get-arounds I currently have in place.
* Take frames when subject in video has struck a pose rather than take one frame when a button is pressed.
* Consider ethics for ethics form.