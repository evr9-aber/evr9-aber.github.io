## Fixing Code and Multiple Frames
While preparing for my demonstration I took a few shortcuts in order to complete it. These made a functional product but one flawed due to my lack of knowledge of certain areas (namely, mediapipe) and thus included multiple workarounds. After the demo, we decided my next step was to allow for multiple frames to be taken rather than just one and done like it is currently.

### Fixing Code
I have read up on Mediapipe documentation and reviewed my code to work out where cleanup was needed. This included adding some try-excepts to catch errors better, cleaning extra files created in order to complete the task, removing redundant lines and rearranging the remaining in a more sensible manner.<br/>
I currently had image file path and sprite name as two separate inputs but, unless we're reading in a file, there is no need to differentiate the two. We probably shouldn't be keeping a separate saved file of the image anyway. So I removed the file_path variable and handled it just with Sprite name and some string editing. This will mean I have to change the debug variable where I test using an input image but I should change that image input to a video input anyway.<br/>
Currently I had that debug feature just be a flag in my input arguments and use the image_path variable but due to dissolving that, I needed to update the argument to take its own separate input for video input. Also put an argument in for whether the app is using the computer's built in camera or a USB camera.

### Multiple Frames
Allowing for multiple frames required a bit more rearranging of my code as currently the second you take a frame, it closes the camera. So I made it so space bar takes and saves a picture and 'q' closes the camera capture. I made it so it would add a number to the end of the file name incrementing by one to keep track of them. When processing the images, I add the output to the list of the Sprite's "costumes" so one object has all of our pictures. Costumes is a list of entries in the json file so I create those costume entries and append them to a costumes list to add into our json file at the end.

### To Do:
* Make it so the program takes a picture whenever the subject holds a pose rather than just have it by button press.
* Write up ethics form