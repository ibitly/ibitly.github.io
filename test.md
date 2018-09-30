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
    
