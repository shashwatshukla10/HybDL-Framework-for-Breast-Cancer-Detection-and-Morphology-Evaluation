# HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation

This repository contains resources related to the **A Hybrid U-Net and LSTM Framework for Breast Cancer Detection and Morphology Evaluation** and consists of three folders.

**Dataset** This folder contains the dataset utilized in this study.

**Code**: This folder provides two Jupyter Notebook files (.ipynb) that cover the implementation of the data engineering and hybrid DL-BHA approach.

**Figures**: This folder provides most of the results presented in the paper.

A detailed description of the working mechanism, methodology, and results of the research is included within the repository files.

# System Model of the Proposed HybDL
The system model of the proposed HybDL consists of three functional phases, as detailed below.

**Data Phase**: The data phase begins with an initial consultation with a physician, during which the patient’s symptoms, medical history, and clinical observations are discussed. Based on this evaluation, the physician may recommend further diagnostic tests, such as digital mammography, to assess any suspected abnormalities. The digital mammogram examination then generates high resolution breast images, which serve as the primary input data for subsequent analysis in the proposed framework.

**Identification Phase**: In this phase, a U-Net model is employed to segment breast tissue into normal, benign, and malignant regions. The segmentation focuses on the regions of interest, enabling the network to learn meaningful spatial features. The model follows an encoder decoder structure, where convolutional layers extract features, max pooling layers reduce spatial dimensions, and upsampling layers restore resolution. Activation functions such as ReLU introduce nonlinearity, allowing the network to effectively distinguish between different tissue types.

**Morphology Phase**: The segmented output is passed to the morphology phase, where key shape based features such as area, perimeter, circularity, and eccentricity are calculated using mathematical formulations. These quantitative features are then fed into a multivariate LSTM network to model temporal changes in tumor characteristics, including growth patterns and shape progression. The resulting predictions provide measurable insights into tumor behavior, supporting clinical decision making and patient follow up.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/SystemModel.jpg" width="800" height="600">
<p align="center">
 
**Fig.1.**  Architecture of the proposed HybDL framework, highlighting key functional phases responsible for breast mammogram examination, Identification, and Morphological Evaluation.
