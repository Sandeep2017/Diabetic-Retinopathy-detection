# Diabetic-Retinopathy-detection
[![forthebadge](https://forthebadge.com/images/badges/made-with-python.svg)](https://www.python.org/)
[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://linkedin.com/in/sandeep-ghosh)

>>>>>> ### Imagine being able to detect blindness even before it happned  !!

Our experiments with Diabetic Retinopathy Detection.
This is an ongoing project and this repository is constantly getting updated.

## Overview
* [Contributors](#Contributors)
* [Introduction](#Introduction)
* [Dataset Used](#Dataset-Used)
* [Augmentation & Preprocessing](#Augmentation-and-Preprocessing)
* [Network Architecture](#Network-Architecture)
* [Loss Function & Optimizer](#Loss-Function-and-Optimizer)
* [Training setup](#Training-setup)
* [Evaluation Metric](#Evaluation-Metric)
* [Results](#Results)

### Contributors:
This project is created by the joint efforts of
* [Subham Singh](https://github.com/Subham2901)
* [Sandeep Ghosh](https://github.com/Sandeep2017)

### Introduction:
Diabetic retinopathy is an eye condition that can cause vision loss and blindness in people who have diabetes if left untreated. It affects blood vessels in the retina. As reported, DR (Diabetic Retinopathy) is the leading cause of blindness in the working-age population of the developed world. 
Currently, detection DR is a time-consuming process that requires a trained clinician to examine and evaluate digital colour fundas photographs of the retina. By the time human readers submit their reviews, often a day or two later, the delayed resuslts lead to lost follow up, miscommunication, and delayed treatment.

Clinicians can identify DR by the presence of lesions associated with the vascular abnormalities caused by the disease. While this approach is effective, its resource demands are high. The expertise and equipment required are often lacking in areas where the rate of diabetes in local populations is high and DR detection is most needed. As the number of individuals with diabetes continues to grow, the infrastructure needed to prevent blindness due to DR will become even more insufficient.

The need for a comprehensive and automated method of DR screening has long been recognized, and previous efforts have made good progress using image classification, pattern recognition, and machine learning. Here, we too are trying to develop a Convolutional Neural Network which can automate the process of DR detection.

### Dataset Used:
We have used multiple DR datasets that are publicly available.
They are: 

* [Deep Drid](https://isbi.deepdr.org/)
* [APTOS 2019 Blindness detection challenge](https://www.kaggle.com/c/aptos2019-blindness-detection)
* [Kaggle 2015 DR detection challenge](https://www.kaggle.com/c/diabetic-retinopathy-detection)

DR can be graded into 5 conditions:
> 0 - No DR

> 1 - Mild 

> 2 - Moderate

> 3 - Severe

> 4 - Proliferative DR

Sample training images from DeepDrid dataset along with their respective grades are given below:

DeepDrid train images
:-------------------------:|
![](https://github.com/Sandeep2017/Diabetic-Retinopathy-detection/blob/master/Images/1.PNG)

### Challenges:
* The dataset has high class imbalance.
* Images contain artifacts.
* Images are out of focus, under/overexposed.
* Lighting conditions are vastly different. 

### Augmentation and preprocessing:
The training data was augmented on the fly using the [Albumentations library](https://albumentations.ai/).
A strong combination of different types of image augmentations were applied with varied probabilities. They were:
* Random Flips.
* Transpose.
* Random Rotations.
* Optical Distortion.
* RGB Shift.
* Random Gamma.
* Random Brightness & contrast.

Along with the above mentioned augmentations, every image in the training and testing sets underwent a Histogram Equalization preprocessing step, i.e, CLAHE (Contrast Limited Adaptive Histogram Equalization) to compensate for the varying lighting conditions, brightness, contrast, etc.

### Network Architecture
Right now we are trying out transfer learning with DenseNet201 and EfficientNet B7. Also we have tried out using separable conv networks and VGG style networks.
The final architecture will be updated soon !

### Loss Function and Optimizer:
Weighted Categorical crossentropy is the loss function that we are using. Also we are trying class oversampling.
Adam with default parameters is the optimizer of our choice.

### Evaluation Metric:
We are using Quadratic Weighted Kappa as our metric.

```Python
from sklearn.metrics import cohen_kappa_score
def kappa(y_true, y_pred):
  y_true = np.argmax(y_true, axis=-1)
  y_pred = np.argmax(y_pred, axis=-1)
  kappa_score = cohen_kappa_score(y_true, y_pred, weights='quadratic')
  return kappa_score

def tf_kappa(y_true, y_pred):
  kappa_score = tf.py_function(func=kappa, inp=[y_true, y_pred], Tout=tf.float32)
  return kappa_score
 ```
