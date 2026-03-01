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
 
**Figure 1.**  Architecture of the proposed HybDL framework, highlighting key functional phases responsible for breast mammogram examination, Identification, and Morphological Evaluation.

**Morhology Features Transformation Pipeline**: A feature sequencing pipeline is constructed to convert spatial morphological feature maps into structured temporal sequences suitable for LSTM processing. In this pipeline, quantitative shape descriptors extracted from segmented regions, such as area, perimeter, circularity, and eccentricity, are first computed for each image. These features are then organized in chronological order to form multivariate time series vectors. The resulting structured feature sequences serve as input to the LSTM network, enabling it to learn temporal dependencies and model the dynamic progression of tumor morphology over time.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/LSTM.jpg" width="800" height="600">
<p align="center">

**Figure 2.**  Feature sequencing pipeline that transforms spatial morphological features into structured temporal sequences for LSTM based modeling.

# Dataset Description
The dataset is accessible through the [Kaggle Website](https://www.kaggle.com/datasets/anaselmasry/datasetbusiwithgt/data). This dataset consists of a total of *780 breast images*, categorized into *133 normal*, *437 benign*,
and *210 malignant* images. A representation of the dataset is presented in Figure 3. 

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/Distribution.jpg" width="600" height="400">
<p align="center">

**Figure 3.**  Dataset showing normal, benign, and malignant images, each presented with and without their masks.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/CombinedImages.png" width="900" height="700">
<p align="center">

**Figure 4.**  A representation of the original, masks, and overlay for the normal, benign, and malignant images. 

# Data Engineering
The Structural Similarity Index (SSIM) algorithm was applied to the overall dataset as well as to each class separately, namely normal, benign, and malignant images, to measure structural similarity between image pairs. A threshold was determined using the 99th percentile of the SSIM distribution to identify highly similar or duplicate images. Key descriptive statistics, including the minimum, maximum, mean, and standard deviation of SSIM scores, were computed to summarize the similarity characteristics across the entire dataset and within each class.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/Table%201.png" width="700" height="500">
<p align="center">

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/SSIM_Global.png" width="650" height="450">
<p align="center">

**Figure 5.**  Global SSIM for the overall dataset with a dynamic threshold with a 99th percentile. 

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/SSIM_PerClass.jpg" width="700" height="500">
<p align="center">

**Figure 6.**  Classwise SSIM for the normal, benign, and malignant images with a dynamic threshold with a 99th percentile. 

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/UniqueDuplicateImages.png "width="700" height="500">
<p align="center">

**Figure 7.**  Formation of two distinct datasets based on the SSIM algorithm.

# Results
## Performance Evaluation

The performance of the proposed **HybDL framework** is evaluated for both breast tumor detection and temporal morphology analysis.

---

### 1. Tumor Detection Evaluation

The detection performance is assessed using two dataset configurations:

- **WDD** — With Duplicate Dataset  
- **WODD** — Without Duplicate Dataset  

The following evaluation metrics are used:

- Accuracy  
- Precision  
- Recall  
- F1-score  
- Area Under the ROC Curve (AUC)  
- Dice Coefficient  

After validating performance on the WODD dataset, a comparative analysis is conducted against state-of-the-art breast tumor detection models to assess robustness and generalization capability.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/Performance_WODD_WDD.png"width="700" height="500">
<p align="center">

**Figure 8.**  Performance analysis of the proposed HybDL model using accuracy, precision, recall, and F1-measure across the training, validation, and testing subsets of the WDD and WODD.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/Dice_Coefficient_WODD_WDD.png"width="700" height="500">
<p align="center">

**Figure 9.**  Dice coefficient of the proposed HybDL for benign and malignant on training, validation, and testing sets 
tumor detection.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/ROCAUCPerClass.jpg"width="800" height="600">
<p align="center">

**Figure 10.**  Area under curve (AUC) performance of the proposed HybDL on WODD and WDD datasets. (a) AUC performance on the WODD dataset and (b) AUC performance on the WDD dataset.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/ConfusionMatrix.png"width="800" height="600">
<p align="center">

**Figure 11.**  Classwise confusion matrix of the proposed HybDL on WODD and WDD datasets. (a) & (c) Background class on WODD & WDD, (b) & (d) Benign class on WODD & WDD, and (c) & (e) Malignant class on WODD & WDD.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/PerformanceImprovement.jpg"width="700" height="500">
<p align="center">

**Figure 12.**  Performance improvement of the proposed HybDL over state-of-the-art methods ( DCNN [87], EDCNN [88], ADU-Net [89], DNBCD [90], U-KAN [91], VGG19 [92], CAR-Model [93], FMRNet [94], and ViT-CNN [95]) for breast tumor detection.


---

### 2. Morphological Evaluation

The morphology modeling performance of the LSTM module is evaluated using regression metrics:

- Mean Absolute Error (MAE)  
- Mean Squared Error (MSE)  
- Root Mean Squared Error (RMSE)  
- Coefficient of Determination (R²)  

These metrics measure the model’s ability to capture temporal tumor growth patterns and shape evolution.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/MorphologyFeaturesDistribution.jpg"width="900" height="700">
<p align="center">

**Figure 13.**  A representation of the different morphology features of the training, validation, and test sets.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/RegressionPredictionFit.png"width="800" height="600">
<p align="center">

**Figure 14.**  Comparative analysis of the proposed HybDL with WODD and WDD using parity plots and residual histograms.

<p align="center">
<img src="https://github.com/shashwatshukla10/HyDL-Framework-for-Breast-Cancer-Detection-and-Morphology-Evaluation/blob/main/Figures/RegressionMSE.jpg"width="700" height="500">
<p align="center">

**Figure 15.**  Training and validation MSE convergence of the HybDL model on two datasets. (a) HybDL with WODD and (b) HybDL with WDD.

---

### 3. Statistical Validation

To ensure reliability and robustness, all results are further validated using a **95% confidence interval**.

---

### 4. Computational Analysis

The computational complexity of the proposed HybDL framework is analyzed to verify its suitability for real-world clinical applications.

---

A comprehensive summary of all results is provided in the figures and tables included in this repository.
