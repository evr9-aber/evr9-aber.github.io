## Notes for Computer Vision Reading

Read certain chapters of Computer Vision: A Modern Approach by Forsyth Ponce.<br/>
Read chapters:
* 4.7, 5.4, 6.3, 6.4, 9.2, 17.1, 20.2, 20.3, 20.5

### Notes about this reading

* Frontal views of faces have distinctive patterns at a low resolution: "eyes form dark pools, under a dark bar (the eyebrows), separated by a lighter bar (specular reflections from the nose), and above a dark bar (the mouth)."
* Searching for pairs of images can be done by comparing "a heavily smoothed and resampled image and then refine that match by looking at increasingly detailed versions of the image"
* When filling holes in images, the order in which pixels are synthesised is important.
* "[Filling holes] rely on two properties of natural images: the prominence of self-similarities - that is, many regions in the same picture often look the same picture often look the same.
* Methods for denoising (might be worth looking into to help with background subtraction)
* Weighting in background subtraction
* "Pixels are neither pure background or pure foreground". The example they use is hair often has some background, this will be something I will look carefully at when testing using other people's sent footage.
* Pictoral structure model and how it applies to parsing people
* We can assume that segments will contain known olor patterns - "typically a mixture of skin color and blue". Will keep in mind when testing with different skin tones. Will also have to record test footage in my room using the LED lights to test different lighting color and how that affects the model.
* Estimate for body parts and how size may affect this
* Why tracking people is difficult
* Number of degrees of freedom in tracking people
* Some human motions are repetitive
* Human motion is complex but comprosises of smaller pieces of motion. "Many everyday motions are stereotyped". This applies to how motion is tracked in video games where different motion tracked animations can be transitioned into one another.
* Figure of activities being classified

### To Do:

* Clean up frontend design
* Test model with new footage from participants
* Continue write-up