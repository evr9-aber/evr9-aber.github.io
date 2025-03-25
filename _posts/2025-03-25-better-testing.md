## Better Test Document

Previously, while testing, I was making it up as I was going along. Coming up with test criteria while filming and assessing. So now that I have rerecorded new footage with a better understanding on what I want to test and what my end goals are for an "ideal model", I can properly assess the issues with my model and how the new live pose landmarker works with it.

### Legacy Testing

To properly evaluate what the new application does right (or wrong), I first need to retest all my work with the legacy version of my application. There were multiple times now that I realise the problem was with my test data rather than my application but the same conclusions could be reached:
* The further away someone is to the camera the less likely the application properly detects movement and will capture non-pose frames
* Wind is the biggest issue
* Things moving in the distance does not cause much of a problem but movement in immediate background (like plants) cause pose detection problems

But there are multiple new discoveries with testing such as:
* Poor lighting causes problems with both the pose detection and background subtraction
* Sun glare can cause problems with movement detection

Breakdowns of the outcomes and explanations for tests can be seen [here](https://evr9-aber.github.io/docs/Test_Criteria_Leg.pdf)

### New Application Testing

The new application fixes the issues I intended to address but comes with some new ones too. The live stream pose landmarker helped fix the following issues:
* Background has less of an effect on the pose detection
* Distance has less of an effect on the movement detection
* Poses captured while subject is still moving mostly mitigated

However, there are problems it does not fix, and has its own issues:
* Any problems with background removal have not been mitigated
* Poor lighting can still cause movement detection problems and can make pose detection fully impossible
* While distance has less effect on movement detection, if too far the pose detection is full on impossible
* Wind is still an issue
* Glare can still be an issue for pose detection

Breakdowns of the outcomes and explanations for tests can be seen [here](https://evr9-aber.github.io/docs/Test_Criteria.pdf)