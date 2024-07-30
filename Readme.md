# Gesture Recognition

## Problem Statement

Imagine you are working as a data scientist at a home electronics company which manufactures state-of-the-art smart televisions. You want to develop a cool feature in the smart TV that can recognize five different gestures performed by the user, which will help users control the TV without using a remote.

In this group project, you are going to build a 3D Conv model that will be able to predict the 5 gestures correctly.

Each gesture corresponds to a specific command:

| Gesture       | Corresponding Action                |
| --------------| ------------------------------------|
| Thumbs Up     | Increase the volume.                |
| Thumbs Down   | Decrease the volume.                |
| Left Swipe    | 'Jump' backwards 10 seconds.        |
| Right Swipe   | 'Jump' forward 10 seconds.          |
| Stop          | Pause the movie.                    |

## Objectives

1. **Generator**: The generator should be able to take a batch of videos as input without any error. Steps like cropping, resizing, and normalization should be performed successfully.

2. **Model**: Develop a model that is able to train without any errors. The model will be judged based on the total number of parameters (as the inference/prediction time should be less) and the accuracy achieved. Start training on a small amount of data and then proceed further.

3. **Write-up**: This should contain a detailed procedure followed in choosing the final model. The write-up should start with the reason for choosing the base model, then highlight the reasons and metrics taken into consideration to modify and experiment to arrive at the final model.

## Conv3D and Transfer Learning Summary Results

| Experiment                                         | Total Parameters | Trainable Parameters | Augmentation | Transfer Learning | Non-trainable Parameters | Training Accuracy | Validation Accuracy | Observations                                                   |
|----------------------------------------------------|------------------|----------------------|---------------|------------------|--------------------------|-------------------|---------------------|---------------------------------------------------------------|
| ModelConv3D1 - Experiment 1 - Frames-16, Epoch-20 | 1,736,389        | 1,735,525            | No            | No               | 864                      | 90.79%            | 81.00%              | Good training accuracy, moderate validation accuracy         |
| ModelConv3D1 - Experiment 2 - Frames-30, Epoch-30 | 1,736,389        | 1,735,525            | No            | No               | 864                      | 89.01%            | 40.00%              | Good training accuracy, poor validation accuracy; likely overfitting |
| ModelConv3D1 - Experiment 3 - Frames-20, Epoch-20 | 1,736,389        | 1,735,525            | No            | No               | 864                      | 79.44%            | 25.00%              | Moderate training accuracy, poor validation accuracy; likely overfitting |
| ModelConv3D1 - Experiment 4 - Frames-16, Epoch-20 | 1,736,389        | 1,735,525            | Yes           | No               | 864                      | 84.00%            | 74.00%              | Good training and validation accuracy with augmentation       |
| ModelConv3D1 - Experiment 5 - Frames-16, Epoch-50 | 1,736,389        | 1,735,525            | Yes           | No               | 864                      | 89.41%            | 84.00%              | High training and validation accuracy with more epochs and augmentation |
| ModelConv3D2 - Experiment 6 - Frames-16, Epoch-50 | 15,987,973       | 1,272,133            | Yes           | VGG16            | 14,715,840               | 96.50%            | 50.00%              | High training accuracy, moderate validation accuracy; potential for improvement |
| ModelConv3D2 - Experiment 7 - Frames-30, Epoch-50 | 15,987,973       | 1,272,133            | Yes           | VGG16            | 14,715,840               | 99.50%            | 55.00%              | High training accuracy, moderate validation accuracy; potential for improvement |
| ModelConv3D3 - Experiment 8 - Frames-16, Epoch-20 | 27,515,205       | 3,926,341            | Yes           | ResNet50         | 23,588,864               | 41.17%            | 25.00%              | Low validation accuracy indicates potential issues with the model or data |

## VGG16 Transfer Learning with LSTM & GRU Summary of Results

| Experiment                                         | Total Parameters | Trainable Parameters | Augmentation | Transfer Learning | Non-trainable Parameters | Training Accuracy | Validation Accuracy | Observations                                                                                                 |
|----------------------------------------------------|------------------|----------------------|---------------|-------------------|--------------------------|-------------------|---------------------|--------------------------------------------------------------------------------------------------------------|
| ModelConv3D4 - Conv3D - VGG16 & LSTM Architecture | 16,481,029       | 1,765,189            | True          | Yes               | 14,715,840               | 85.56%            | 82.00%              | Good training accuracy and moderate validation accuracy. Suggests effective feature extraction with VGG16, but additional improvements may be needed for validation accuracy. |
| ModelConv3D5 - Conv3D - ResNet50 & LSTM Architecture | 16,334,341       | 1,618,501            | True          | Yes               | 14,715,840               | 96.64%            | 94.00%              | Excellent training accuracy and high validation accuracy. The model effectively utilizes ResNet50 for feature extraction, resulting in strong performance across both training and validation phases. |

## Team

Jitesh Rathod  [https://www.linkedin.com/in/jitesh-rathod/]
Asheesh Jakhmola
