# CIFAR-10 Transfer Learning with MobileNetV2

## Overview

This project demonstrates **transfer learning and fine-tuning using MobileNetV2** for image classification on the **CIFAR-10 dataset**.

The project investigates whether a pretrained CNN can outperform a CNN trained from scratch. It also compares feature extraction, fine-tuning, and hyperparameter tuning to determine the best-performing approach.

## Dataset

The project uses the **CIFAR-10 dataset**, which contains:

* 60,000 color images
* Image size: 32 × 32
* 10 classes
* 50,000 training images
* 10,000 test images

The CIFAR-10 images are resized from **32 × 32 to 96 × 96** to match the MobileNetV2 input configuration used in this project.

## Model

The project uses **MobileNetV2 pretrained on ImageNet**.

The pretrained convolutional layers provide learned visual features that can be reused for CIFAR-10 classification. The original ImageNet classification layer is removed using `include_top=False`, and a new classification head is added for the 10 CIFAR-10 classes.

## Experiments

Three approaches were evaluated:

### 1. Feature Extraction

The pretrained MobileNetV2 base was used as a feature extractor while its pretrained layers remained frozen.

**Test Accuracy: 82.10%**

### 2. Fine-Tuning

Selected layers of the pretrained MobileNetV2 model were unfrozen and trained further on CIFAR-10.

**Test Accuracy: 82.40%**

### 3. Hyperparameter Tuning

Hyperparameter tuning was performed to identify a better-performing configuration for the transfer-learning model.

**Test Accuracy: 83.73%**

This was the **best-performing model in Project B**.

## Final Results

| Approach                     | Test Accuracy |
| ---------------------------- | ------------: |
| Feature Extraction           |        82.10% |
| Fine-Tuning                  |        82.40% |
| Hyperparameter-Tuned Model   |    **83.73%** |
| CNN from Scratch — Project A |        67.72% |

## Project A vs Project B

Project A used a CNN trained from scratch on CIFAR-10 and achieved **67.72% test accuracy**.

Project B used transfer learning with MobileNetV2 and achieved **83.73% test accuracy** after hyperparameter tuning.

This represents an improvement of approximately **16 percentage points** over the CNN trained from scratch.

The result demonstrates the practical benefit of using a pretrained CNN for image classification instead of learning all visual features from scratch.

## Error Analysis

After training the final model, error analysis was performed using:

### Confusion Matrix

The confusion matrix was used to identify which CIFAR-10 classes were classified correctly and which classes were frequently confused with each other.

### Misclassified Images

Misclassified test images were visualized to inspect examples where the model made incorrect predictions.

The final evaluation showed:

* **Test Loss:** 0.4863
* **Test Accuracy:** 83.73%

Out of 6,000 images in the evaluated holdout set, **976 were misclassified**.

## Final Model

The final tuned model was saved as:

```text
cifar10_transfer_learning_final.keras
```

The saved model was loaded again and evaluated on the same holdout/test data to verify that the saved model reproduced the final performance.

## Technologies Used

* Python
* TensorFlow / Keras
* MobileNetV2
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Keras Tuner

## Key Learning Outcomes

Through this project, the following concepts were explored:

* Transfer learning
* Pretrained CNNs
* ImageNet pretrained weights
* Feature extraction
* Fine-tuning
* Hyperparameter tuning
* Model evaluation
* Confusion matrices
* Misclassified image analysis
* Saving and loading Keras models
* Comparing a pretrained model with a CNN trained from scratch

## Conclusion

The experiments show that **transfer learning with MobileNetV2 significantly improved CIFAR-10 classification performance compared with the CNN trained from scratch in Project A**.

Among the approaches tested in Project B, the **hyperparameter-tuned model achieved the highest test accuracy of 83.73%** and was selected as the final model.
