## Pose Segmenter Live Stream

To focus the background subtraction method to detect stillness within the person, rather than the whole frame. To do this I am using a Live_Stream version of the MediaPipe pose segmenter in order to create an extra mask to apply before the MoG.

### Issues

Doing this live stream requires asynchrous result callback to run along side my synchrous code. This caused issues as my code would attempt to grab data that had not yet updated or data updating midway through its use. For example, I had a check if the mask for my frame was None to ensure that I wasn't attempted to apply my functions to a NoneType variable, however, as it was updating asynchrously and globally, it changed itself to NoneType while already inside my if statement. This was easy to mitigate by giving the value of the old data before turning NoneType to another variable that won't update globally.<br/>

Other issues arose, like setting up the callback function in the first place, the fact that my image model for pose_segmenter rejected having a callback function set so I had to add an extra check to prevent that, it required a timestamp to work, it is more computationally heavy.<br/>

Prerecorded footage seems to perform poorly with the live_stream model which needs to be fixed before further testing. I could make it be a video model but that unfairly misses out the callback function and thus makes it poorer for testing.<br/>

I realised the mask was not actually properly applying, instead of outlining my person, it instead was creating more like a bounding box for the person, not a very accurate one at that. I realised that how I was calculating the mask was causing it to take any input and output its extreme unless it was exactly zero. While this was helping, this was not what I had in mind by using pose segmentation. When I fixed this calculation, I realised that the pose segmentation model was asynchronously lagging behind my live feed and thus was, after a few seconds, made useless to the MoG.

### To Do:
* Fix live feed delay
* Update model to handle saved videos better
* Experiment with test footage to create new test sheet
* Tweak model if necessary
* Prepare for demonstration