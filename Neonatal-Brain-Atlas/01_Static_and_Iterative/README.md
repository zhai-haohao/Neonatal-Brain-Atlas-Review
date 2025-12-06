# Phase 1 & 2: Static and Iterative Template Construction

> Corresponding to **Section 2.1 and 2.2** of the review paper.

## 📖 Overview
This section covers the foundational evolution of neonatal atlas construction:
1. **Static Templates (Phase 1):** Early approaches that aligned population data to a single subject using linear (rigid/affine) transformations (Kazemi et al., 2007; Oishi et al., 2011).
   * *Limitation:* Highly biased towards the chosen reference subject (Gholipour et al., 2017).

2. **Iterative Templates (Phase 2):** The transition to groupwise, non-linear registration (e.g., ANTs SyN) to create an "average" brain shape (Avants et al., 2008; Schuh et al., 2018).
   * *Advantage:* Removes reference bias and progressively sharpens anatomical details through iterative averaging loops (Jia et al., 2010).

## 🛠️ Key Methods & Tools

| Category | Method | Year | Core Algorithm | Availability |
| :--- | :--- | :--- | :--- | :--- |
| **Static** | **Single-Subject** | 2007 | Rigid/Affine Registration | [Paper](https://www.sciencedirect.com/science/article/abs/pii/S1053811998903950)  |
| **Iterative** | **ABSORB** | 2010 | Self-organized Registration & Bundling | [Paper](https://www.sciencedirect.com/science/article/abs/pii/S1053811910002806) |
| **Iterative** | **ANTs (SyN)** | 2013 | Symmetric Diffeomorphic (SyN) | [GitHub](https://github.com/ANTsX/ANTs) |

> **Note:** While older methods like ABSORB pioneered the field, **ANTs (Advanced Normalization Tools)** has become the standard implementation for iterative atlas construction due to its open-source availability and robust pipeline.

## 💻 Practical Usage: How to Build an Iterative Atlas

The review paper highlights the **ANTs** pipeline (`antsMultivariateTemplateConstruction2.sh`) as a representative workflow for this phase.

If you have installed ANTs, you can reproduce the "Iterative Loop" (Figure 1 in the paper) using the following command:

```bash
# Basic usage of the ANTs template construction script
# This script performs the Registration -> Averaging -> Update loop automatically.

antsMultivariateTemplateConstruction2.sh \
  -d 3 \                    # Dimension: 3D images
  -o OutputPrefix_ \        # Prefix for generated template files
  -i 4 \                    # Number of iterations (Review suggests ~4 for convergence)
  -g 0.25 \                 # Gradient step size for update
  -j 8 \                    # Number of CPU cores
  -c 2 \                    # Parallel control (0=serial, 2=PAD, etc.)
  -k 1 \                    # Number of modalities (1 = T1 or T2 only)
  -w 1 \                    # Weight for the modality
  -r 1 \                    # Perform initial rigid alignment? (1=Yes)

  Subject_*.nii.gz          # Input images (wildcard)
