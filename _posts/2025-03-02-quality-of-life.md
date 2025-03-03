## Quality of Life Changes

Started asking friends if they would be available for using their footage for testing but until I can get my ethics form gets confirmed then I cannot continue with this. So for now, I have implemented QOL changes to help usage and future development.

### Naming Conventions

Been coding mostly in C before this project recently, so I have needed to remind myself of conventions for Python. I have good experience with Python, working with it a lot last year, but I still sometimes mix up my conventions and that has affected my variable and filename naming causing them to be inconsistent. So I have cleaned that up for the future.

### Audio Cues

There are text cues already for frame capture but when the subject is stood across the room, trying to hold a pose, seeing it is not always easy, if at all possible. To help users know when the application is working, it made sense to add audio cues. So, I found some royality free sounds on freesound.org to use in my project. I have a small ding (from [here](https://freesound.org/people/MashedTatoes2/sounds/515643/)) to alert the user that it has detected you are still enough for a pose and it has begun capture. Then if they continue to stay in that pose, a frame is captured and a computer click sound is played (from [here](https://freesound.org/people/Flem0527/sounds/629979/)).

### To Do:
* Record more videos of myself in different contexts for testing.
* Record videos of objects to see how the application reacts with it.
* Record videos of possible non-human subjects that students would like to use.
* Create second mode to allow users to not use human pose segmentation but instead use background removal for inanimate objects that students may also want to use as sprites.