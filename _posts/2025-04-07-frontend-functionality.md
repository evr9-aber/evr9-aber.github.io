## Frontend development

Added functionality to the remaining widgets on frontend and added user input. Also added back the backend debugging options

### Backend Debugging

I removed certain options for running the backend by itself as my main goal was to link the frontend and backend. For testing purposes I still need the backend to run by itself. This was mostly fixed using some self.variables and if __name__ == "__main__".<br/>
I also changed certain things in preparation for frontend. Such as making the feedback text self.variables so that the frontend will be able to use them.

### Feedback Label

The feedback label acts as the app's way of letting the user know of different errors and statuses. So when the input for a function is not valid, it lets the user knows through the text. While recording it gets the status labels from the self.feedback strings in the backend and updates the text accordingly.

### Sprite Name Entry

Instead of being hard coded, the sprite name can be entered in this entry box as input for the record_poses. If the user is out of frame, the text will turn red to let the user know. This is a simple string comparison if which I think is quite volatile as it will break if I change the out of frame message (will look into a better method for this later). If you attempt to record with an empty entry box, the feedback label will let you know and the recording will not start.

### File Path Select

Instead of being hard coded, the file path can be selected using the file button opening a filedialog.askopenfilename to search for .sb3 files. If the file path does not exist, the feedback label will let you know when you try to record and the recording will not start. I added a label above the folder button to tell the user what the current selected file is. Originally I made this a label but ctk labels can't have borders and I felt it looked wrong without them. So I changed it to a deactivated textbox so that it could look the part while not allowing for users to freely edit. That had its own issues as whenever I updated the text in it with the file path from the button, I would have to reactivate it and redeactivate it in order for it to do it.

### Take Photo Button

Disabled by default, while recording you can press this button to manually take a frame. This meant changing the moment capturing a frame in the backend as a defined function for the frontend to use. This didn't need too much rearranging but I did need a way to take this capture using the information the frontend had because I didn't want to make the backend loop to contiously update frame as a self.frame. A global variable should not be changed that much. Luckily, I was already capturing frames in the frontend (and had access to the sprite name box which was the other needed argument for this function). I am unsure if this was the best way to solve this as it means a slight disconnect for the front and backend but it works.

### To Do:
* Clean up frontend design
* Test model with new footage from participants
* Continue write-up