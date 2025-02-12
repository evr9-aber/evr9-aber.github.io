## First Draft

Hannah Dee recommended I attempt to create a version of my project that goes from start to end as a proof of concept starting point.

### Preparation

Made a quick camera capture app using the Computer Vision Workshop 3 code then adding another line to write an image from the camera which OpenCV provides.

### Discoveries

* I discovered that the .sb3 file is storing the assets in plane text though there has been some form of manipulation
* Hannah Dee pointed out that the string of characters the assets is stored as is md5 hashing
* Thanks to a thread on Scratch's discussion board I discovered that .sb3 is simply a zip file - https://scratch.mit.edu/discuss/topic/760429/
* You can literally rename a file to a .zip and unzip it just fine.
* When unzipped, you can see all the assets as plane files, and a project.json file to store the information about each file.
* Reading this file, I realised I can likely unzip the file, insert the image created by the camera into the output folder, append information about that image to json file, rezip file.
* MD5 hash is not hash of name but seems to be hash of image data (needs further investigating)

#### Success!

These discoveries worked great and created a Scratch file with the image from webcam directly added as new sprite.<br/>
First draft of project has been created. It goes from taking a picture from a video on webcam then importing it into a Sprite project. It is crude and not good format. Still needs image processing and background subtraction required for project specs. Will show off in group meeting.

### To Do:

* Begin researching which type of background removal to use (background subtraction vs find person)
* Write paragraph on what type of software development approach to use (e.g. Agile)