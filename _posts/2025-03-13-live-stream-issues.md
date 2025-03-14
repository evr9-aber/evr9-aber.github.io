## Live Stream Struggles

Was hoping to get a version of the model to utilise the Live_Stream model for the Mid Project Demo and while I am getting closer, I do not believe it will be demo ready. I can talk about it but it will not be ready to show off. I did fix the mask though, so when it is performing properly it does work as intended.

### Issues
The model is beginning to work but the pose landmarker model is still too heavy for usage on a laptop. If there are any complicated movements done by the subject in frame, it can lead to multiple seconds of delay before the Pose Landmarker catches back up to the livestream and thus the MoG model is pretty useless until the model catches up. For short videos, and simple movements the model tends to work fine, but if there is even too many tabs open on the computer it can cause it to be worse performing than the app without the landmarker.

#### How I am trying to mitigate it
At the moment I am mitigating this issue by lowering the size of the input stream the model is getting, this leads to less accuracy but better performance, and the accuracy loss is not enough to be concerned over.<br/>
I am also using threading to help image processing not interrupt the main processes.<br/>
Have set up multiple variables that I am lowering and increasing to test performance with confidence of model.<br/>
Using lite version of AI for live stream which is less accurate but much easier for my computer to handle<br/>

### To Do:
* Write up forms for people testing as outlined in my ethics
* Experiment with test footage to create new test sheet
* Tweak model if necessary
* Prepare for demonstration