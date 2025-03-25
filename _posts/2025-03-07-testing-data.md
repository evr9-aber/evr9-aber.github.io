## Video Testing Evaluation

After recording my test footage, I needed to one by one test the videos with my current model. I had already set up a debug argument to allow for videos to be used instead of the web camera so I could get straight into it. However, it did expose some issues that I had not noticed previously that required fixing before any actual testing could be done.

### Fixing Oversights

Part of some of my videos has no person in frame. This caused two issues that previous testing had not yet revealed. Firstly, if a frame was taken with no human subject, the catch I put in place was not robust enough to not cause the system to break in that scenario. So before proper testing could start I quickly set up my function to return a boolean to skip frames with no person recognised in frame. I will likely return to add something else as my catch but was adequate for the tests. Secondly, it would interpret no subject in the video to be "lack of movement" and thus a pose had been struck and a frame was captured. This last one does not need immediate attention as it does not inherently break any systems, it's just poor logic. There are two ways currently for me to approach it with: add a ceiling value for stillness as well as the floor it currently uses (in order to ignore levels of stillness impossible for a person to keep), or, more likely, use the pose segmentation to detect movement instead of the current background subtraction.<br/>

Another minor problem was that, the image capture is supposed to work by detecting stillness, waiting a second to gauge if that stillness is intentional, then capture the frame, go on cooldown to give the person time to move again before beginning the process again. However, the code was skipping over that second wait if the frame after the cooldown was still enough by the background threshold. This was due to me resetting the second wait when movement was detected, but movement is not measured during the cooldown phase, so if there is no movement when it gets out of cooldown, it sees it has already waited a second previously and captures the frame immediately. This just required me to reset the wait timer when the capture is taken to properly restart the process.

### Test Footage

I recorded the following videos outside:
* In an Open Area
* Against a large door
* With Landscape as background
* With the Sea as my background
* With Plants as my background

I recorded each of these twice, once with long sleeved top and my legs covered, another with a short sleeved top and my legs exposed.<br/>

Important notes about each video:
* Open Area had birds in the background, and passerbys interrupt the recordings
* Against the door had a cat pass by the frame
* Sea recordings did not always have me fully in frame and was dealing with strong winds
* The plants were being affected by the wind

#### Outcomes

A table with an overview of the outcomes can be seen [here](https://evr9-aber.github.io/docs/Test_Criteria_Old.pdf)

#### Conclusions

Biggest things to affect how effective the pose detection was is distance from camera, heavy winds, and nearby plants. <br/>

Distance from camera: When far away from camera (as was the case with the landscape recordings), poses can be detected even though there is movement indicating that it is not intended to be a pose, likely due to the distance making the subject smaller thus the movements are not taking up as much of the frame. <br/>

Heavy winds: While any wind causes some inaccuracy, heavy winds can make much of the poses to be near impossible to detect, as there is very little stillness within the frame. Background movement had shockingly very little to do with the poor performance of the Sea tests as the mask rarely picked up the sea’s movement significantly, instead the movement of the camera was causing the discrepancies. <br/>

Nearby Plants: The landscape footage had little problem with the movements of the greenery and roads behind it, despite having so many potential things to focus on. Even the door video with the cat in frame, did not have much problems with extra movement due to the cat staying relatively still. Plants being close to the subject though had a massive impact in performance due to their constant movement in the wind. It is this inconsistency in movement that makes stillness detected in the rest of the frame to be impossible.

### To Do:
* Test using pose segmentation to detect movement rather than the current form of using background removal techniques to see which is better.
* Record videos of possible non-human subjects that students would like to use.
* Create second mode to allow users to not use human pose segmentation but instead use background removal for inanimate objects that students may also want to use as sprites.
* Once ethics form comes back, request videos from people I know to use as test data.