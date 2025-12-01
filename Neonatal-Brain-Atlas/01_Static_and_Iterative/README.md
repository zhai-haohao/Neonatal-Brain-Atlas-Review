# Phase 1 & 2: Static and Iterative Template Construction

> Corresponding to **Section 2.1 and 2.2** of the review paper.

## 📖 Overview
This section covers the foundational evolution of neonatal atlas construction:
1.  [cite_start]**Static Templates (Phase 1):** Early approaches that aligned population data to a single subject using linear (rigid/affine) transformations[cite: 36, 38].
    * [cite_start]*Limitation:* Highly biased towards the chosen reference subject[cite: 48].
2.  [cite_start]**Iterative Templates (Phase 2):** The transition to groupwise, non-linear registration (e.g., ANTs SyN) to create an "average" brain shape[cite: 53, 64].
    * [cite_start]*Advantage:* Removes reference bias and progressively sharpens anatomical details through iterative averaging loops[cite: 90, 91].

## 🛠️ Key Methods & Tools

| Category | Method | Year | Core Algorithm | Availability |
| :--- | :--- | :--- | :--- | :--- |
| **Static** | **Single-Subject** | 2007 | Rigid/Affine Registration | N/A (Concept only) |
| **Iterative** | **ABSORB** | 2010 | Self-organized Registration & Bundling | [Paper](https://pubmed.ncbi.nlm.nih.gov/20139015/) |
| **Iterative** | **ANTs (SyN)** | 2013 | Symmetric Diffeomorphic (SyN) | [GitHub](https://github.com/ANTsX/ANTs) |

> [cite_start]**Note:** While older methods like ABSORB [cite: 67] [cite_start]pioneered the field, **ANTs (Advanced Normalization Tools)** [cite: 69] has become the standard implementation for iterative atlas construction due to its open-source availability and robust pipeline.

## 💻 Practical Usage: How to Build an Iterative Atlas

[cite_start]The review paper highlights the **ANTs** pipeline (`antsMultivariateTemplateConstruction2.sh`) as a representative workflow for this phase[cite: 74].

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