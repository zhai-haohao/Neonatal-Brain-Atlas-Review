# Phase 5: Deep Learning-Based Template Construction

> Corresponding to **Section 2.5** of the review paper.

## 📖 Overview
This phase represents a paradigm shift from iterative voxel-wise averaging to **data-driven learning**. Deep neural networks (DNNs) are used to either:
1.  **Accelerate Registration:** Replacing slow iterative optimization with fast inference networks (e.g., VoxelMorph).
2.  **Generate Conditional Atlases:** Using Generative Adversarial Networks (GANs) or Diffusion Models to create sharp, attribute-specific templates (e.g., specific age or pathology).
3.  **Implicit Representation (INR):** Modeling the brain as a continuous function $f(x,y,z,t) \rightarrow \text{Intensity}$, independent of image resolution (e.g., CINEMA).

## 🚀 State-of-the-Art Methods & Resources

| Method | Year | Author | Highlights | Links |
| :--- | :--- | :--- | :--- | :--- |
| **VoxelMorph** | 2019 | Dalca et al. | **Unsupervised Registration.** The foundation for most DL-based atlas methods. Infers deformation fields in seconds. | [Paper (NeurIPS)](https://papers.nips.cc/paper/2019/hash/5b2239634e9089203a303681648a5864-Abstract.html) \| [GitHub](https://github.com/voxelmorph/voxelmorph) |
| **Atlas-GAN** | 2021 | Dey et al. | **Conditional GAN.** Uses adversarial loss to sharpen templates and allows conditioning on attributes (e.g., age). | [Paper (ICCV)](https://openaccess.thecvf.com/content/ICCV2021/html/Dey_Generative_Adversarial_Registration_for_Improved_Conditional_Deformable_Templates_ICCV_2021_paper.html) \| [GitHub](https://github.com/neel-dey/Atlas-GAN) |
| **Diff-Def** | 2024 | Starck et al. | **Diffusion Models.** Generates deformation fields using latent diffusion for highly realistic conditional atlases. | [Paper (ArXiv)](https://arxiv.org/abs/2403.16776) |
| **MultiMorph** | 2025 | Abulnaga et al. | **Recursive Registration.** On-demand atlas construction with population centrality constraints. | [Paper (CVPR)](https://arxiv.org/abs/2506.09668) \| [Project](https://github.com/vinkle/MultiMorph) |
| **CINEMA** | 2025 | Dannecker et al. | **Implicit Neural Rep (INR).** Resolution-agnostic spatiotemporal atlas. The current SOTA for fetal/neonatal data. | [Paper (ArXiv)](https://arxiv.org/abs/2506.09668) \| [Code](https://github.com/m-dannecker/CINEMA) |


## 📚 Extended Bibliography (Categorized)
A comprehensive list of deep learning works referenced in the review, categorized by their methodological focus.

### 1. Conditional & Generative Atlases
*Methods that allow generating atlases conditioned on attributes (e.g., Age, Sex).*
* **Atlas-GAN:** *Generative adversarial registration for improved conditional deformable templates.* (Dey et al., ICCV 2021)
    * [Paper Link (CVF)](https://openaccess.thecvf.com/content/ICCV2021/html/Dey_Generative_Adversarial_Registration_for_Improved_Conditional_Deformable_Templates_ICCV_2021_paper.html)
* **CAS-Net:** *Conditional atlas generation and brain segmentation for fetal MRI.* (Li et al., MICCAI PIPPI Workshop 2021)
    * [Paper Link (Springer)](https://link.springer.com/chapter/10.1007/978-3-030-87735-4_21)
* **Deep-Diffeomorphic:** *Deep-Diffeomorphic Networks for Conditional Brain Templates.* (Whitbread et al., Human Brain Mapping 2025)
    * [Paper Link (Wiley)](https://onlinelibrary.wiley.com/doi/full/10.1002/hbm.26186)
* **Diff-Def:** *Diffusion-Generated Deformation Fields for Conditional Atlases.* (Starck et al., IEEE TMI 2025)
    * [Paper Link (IEEE)](https://ieeexplore.ieee.org/document/10360341)

### 2. Surface-Based Learning (Spherical)
*Deep learning approaches applied specifically to cortical surface registration and atlas building.*
* **S3Reg:** *Superfast Spherical Surface Registration Based on Deep Learning.* (Zhao et al., IEEE TMI 2021)
    * [Paper Link (IEEE)](https://ieeexplore.ieee.org/document/9369062)
* **Unsupervised Spherical Networks:** *Learning 4D infant cortical surface atlas with unsupervised spherical networks.* (Zhao et al., MICCAI 2021)
    * [Paper Link (Springer)](https://link.springer.com/chapter/10.1007/978-3-030-87234-2_14)

### 3. Registration Frameworks
*General-purpose registration networks adapted for atlas tasks.*
* **Unsupervised Multimodal:** *Unsupervised deep learning registration model for multimodal brain images.* (Abbasi et al., JACMP 2023)
    * [Paper Link (Wiley)](https://aapm.onlinelibrary.wiley.com/doi/full/10.1002/acm2.14156)
* **Anatomically Constrained:** *Learning spatiotemporal probabilistic atlas with anatomically constrained registration network.* (Pei et al., MICCAI 2021)
    * [Paper Link (Springer)](https://link.springer.com/chapter/10.1007/978-3-030-87234-2_57)
* **Rethinking Fetal Atlas:** *A Deep Learning Perspective.* (Zhang et al., MICCAI PIPPI Workshop 2024)
    * [Paper Link (Springer)](https://link.springer.com/chapter/10.1007/978-3-031-45544-5_12)
