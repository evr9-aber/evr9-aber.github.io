## Notes while developing front end after showing design

* Found website called Custom Tk Builder to quickly design the basis for the app window. Uses visual GUI for me to build the scene then converts it to code for me to use.
* Through that discovered CustomTk which gives me more options with Tkinter's widgets. Checked their github to ensure I had right to use in a product, I could.
* Tkinter does not allow for round buttons, just rounded. Best workaround is to make the circular icons images then setting the buttons to the images (note for later: ensure button is png).
* GeekForGeeks had idea for displaying webcam by using Pillow and OpenCV to make a label an updating image to simulate the webcam stream.
* Having issues with webcam size in window, seems to not be scalable but instead has sizes based on some form of baseline, will have to investigate further because it currently does not look great.

### Investigated further into webcam size issue
Seems to be an issue with opencv displaying the camera. I was changing the webcam size using cap.set(cv.CAP_PROP_FRAME_WIDTH, width) and cap.set(cv.CAP_PROP_FRAME_HEIGHT, height) which was not working as webcams handle sizes in discrete values rather than arbitrary scaling. The workaround for this was to scale the frame after it had been recorded by the webcam using cv.resize(frame, frame_size, cv.INTER_LINEAR) where frame_size is (width, height). This method allows for arbitrary scaling so I can scale how I would like. My webcam captures at 4:3 aspect ratio so that is what I have designed around. Other webcams may record at other aspect ratios so I have set up a scaling method which scales the width using hard coded values but height by calculating the ratio of the webcam's native width and the new hard coded width and applies it to the height. This means that, if the webcam footage is of a different aspect ratio than the one I have designed around, it doesn't get squished.

### To Do:
* Continue write-up
* Connect frontend to backend
* Test model with new footage from participants
* Update frontend to be more stylised