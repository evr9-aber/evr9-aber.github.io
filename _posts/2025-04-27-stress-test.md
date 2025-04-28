## Frontend Stress Tests

Stress tested the frontend and how it handled different file paths, sprite names, and tested every feature to ensure there was no way to break or lock up the system.

### Sprite Name Findings

Scratch was surprisingly good at dealing with sprite names. For example, when I named a sprite the same name as another sprite already within the project, when I opened the project it updated the name from Sprite1 to Sprite2.<br/>

When testing for unusual characters, the main problem was saving the image to a temporary file. It would refuse to save certain files without throwing an error then threw an error when attempting to open. Sometimes the name opencv saved the image as was different to the string and so threw an error when attempting to open it later to display in the frontend.

### Fixing Name Issue

Added a check for when a character was not a letter, number, dash or underscore. 

### To Do:
* Finish Write-Up