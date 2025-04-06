## Connected Backend and Frontend!

Once I had rearranged my backend, I realised that my frontend should be similarly restructured to a Class for the sake of consistency and to allow for a main.py<br/>
I was using a PIL image image as that was what GeekForGeeks suggested; I, however, was using a CustomTkinter label rather than a regular Tkinter label and thus had access to CTkImage which gave me a warning that "Image can not be scaled on HighDPI displays, use CTkImage instead." So I made the necessary changes. 

### Issues encountered

Even though I had rearranged my backend to be more appropriate for my frontend, it was still designed to be standalone rather than with a button press. As such it had its own loops and variables to worry about. Originally, as my frontend was already handling a camera loop, I attempted to redesign my backend code to not be a loop, rather a command to be called by a loop. After a while trying to set this up, I realised that I would have to significantly change my code around for this to work as there were too many variables that needed to be contained within the backend's loop and would thus either need to be changed to global variables or continously passed into the loop, neither of which were elegant solutions. After reevaluation, I reverted the code mostly back to its original form, keeping the removal of the cv.imshow and waitkeys as those were not needed with a frontend in place.<br/>
This came with its own issue though as the frontend still needed to keep functioning while the backend is looping. The solution was threading. But I still needed to end the loop in the function and return a value (frame_count) from the function. Luckily self.variables were the way forward. By changing the loop from while True to while self.recording, I could simply make it so a second press of the recording button from the frontend changed that variable and end the loop. Once the loop finished (using thread.join() to wait for the thread to finish), it could update self.frame_count within the SpriteMaker class and thus return the variable by allowing me to fetch it.<br/>
I encountered an issue with my webcam as I had a cap = cv.VideoCapture() for my frontend and in my backend. Trying to open both caused my application to crash as the webcam was already occupied by another bit of code. This meant some further rearranging as I now needed to pass cap as a variable into my function so both my frontend and backend could use the same webcam capture rather than both trying to access it through its own capture.<br/>
I had to disable some backend debug features such as differentiating video capture and live feed. This was due to no longer passing in which footage to use, but rather the footage itself. Also the removal of waitkey means I no longer can test the backend by itself. Disabling these features allowed me to focus on this functionality but I will have to add them back to test.<br/>
Now a press of my record button on my frontend controls the backend and captures as intended!

### To Do:
* Implement functionality of other buttons
* Fix backend debug options temporarily disabled while connecting frontend and backend
* Allow user to input Sprite Name
* Make text box update with user feedback
* Clean up frontend design
* Test model with new footage from participants
* Continue write-up