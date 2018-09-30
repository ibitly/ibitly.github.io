# Documentation for the Oppo Demo App

## UI

_Scoring_ is only function available in this demo app right now. It provides rating scores for photos in different aspects. There are three buttons on the major UI:
1. ADD IMAGE - choose a photo from your phone and the app will show the rating scores of the photo.
2. ADD FOLDER - choose a folder from your phone and the app will calculate the rating scores for all the photos inside the folder and show the results on the screen.
3. SAVE TO SDCARD - this button saves all the results on the screen to a CSV file at the root path of the SD Card.  

## Photo Ratings

There are three sets of rating scores as shown on the screen: 
1. Scores for five different aspects (_Clarity, Exposure, Colorfulness, Composition, Emotion_) based on traditional computer vision. They are roughly in the range of 0 - 6.
2. _CompositionDL_: A composition score based on a deep learning model. It is rougly in the range of 0 - 6.
3. A score for _Overall Aesthetics_ (in the range of roughly 0 - 1) and scores for 11 attributes (in the range of about -1 to 1) based on another deep learning model.

There are also two overall scores, which are linear combination of 5 scores as shown in the following formula:

    Overall = 0.2 * Clarity + 0.3 * Composition + 0.2 * Colorfulness + 0.3 * Exposure + 2 * Overall_Aesthetics - 1.0
    Overall (with CompositonDL) = 0.2 * Clarity + 0.3 * CompositionDL + 0.2 * Colorfulness + 0.3 * Exposure + 2 * Overall_Aesthetics - 1.0
    


## Sample export as csv

```
Overall,Overall(with Composition_DL),clarity,clarity_rating,exposure,exposure_rating,colorfulness,colorfulness_rating,composition,composition_rating,emotion,emotion_rating,compositionDL,compositionDL_rating,Overall Aesthetics,Balancing Element,Color Harmony,Good Content,DoF,Light,Motion Blur,Object Emphasis,Repetition,Rule of Thirds,Symmetry,Vivid Color,File Path
4.4744763,3.8237572,3.5549173,4.0,4.172337,4.0,2.420254,2.0,3.5339706,4.0,-1.0,1.0,0.9310937,1.0,0.4832512,0.058778103,0.31004578,0.19818033,-0.035638005,0.08463739,-0.013548456,-0.3640391,0.07013942,-4.4339523E-4,0.023627505,-0.04665517,/DCIM/Camera/IMG_20180918_154022.jpg
-10000.0,0.0,-1000.0,1.0,-1000.0,1.0,-1000.0,1.0,-2997.0,1.0,-1000.0,1.0,-502.5,1.0,null,null,null,null,null,null,null,null,null,null,null,null,/DCIM/Camera/VID_20180918_153959.mp4
4.7945457,4.2683544,3.1151402,4.0,3.9206836,4.0,2.782359,3.0,5.464679,5.0,0.0,1.0,3.3599133,3.0,0.458457,0.01565955,0.16373156,0.10090281,-0.011677088,-0.0098584145,-0.016150463,0.3474432,0.048235144,-0.04199028,0.022995586,-0.16633546,/DCIM/Camera/IMG_20180919_084318.jpg
```

