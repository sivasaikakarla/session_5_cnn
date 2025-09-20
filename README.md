# 🧠 MNIST Challenge: Journey to 99.4% Accuracy

This repository documents the process of building and optimizing a **Convolutional Neural Network (CNN)** to achieve **99.4% accuracy** on the MNIST dataset under strict constraints.

## 🎯 Challenge Constraints
- **Total Parameters:** < 20,000  
- **Training Epochs:** < 20  
- **Required Techniques:** Batch Normalization, Dropout, and Global Average Pooling (GAP)  

The project demonstrates how to iteratively diagnose model performance, apply modern deep learning techniques, and fine-tune hyperparameters to transition from a strong baseline to a state-of-the-art solution.

---

## 🏆 Final Model Performance
| Requirement | Status & Result |
|-------------|-----------------|
| **Peak Test Accuracy > 99.4%** | ✅ 99.40% (Achieved at Epoch 19) |
| **Parameters < 20k** | ✅ 19,664 |
| **Epochs < 20** | ✅ 19 |
| **Use of Batch Normalization** | ✅ Yes |
| **Use of Dropout** | ✅ Yes |
| **Use of GAP Layer** | ✅ Yes |

Final model details are in **`4th_approach.ipynb`**.

---

## 📊 Comparative Analysis of the Four Approaches

| Metric | Approach 1 (Baseline) | Approach 2 (Capacity Up) | Approach 3 (Heavy Regularization) | Approach 4 (Final Tuning) |
|--------|------------------------|---------------------------|------------------------------------|----------------------------|
| **Notebook File** | `1st_approach.ipynb` | `2nd_approach.ipynb` | `3rd_approach.ipynb` | `4th_approach.ipynb` |
| **Peak Test Accuracy** | 98.84% | 98.60% | 98.96% | **99.40%** |
| **Total Parameters** | 7,340 | 10,128 | 19,664 | 19,664 |
| **Batch Normalization** | ✅ | ✅ | ✅ | ✅ |
| **Dropout** | ✅ | ✅ | ✅ | ✅ |
| **GAP Layer** | ✅ | ✅ | ✅ | ✅ |
| **Key Change** | Initial design | More params, OneCycleLR | AdamW, Cutout, Heavy Reg. | Relaxed weight decay |
| **Observation** | Underfitting | Overfitting | Over-regularized | Balanced & Optimized |

---

## 🔬 Detailed Iteration Breakdown

### **Approach 1: The Baseline (98.84%)**
- **Goal:** Establish a lightweight baseline model with required techniques.  
- **Method:** Simple CNN with 7.3k parameters, Batch Norm, Dropout, GAP, and StepLR scheduler.  
- **Analysis:** Strong start but hit a ceiling → **Underfitting**.  

---

### **Approach 2: Increasing Capacity (98.60%)**
- **Goal:** Address underfitting by increasing capacity.  
- **Method:** 10.1k parameters, RandomAffine augmentation, OneCycleLR scheduler.  
- **Analysis:** Accuracy dropped → **Overfitting** from added capacity without stronger controls.  

---

### **Approach 3: Heavy Regularization (98.96%)**
- **Goal:** Use full parameter budget with strong regularization.  
- **Method:** 19.7k parameters, **AdamW** optimizer (`weight_decay=0.01`), Cutout augmentation.  
- **Analysis:** Accuracy improved, but model was **slightly over-regularized**.  

---

### **Approach 4: Final Fine-Tuning (99.40%)**
- **Goal:** Balance model capacity and regularization.  
- **Method:** Reduced `weight_decay` from `0.01 → 0.001`.  
- **Analysis:** Accuracy climbed past **99.4%** within 19 epochs. 🎉  


