# Phase 4: Probabilistic & Multimodal Atlases

> Corresponding to **Section 2.4** of the review paper.

## 📖 Overview
As imaging hardware evolved (e.g., 3T/7T scanners), researchers moved beyond single-modality structural templates to capture the complex biological reality of the neonatal brain.

* **Probabilistic Atlases (Sec 2.4.1):** Instead of assigning a discrete label to each voxel, these atlases model the *probability distribution* of tissue types (GM/WM/CSF). This effectively handles the "partial volume effects" and blurred boundaries common in neonatal MRI.
* **Multimodal Integration (Sec 2.4.2):** Fusing complementary information—aligning high-contrast structural data (T2w) with microstructural fiber orientation (DTI) and functional networks (fMRI).

## 🛠️ Key Methods & Resources

| Method / Atlas | Year | Author | Focus & Modalities | Verified Links |
| :--- | :--- | :--- | :--- | :--- |
| **JHU Neonatal Atlas** | 2011 | Oishi et al. | **Multimodal.** Integration of T1, T2, and DTI tensors into a unified template. | [Paper](https://pubmed.ncbi.nlm.nih.gov/21276861/) \| [NITRC Download](https://www.nitrc.org/projects/uofm_jhu_atlas) |
| **4D Probabilistic Atlas** | 2011 | Kuklisova-Murgasova et al. | **Probabilistic.** Uses Gaussian Mixture Models (GMM) to create dynamic tissue probability maps. | [Paper](https://pubmed.ncbi.nlm.nih.gov/20969966/) \| [Brain-Development.org](https://brain-development.org/brain-atlases/neonatal-brain-atlases/) |
| **UNC/UMN BCP Atlas** | 2022 | Chen et al. | **High-Res Probabilistic.** Built from the Baby Connectome Project (BCP) with 542 scans. | [Paper](https://doi.org/10.1016/j.neuroimage.2022.119097) \| [NITRC Download](https://www.nitrc.org/projects/uncbcp_4d_atlas/) |
| **dHCP Parametric Atlas** | 2021 | Uus et al. | **Multimodal Growth.** Models intensity and diffusion (NODDI) changes using Gompertz growth functions. | [Paper](https://pubmed.ncbi.nlm.nih.gov/34220423/) \| [dHCP Data](http://www.developingconnectome.org/data-release/third-data-release/) |
| **Multi-Resolution Atlas** | 2023 | Li et al. | **Unified Representation.** Unified anatomy, connectivity, and function from dHCP data. | [Paper](https://pubmed.ncbi.nlm.nih.gov/37003446/) \| [dHCP Project](http://www.developingconnectome.org/) |

## 🧪 Core Concepts

### 1. Probabilistic Modeling (GMM)
Unlike static averaging, probabilistic methods model the intensity distribution of a voxel across the population using a mixture of Gaussians:
$$P(y|\theta) = \sum_{k=1}^{K} w_k \mathcal{N}(y | \mu_k, \sigma_k)$$
Where $K$ represents tissue classes (e.g., Cortex, WM, CSF). This provides a "soft" segmentation prior crucial for handling the low contrast in neonatal brains.

### 2. Multimodal Fusion
Integrating DTI (Diffusion Tensor Imaging) requires more than just intensity averaging. It involves **Tensor Reorientation**:
* When the brain image is warped spatially, the diffusion tensors (fiber directions) must also be rotated to remain consistent with the new anatomy.

## 📂 Featured Datasets
This era relies heavily on large-scale public datasets.
* **dHCP (Developing Human Connectome Project):** The gold standard for multimodal neonatal data (Structure + DTI + fMRI).
* **BCP (Baby Connectome Project):** Focuses on longitudinal development from birth to early childhood.
