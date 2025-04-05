## Process connecting the frontend and backend

* It is good practice to have the frontend and backend in separate python files.
* For best use it makes sense to make the backend as a class so that you can import it and call the functions as button presses on the frontend.
* I did not program my backend with this in mind so I am going to have to reprogram it
* Needs to be reprogrammed anyway as it was designed as if it was a standalone app so there's opened windows that go against my frontend design.
* Webcam is open already on the app so rather than getting another webcam recording its best to pull from the same source, so this will require reprogramming of both my backend and frontend.
* Global variables will have to be changed to be self.variable in the init()

### Issues encountered

``` python
Exception has occurred: ValueError
Task runner is currently not running.
  File "C:\Users\evane\Documents\CS39440-Major-Project\Major-Project\Project\CS39440\app\backend.py", line 214, in process_frame_async
    detector.detect_async(mp_image, frame_id)
ValueError: Task runner is currently not running.
```
This was due to me having detector in a context manager:
``` python
with self.create_pose_detector(running_mode) as detector:
```
With this and then running something asynchronously in a separate thread, this doesn't work because the context manager might close the task runner when the thread executes. To fix that I am just creating a detector [detector = self.create_pose_detector(running_mode)] before my loop and explicitly close it afterwards.

### To Do:
* Continue write-up
* Connect backend to frontend
* Test model with new footage from participants
* Update frontend to be more stylised