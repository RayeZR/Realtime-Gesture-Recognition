# Real-time gesture recognition

## Introduction

This repo is my course project for Machine Learning & Computer Vision of UCA (2019-2020). 

The aim of this project is to use traditional CV method and deep learning based method to achieve real-time hand gesture detection with OpenCV and webcam. 

The project is implemented in python using google colab notebook, with minor js helpers.

Reference to the original page: https://moodle.polytech.unice.fr/course/view.php?id=7

## Method

CAMShift (Continuously Adaptive Meanshift) is used to detect and track the hand. Pretrained MLP and VGG19 are used to perform gesture recognition. Data used to train the models are collected by myself. An overview of the steps:

1. Detect the face using the Adaboost Haar cascade detector

   The trained Harr cascade face detector in opencv-python is used to detect the captured image of the webcam. The detector is an Adaboost classifier, with 38 weak classifiers to improve the precision (reduce the bias) while not exerting big influence on variance. Each classifier contains a number of Haar features. The Harr features are a series of black and white rectangle-like filters which can be computed quickly by the integral map. With only the first two simple features, the classifier can yield 100% recall and reject 50% non-faces. And with only the first two classifier, the algorithm can obtain a 100% recall and reject 80% non-faces.

2. Use the detected face to compute the histogram and initialize the histogram in CAMShift
3. After the first color initialization, use CAMShift to detect and track face and hand areas
4. Face detection using CAMShift
5. Erase the face area, detect hand in the new probability map
6. Transform the detected hand image into the input feature to be fed into the MLP or VGG net
7. Show the real-time detection result in the camera view

More details in implementation, demos and examples can be found in the google colab notebook.

## Acknowledgement

I would like to thank Prof. Frédéric Precioso, our course lecturer, for delivering us the interesting and informative lectures.

I would also like to thank Dr. Melissa Sanabria, our teaching assistant, for giving us lots of practical guidance of the content.



