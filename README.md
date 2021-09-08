# LONGL-Net

This repository contains the Pytorch implementation for:

**LONGL-Net: A New Temporal Correlation Structure Guided Deep Learning Framework for Predicting Longitudinal Age-related Macular Degeneration Severity**<br/>Alireza Ganjdanesh, Jipeng Zhang, Emily Chew, Ying Ding, Wei Chen&dagger;, Heng Huang&dagger;

<div align="center">
    <img style="display: inline" src=./Figures/LongitudinalPred.png width = '381px' height = '238px'>
    <img style="display: inline" src=./Figures/ProgressedMainText1.png width = '381px' height = '238px'>
</div>
<div align="center">
    <img style="display: inline" src=./Figures/saliency.png width = '381px' height = '498px'>
</div>

**Abstract:** Age-related Macular Degeneration (AMD) is the principal cause of blindness in developed countries, and its prevalence will increase to 288 million people in 2040. Therefore, automated grading and prediction methods can be highly beneficial for recognizing susceptible subjects to late-AMD by enabling clinicians to start preventive actions for them. Clinically, AMD severity grade is quantified by Color Fundus Photographs (CFP) of the retina, and many machine learning based methods have been developed for grading AMD severity. However, very few models were developed to predict the longitudinal progression status, i.e. the future late-AMD risk prediction based on the current CFP, which is more clinically interesting. To address this challenge, in this paper, we propose a new deep neural network based classification model (LONGL-Net) which can simultaneously tackle both grading the current CFP and predicting the longitudinal outcome, i.e., whether the subject will be in late-AMD in a future time point. We design a new temporal-correlation-structure guided Generative Adversarial Network (GAN) model that learns the interrelations of temporal changes in CFPs of the subjects in consecutive time points, which enables us to perform longitudinal prediction for CFPs corresponding to the classifier’s outcome, and by doing so, provides interpretability for the classifier’s decisions for ophthalmologists by forecasting the changes in AMD symptoms in the future CFPs. We used about 30,000 CFP images from 4,628 participants in the Age-Related Eye Disease Study (AREDS), the largest longitudinal dataset available for AMD. Our classifier showed averaged 0.905 (95% confidence interval 0.886 - 0.922) Area Under the Curve (AUC) and 0.762 (95% confidence interval 0.733 – 0.792) accuracy on 3 class classification problem of simultaneously grading current time point’s AMD condition and predicting late AMD progression of the subject in the future time point. We further validated our model on the UK Biobank dataset, where our model showed average 0.905 accuracy and 0.797 sensitivity in grading 300 CFP images.

## Installation

#### Data Preparation
Please refer to [`Data`](./Data) directory for detailed data preparation steps.

#### Dependencies
- Python 3.7 
- PyTorch + Torchvision
- Pytorch Lightning (for data preparation)
- Tensorflow
- Scikit-learn + Scikit-image
- PIL

## Code Overview
- [`main_classifier.py`](main_classifier.py): train the classification model with different time gap values.
- [`main_evaluate_classifier.py`](main_evaluate_classifier.py): code for evaluating the trained classification model's checkpoints and obtaining their performance confidence interval.
- [`main_binary_classifier.py`](main_binary_classifier.py): train the a binary classifier to grade whether its input fundus image being in advanced AMD or not.
- [`main_UKB.py`](main_UKB.py): evaluate trained classification model on the independent UK Biobank dataset.
- [`main_next_step_GAN.py`](main_next_step_GAN.py): train the GAN model.
- [`main_evaluate_GAN.py`](main_evaluate_GAN.py): quantitive evaluation of the trained GAN models.
- [`main_longitudinal_image_prediction.py`](main_longitudinal_image_prediction.py): code for longitudinal prediction of fundus images of the subjects using the trained GAN models' checkpoints.
- [`main_visualization.py`](main_visualization.py): plotting the saliency maps of the outputs of the classification model.
- [`main_resize_images.py`](main_resize_images.py): code for preprocessing images in AREDS and UK Biobank datasets.

### Trained Checkpoint Models
All of our trained checkpoint models are available [here](https://drive.google.com/drive/folders/1fGw8NEiO32e0S5DriuxrI7nbySyNi-gk?usp=sharing). Please download and put them in their corresponding folder in the [`checkpoints`](Models/checkpoints) directory.

## Contact

If you have any questions, please feel free to contact us through email (alireza.ganjdanesh@pitt.edu) or GitHub issues.
