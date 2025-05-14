# Deep Learning Project: Jailbreaking Deep Models

## Overview

This project explores the vulnerability of deep image classification models to adversarial attacks. We focus on ResNet-34 and DenseNet-121 pre-trained on ImageNet-1K, and evaluate their robustness to both pixel-wise (L∞) and patch-based (L0) adversarial perturbations. We design, implement, and compare multiple attack strategies including FGSM, PGD (with random start and momentum), targeted attacks, and patch-based attacks. We also evaluate attack transferability to DenseNet-121.

## Tasks Implemented

### Task 1: Baseline Evaluation on ResNet-34

* Loaded pre-trained ResNet-34 model from torchvision.
* Preprocessed test dataset using ImageNet normalization.
* Evaluated model on 500 test images from 100 ImageNet classes.
* Computed Top-1 and Top-5 accuracy.
* Visualized correct and incorrect predictions.

### Task 2: FGSM Attack (Adversarial Test Set 1)

* Implemented Fast Gradient Sign Method with ε = 0.02.
* Verified perturbation bounds (L∞ <= 0.02).
* Visualized adversarial examples and compared with originals.
* Saved 500 adversarial images to `AdversarialTestSet1/`.
* Observed significant drop in classification accuracy.

### Task 3: Improved Pixel-wise Attacks (Adversarial Test Set 2)

* Designed and compared three advanced attacks:

  * Targeted PGD
  * Untargeted PGD with random start
  * Momentum PGD
* Chose best-performing attack based on Top-1 accuracy degradation.
* Saved best 500 adversarial samples to `AdversarialTestSet2/`.
* Visualized differences and attack progression.

### Task 4: Patch-based Attack (Adversarial Test Set 3)

* Implemented targeted PGD within a 32x32 random patch.
* Increased ε = 0.5, α = 0.05, steps = 40.
* Saved 500 adversarial samples to `AdversarialTestSet3/`.
* Visualized attack region and perturbation heatmap.
* Evaluated impact on ResNet-34 accuracy.

### Task 5: Transferability Evaluation on DenseNet-121

* Evaluated DenseNet-121 on:

  * Original test set
  * Adversarial Set 1 (FGSM)
  * Adversarial Set 2 (Improved PGD)
  * Adversarial Set 3 (Patch Attack)
* Reported Top-1 and Top-5 accuracy for all datasets.
* Observed high transferability from pixel-wise attacks, reduced success from patch-based attack.

## Accuracy Summary

Top-1 Accuracy (Original ResNet-34): 70.40%
Top-5 Accuracy (Original ResNet-34): 87.00%

Top-1 Accuracy (DenseNet-121):
- Original: 68.20%
- Adversarial Set 1: 29.20%
- Adversarial Set 2: 15.60%
- Adversarial Set 3: 42.40%

## Key Takeaways

* Adversarial examples are effective even with imperceptible changes.
* Multiple-step attacks (PGD, momentum) outperform FGSM.
* Patch attacks are challenging but still degrade accuracy.
* Adversarial examples can transfer across architectures.

## Folder Structure

```
DL_Project/
├── TestDataSet/
│   └── TestDataSet/ (original test images)
│   └── labels_list.json
├── AdversarialTestSet1/ (FGSM outputs)
├── AdversarialTestSet2/ (Improved attack outputs)
├── AdversarialTestSet3/ (Patch attack outputs)
├── DL_Project-3.ipynb
└── README.md
```

## Requirements

Install dependencies:

```bash
pip install torch torchvision matplotlib tqdm
```

## Citation

* \[Goodfellow et al., 2015] Explaining and Harnessing Adversarial Examples
* \[Kurakin et al., 2016] Adversarial Examples in the Physical World
* \[Xie et al., 2019] Improving Transferability of Adversarial Examples with Input Diversity

---
Thank You!
