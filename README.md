# Bird Call Classification
# Overview

This project is an offshoot from a kaggle competetition to identify birdcalls in soundscape recordings.  This competition can be broken into two challenges. first is to identify sounds that are birdcalls in the soundscapes.  The second is to correctly identify the species that produced this call.  here in this notebook, I go after the second challenge.  The strategies and lessons learned here will hopefully help the soundscape identification challenge.

https://www.kaggle.com/c/birdclef-2021/overview


# Goal

Classify the species of any given bird call recording, from a subset of the full bird call database.

The overall database contains 62874 calls with 397 species, totalling over 39 Gb.  Before venturing out and dedicating computing power and time to such a large task, effective strategies that have a strong chance of success should be developed.

This analysis focus on the 5 species with the most recordings within the west coast of the US.


# Strategy

- create a spectrograph of the recording
- perform some basic filtering
- run the filtered spectrograph through a convolutional neural network

# Results and Conclusion

running a convolutional neural network on the spectrogram of the bird call, even when cut down in length and frequency range, did not yield any kind of ability to predict bird species.  All the above models hit early stopping before epoch 20 (early stopping at 5 with no decreas in loss).  training accuracy always maxes out at 0.32, and testing accuracy holds at 0.30.


# Future steps

In continuing with the spectrogram/image neural net strategy:
- additional work needs to be done on preprocessing to create more clarity for the neural net.  Adding noise to the spectrograph my focus the model on the actual signal.
- Implementing prebuilt models that have worked well for other image classification tasks may have better results.  to use them, cloud services may be needed for access to enough gpu memory
- identifying if there's too much variation within species based on type of call would help as well.  then classes could be built to be a combination of species and type of call.

There may also be additional signals that can be found by characterizing the sound outside of just the spectrogram.  Further signal analysis needs to be done to find differentiating features.
