# VocalVibe Interpreter

* The idea behind this project was to build a machine learning model capable of detecting emotions from speech. In today's world, personalization is essential in the services we interact with daily. 

* The ultimate goal is to create an emotion detector that can gauge emotions and, in the future, recommend various services or products based on your mood. This could be used in industries like marketing to suggest products based on emotions, or in the automotive industry to adjust the speed of autonomous cars depending on the driver's emotional state to avoid potential accidents.

## Analyzing Audio Signals
![](images/joomla_speech_prosody.png?raw=true)

### Datasets:
This project utilizes two datasets:

1. **[RAVDESS](https://zenodo.org/record/1188976)**:
   This dataset contains 1500 audio files from 24 actors (12 male, 12 female) recording short audios in 8 different emotions: neutral, calm, happy, sad, angry, fearful, disgust, and surprised. The file names are labeled such that the 7th character indicates the emotion being expressed.

2. **[SAVEE](http://kahlan.eps.surrey.ac.uk/savee/Download.html)**:
   This dataset consists of 500 audio files recorded by 4 male actors. The first two characters of each file name correspond to the portrayed emotion.

## Audio File Analysis:
Tested audio files were analyzed using waveform and spectrogram plots.

**Waveform:**
![](images/wave.png?raw=true)

**Spectrogram:**
![](images/spec.png?raw=true)

## Feature Extraction:
The next step involves extracting features from the audio files to train the model. For this, we used the [**LibROSA**](https://librosa.github.io/librosa/) library in Python, a popular library for audio analysis.

![](images/feature.png?raw=true)

- Audio files were standardized to 3 seconds to ensure consistent feature extraction.
- The sampling rate of each file was doubled while keeping the frequency constant to maximize feature extraction.

**Extracted Features:**
![](images/feature2.png?raw=true)

The extracted features are arrays of values, with labels appended to them.

## Building Models:
Since this is a classification problem, a **Convolutional Neural Network (CNN)** was employed. Alternative models, including **Multilayer Perceptrons (MLP)** and **Long Short-Term Memory (LSTM)** networks, were tested but underperformed, with low accuracy rates.

Model tuning is a time-intensive process. The most successful CNN model achieved a validation accuracy of just over 70%.

![](images/cnn.png?raw=true)

## Predictions:
After tuning the model, predictions were made using test data. Here is a comparison between actual and predicted values.

![](images/predict.png?raw=true)

## Live Voice Testing:
The model was also tested on live recordings that were not included in the training data. We recorded voices with different emotions to predict the outcomes. The following is an example of a male voice saying, "This coffee sucks" in an angry tone.

![](images/livevoice.PNG?raw=true)
![](images/livevoice2.PNG?raw=true)

As shown, the model accurately predicted both the voice and the emotion.

## Decoding the Output:
If you are using the model directly, here is the decoding guide for the output range (0-9):

- 0 - female_angry
- 1 - female_calm
- 2 - female_fearful
- 3 - female_happy
- 4 - female_sad
- 5 - male_angry
- 6 - male_calm
- 7 - male_fearful
- 8 - male_happy
- 9 - male_sad

## Conclusion:
Building this model involved a great deal of trial and error. The model can accurately distinguish between male and female voices and detects emotions with more than 70% accuracy. This accuracy can be further improved by adding more training data.
