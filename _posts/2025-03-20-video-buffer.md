## Video Testing

Tried one last thing to get prerecorded videos to run smoothly using a video buffer. This has not helped and I think it is time I accept that it is not going to as they mismatch the model. Testing will take a bit longer but should still be completely valid despite harsh runtimes. Besides, I realised that I could simply run the testing on my main computer. My laptop is not that powerful but that is actually useful for testing because it means it is realistic to the computers that a school is going to have; they are unlikely to have computers as powerful as my main home computer due to budget. However, for testing pre-recorded videos, I can run it on my main computer because we are not testing how well it runs but rather the model. Testing how well it runs can be done with live video on my laptop to test for real scenarios, while my model testing can be done on my more powerful computer for it to run better.

### Fixed exit key

Had a problem come up during my demonstration where my q key took multiple attempts to exit out of the program. Turns out that the way I was handling wait key was wrong and I was perhaps lucky that pressing q actually worked at all. I had two cv.waitKey(1) for the loop, the first being for manually capturing a frame, and the second for exiting. Manually taking a frame works every time as it is the first waitkey. I have now put them in the same elif statement and it now exits every time.<br/>

From:

``` python
if cv.waitKey(1) == 32: # if space bar is pressed
    frame_path = f"{image_name}_{frame_count}.png"
    cv.imwrite(frame_path, frame) # write image to image path
    frame_count += 1
    status_text = "CAPTURED"
    sound_channel.play(pygame.mixer.Sound('sounds/camera_click.wav'))

if cv.waitKey(1) == ord('q'): # if q key is pressed
    break
```

To:
``` python
key = cv.waitKey(1)
if key == 32: # if spacebar is pressed, capture a frame
    frame_path = f"{image_name}_{frame_count}.png"
    cv.imwrite(frame_path, frame) # write image to image path
    frame_count += 1
    status_text = "CAPTURED"
    sound_channel.play(pygame.mixer.Sound('sounds/camera_click.wav'))
elif key == ord('q'): # if q key is pressed, exit
    break
```

### To Do:
* Put test videos onto computer and run tests on all of them
* Experiment with test footage to create new test sheet
* Tweak model if necessary
* Write up forms for people testing as outlined in my ethics