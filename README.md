# Jailbreaking Deep Models
*A study of adversarial attacks on ImageNet classifiers – Spring 2025 Deep Learning Project*

![Adversarial Examples](https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/Adversarial_Example.svg/800px-Adversarial_Example.svg.png)

---

## Overview

This project investigates the **vulnerability of deep neural networks** to subtle, imperceptible input perturbations. We mount a series of adversarial attacks on a pretrained **ResNet-34** classifier trained on a subset of **ImageNet-1K**, and evaluate their **transferability to DenseNet-121**.

We implement and analyze:

- FGSM (Fast Gradient Sign Method)
- PGD (Projected Gradient Descent)
- Iterative Patch Attacks (PatchPGD)

---

## 🗂️ Project Structure
📁 Jailbreaking-Deep-Models/
├── 📄 report.pdf
├── 📁 data/
│ └── TestDataSet/
├── 📁 adversarial_test_set_1/ # FGSM
├── 📁 adversarial_test_set_2/ # PGD
├── 📁 adversarial_test_set_3/ # PatchPGD


---

## 🧪 Experimental Results

| Dataset                  | ResNet-34 Top-1 | ResNet-34 Top-5 | DenseNet-121 Top-1 | DenseNet-121 Top-5 |
|--------------------------|-----------------|------------------|---------------------|----------------------|
| Original                 | 76.00%          | 94.20%           | 74.80%              | 93.60%               |
| Adversarial Set 1 (FGSM) | **6.20%**       | 35.40%           | 63.60%              | 89.00%               |
| Adversarial Set 2 (PGD)  | **0.00%**       | **2.20%**        | 47.60%              | 81.60%               |
| Adversarial Set 3 (PatchPGD) | 5.40%     | 43.20%           | 65.80%              | 90.40%               |

---

## 📊 Attack Techniques

| Attack | Perturbation | Scope      | ε (budget) | Steps | Notes |
|--------|--------------|------------|------------|-------|-------|
| FGSM   | One-shot     | Whole image | 0.02       | 1     | Gradient sign |
| PGD    | Iterative    | Whole image | 0.02       | 10    | Multi-step FGSM |
| PatchPGD | Iterative | 32×32 patch | 0.5        | 60    | Localized + restarts |

---

## 🧠 Models Used

- 🎯 **ResNet-34** for primary attacks
- 🔁 **DenseNet-121** for transferability evaluation  
All models loaded using `torchvision.models` with pretrained ImageNet-1K weights.
