# AI-Assisted Chest X-ray Diagnosis using Deep Learning, Explainable AI (Grad-CAM), and RAG

## Project Overview

This project presents an AI-assisted Chest X-ray Interpretation System that combines:

* Deep Learning for disease classification
* Explainable AI (Grad-CAM) for visual explanations
* Retrieval-Augmented Generation (RAG) for grounded medical interpretations

The system was developed using the NIH ChestX-ray14 dataset and evaluates multiple deep learning architectures for multi-label thoracic disease classification.

---

## Problem Statement

Manual interpretation of chest X-rays requires significant clinical expertise and can be time-consuming. This project aims to develop an automated system capable of:

* Detecting thoracic diseases from chest X-ray images
* Providing explainable predictions through heatmap visualization
* Generating grounded disease explanations using retrieval-based reasoning

---

## Dataset

**Dataset:** NIH ChestX-ray14

* Total Images: 112,120
* Unique Patients: 30,805
* Disease Categories: 14
* Image Format: PNG

### Disease Classes

1. Atelectasis
2. Cardiomegaly
3. Effusion
4. Infiltration
5. Mass
6. Nodule
7. Pneumonia
8. Pneumothorax
9. Consolidation
10. Edema
11. Emphysema
12. Fibrosis
13. Pleural Thickening
14. Hernia

---

## Data Preprocessing

* Image resizing to 224 × 224
* Grayscale conversion
* Tensor transformation
* Normalization
* Multi-label binary encoding
* Dataset sampling (5,000 images for experimentation)

---

## Models Implemented

### 1. Custom CNN

Architecture:

* Conv2D
* ReLU
* MaxPooling
* Conv2D
* ReLU
* MaxPooling
* Fully Connected Layer
* Output Layer (14 classes)

Training Configuration:

* Loss Function: BCEWithLogitsLoss
* Optimizer: Adam
* Learning Rate: 0.001
* Epochs: 5

---

### 2. ResNet18 (Transfer Learning)

Pretrained on ImageNet.

Advantages:

* Faster convergence
* Better feature extraction
* Improved generalization

Training Configuration:

* Loss Function: BCEWithLogitsLoss
* Optimizer: Adam
* Learning Rate: 0.0001
* Epochs: 5

---

### 3. VGG19 (Transfer Learning)

Pretrained on ImageNet.

Advantages:

* Deep architecture
* Strong feature extraction capability
* Effective transfer learning

Training Configuration:

* Loss Function: BCEWithLogitsLoss
* Optimizer: Adam
* Learning Rate: 0.0001
* Epochs: 5
* Batch Size: 16

---

## Explainable AI using Grad-CAM

Grad-CAM was used to visualize image regions that contributed most strongly to model predictions.

Benefits:

* Improves model transparency
* Helps verify predictions visually
* Increases trust in AI-assisted diagnosis

---

## Retrieval-Augmented Generation (RAG)

A lightweight RAG framework was implemented to provide grounded medical explanations.

Workflow:

1. Predict disease using ResNet18
2. Retrieve relevant medical knowledge
3. Generate disease explanation
4. Present interpretation with disclaimer

Example:

Predicted Disease: Pneumothorax

Explanation:
Collapsed lung caused by air leakage.

---

## Evaluation Metrics

* AUROC (Area Under ROC Curve)
* PR-AUC (Precision Recall Area Under Curve)
* Precision
* Recall
* F1 Score

---

## Results

### Model Comparison

| Model      | Mean AUROC | Mean PR-AUC    |
| ---------- | ---------- | -------------- |
| Custom CNN | 0.6741     | Not Calculated |
| ResNet18   | 0.7340     | 0.1876         |
| VGG19      | 0.6674     | 0.1228         |

### Best Performing Model

**ResNet18**

* Mean AUROC: 0.7340
* Mean PR-AUC: 0.1876

---

## Top Disease-wise AUROC (ResNet18)

| Disease       | AUROC  |
| ------------- | ------ |
| Cardiomegaly  | 0.8544 |
| Edema         | 0.8482 |
| Pneumothorax  | 0.8454 |
| Consolidation | 0.8322 |
| Effusion      | 0.8192 |

Lowest Performing Disease:

* Pneumonia (~0.51 AUROC)

---

## Technologies Used

### Programming

* Python

### Deep Learning

* PyTorch
* Torchvision

### Data Processing

* NumPy
* Pandas

### Visualization

* Matplotlib

### Explainability

* Grad-CAM

### Retrieval-Augmented Generation

* Custom Retrieval Pipeline

### Environment

* Google Colab
* NVIDIA T4 GPU

---
## Repository Contents

- AI_Assisted_ChestXray.ipynb
- AI_Assisted_Chest_Xray_Report.pdf
- gradcam_example.png
- resnet18_results.csv
- model_comparison_summary.csv
- README.md
---

## Conclusion

This project successfully demonstrates an end-to-end AI-assisted chest X-ray interpretation pipeline integrating:

* Deep Learning
* Transfer Learning
* Explainable AI
* Retrieval-Augmented Generation

Among all evaluated models, ResNet18 achieved the highest overall performance and was selected as the final model for disease interpretation.

---

## Future Work

* Train on the complete NIH dataset
* Implement DenseNet121 and EfficientNet
* Integrate Large Language Models (LLMs)
* Deploy using FastAPI and Streamlit
* Experiment tracking with MLflow / Weights & Biases
* Real-world clinical deployment
