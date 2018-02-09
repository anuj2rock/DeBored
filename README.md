## A simple android app to help my parents learn new channel numbers. 

### Overview 
I built this app by training a convolutional neural network for channel name spotting. I trained it over a self made dataset of short audio clips (thanks to family members for recording session and a script that helped randomise noise in clips).

This project is customization upon open source Android TF demo app, which was fitting my use case. 

I made some changes in SpeechActivity.java to change UI elements according to my use case.

### Training Convolutional N/W for speech recognition

1. Created a dataset of short clips with each channel name, about 200 clips for each channel and 25 channels were covered.
2. Used train.py from ../tensorflow/examples/speech_commands/ tutorial.
3. Made changes in '--clip_duration_ms' , '--wanted_words' and trained it for 20000 steps.
4. Resulted in a good accuracy of 91%
5. Freezed optmized graph and bundled it into android app's assets folder along with channel name text file.
6. Tweaked SpeechActivity.java to display channel name & number when it identified a channel name and changed DETECTION_THRESHOLD to 0.9f.
7. Bundled apk.

Note: I followed [this really great tutorial on Tensorflow website.](https://www.tensorflow.org/versions/master/tutorials/audio_recognition) 

### Take away
Convolutional neural network based speech recognition works by converting audio signals to spectrograms and then making time line related tweaks to it and feeding these 'spectrogram-images' to convolutional network( a pocess similar to image clasification scenarios).

This approach is definitely not state of teh art but is best to get going quickly and it did fit my use case quite perfectly.
