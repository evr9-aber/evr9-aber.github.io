## Updating the Vision Model

The main issues with detecting when someone stands still was with plants in the background moving and with the person not being in frame or being small within the frame. All of these issues could be addressed by focusing our stillness onto our subject. Instead of taking the whole frame into account, we find and track our subject using our MediaPipe pose segmentation model, and look at how our MoG background removal reacts to specifically that MediaPipe mask.

### Development

So far, my MediaPipe pose segmentation model has been working using still images. This new task requires Pose Segmenter to work on a Live_Stream. This is causing me various issues.
* It functions differently from the Image running format
* It requires Result Callback to function
* This is a relatively new thing for me coding-wise
* This complicates testing using pre-recorded footage, as Pose Segmenter has a video running mode too that I cannot properly utilise without having my prerecorded testing be different from my webcam testing.

### To Do:
* Solve result callback issue
* Fix any possible issues with giving prerecorded footage once this method is working
* Test against same videos as previous to create new results table