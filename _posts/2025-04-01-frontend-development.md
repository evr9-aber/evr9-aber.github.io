## Notes while developing front end after showing design

* Found website called Custom Tk Builder to quickly design the basis for the app window. Uses visual GUI for me to build the scene then converts it to code for me to use.
* Through that discovered CustomTk which gives me more options with Tkinter's widgets. Checked their github to ensure I had right to use in a product, I could.
* Tkinter does not allow for round buttons, just rounded. Best workaround is to make the circular icons images then setting the buttons to the images (note for later: ensure button is png).
* GeekForGeeks had idea for displaying webcam by using Pillow and OpenCV to make a label an updating image to simulate the webcam stream.
* Having issues with webcam size in window, seems to not be scalable but instead has sizes based on some form of baseline, will have to investigate further because it currently does not look great.
