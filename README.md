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

### Introduction
Diabetic retinopathy is an eye condition that can cause vision loss and blindness in people who have diabetes if left untreated. It affects blood vessels in the retina. As reported, DR (Diabetic Retinopathy) is the leading cause of blindness in the working-age population of the developed world. 
Currently, detection DR is a time-consuming process that requires a trained clinician to examine and evaluate digital colour fundas photographs of the retina. By the time human readers submit their reviews, often a day or two later, the delayed resuslts lead to lost follow up, miscommunication, and delayed treatment.

Clinicians can identify DR by the presence of lesions associated with the vascular abnormalities caused by the disease. While this approach is effective, its resource demands are high. The expertise and equipment required are often lacking in areas where the rate of diabetes in local populations is high and DR detection is most needed. As the number of individuals with diabetes continues to grow, the infrastructure needed to prevent blindness due to DR will become even more insufficient.

The need for a comprehensive and automated method of DR screening has long been recognized, and previous efforts have made good progress using image classification, pattern recognition, and machine learning. Here, we too are trying to develop a Convolutional Neural Network which can automate the process of DR detection.

### Dataset Used
We have used multiple DR datasets that are publicly available.
They are: 

* [Deep Drid](https://isbi.deepdr.org/)
* [APTOS 2019 Blindness detection challenge](https://www.kaggle.com/c/aptos2019-blindness-detection)
* [Kaggle 2015 DR detection challenge](https://www.kaggle.com/c/diabetic-retinopathy-detection)
