### ARIN5103 Project: Represent, Compare, and Learn: A Similarity-Aware Framework for Class-Agnostic Counting (Ablation Studies)  

---

### 1. Project Overview

This repository contains the **experiments and logs** for an ARIN5103 course project, built on top of the CVPR 2022 paper:  
**“Represent, Compare, and Learn: A Similarity-Aware Framework for Class-Agnostic Counting”** (BMNet / BMNet+).

The paper addresses **Class-Agnostic Counting (CAC)**: given a few exemplars of a category, the model counts all instances of that category in a query image. The key idea is a **similarity-aware framework** that **jointly learns feature representations and similarity metrics** in an end-to-end manner, instead of using a fixed inner product as similarity.

Core components:

- **BMNet (Bilinear Matching Network)**  
  - Learnable **bilinear similarity metric** instead of fixed inner product  
  - Joint optimization of representation and similarity metric  

- **BMNet+** (BMNet with three extensions)  
  - **Self-Similarity Module (SS)**: self-attention across instances of the same category to reduce intra-class variation (scale, pose, etc.)  
  - **Dynamic Similarity Metric (DSM)**: exemplar-conditioned channel attention to focus on category-specific patterns  
  - **Similarity Loss (SL)**: direct supervision on the similarity map, encouraging high similarity for target regions and low similarity for background

---

### 2. Repository Structure

- **`B1_baseline/`**  
  - Corresponds to the **baseline BMNet**

- **`ml_DSM_only/`**  
  - Only **Dynamic Similarity Metric (DSM)** is enabled.  

- **`ml_SE_only/`**  
  - Only **Scale Embedding (SE)** is enabled.  

- **`ml_SS_only/`**  
  - Only **Self-Similarity (SS)** is enabled.  

- **`VIT_backbone/`**  
  - Experiments using a **ViT/Transformer-based backbone** instead of ResNet-50 as the feature extractor.  
  - The ViT version is vit_base_patch-16_224

- **`-+++`, `+-++`, `++-+`, `+++ -`, `++++` and similar folders**  
  - These symbol names typically encode **on/off combinations of core modules** (e.g., SS, DSM, SL, SE).  
  - The exact meaning of each combination is specified in the corresponding `config.yaml`.  
  - They can be mapped to the ablations in Table 4 (B1–B10) of the paper to see how each module contributes to validation and test performance.

