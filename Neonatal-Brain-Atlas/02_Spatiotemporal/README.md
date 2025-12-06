# Phase 3: Spatiotemporal (4D) Atlas Construction

> Corresponding to **Section 2.3** of the review paper.

## 📖 Overview
This phase addresses the "temporal discontinuity" (or jumps) observed in discrete stage-wise atlases. The goal is to build **continuous, time-aware models** that capture smooth developmental trajectories.

* **Discrete Stage-wise:** Grouping subjects by week (e.g., 24w, 25w). Prone to artifacts between weeks (Wu et al., 2021; Feng et al., 2019).
* **Continuous Time-aware:** Using mathematical regression (e.g., Kernel Regression) to jointly estimate template shape and intensity over continuous time (Gholipour et al., 2017; Serag et al., 2012).

## 🛠️ Key Methods & Algorithms

Since many methods in this era predate the standard use of GitHub, we link to their **Laboratory Project Pages** or host **Toolboxes**.

| Method / Algorithm | Year | Author | Core Technique | Links |
| :--- | :--- | :--- | :--- | :--- |
| **Discrete Stage-wise** | 2016 | Blesa et al. | Independent averaging per age bin. | [Paper](https://www.frontiersin.org/articles/10.3389/fnins.2016.00220/full) \| [Toolbox](https://www.nitrc.org/projects/unc_brain_atlas/) |
| **Kernel Regression (4D)** | 2017 | Gholipour et al. | **Nadaraya-Watson Kernel Regression.** Weights contributions based on temporal distance. | [Paper](https://www.nature.com/articles/srep20734) \| [Lab Page](http://crl.med.harvard.edu/research/fetal_brain_atlas/) |
| **Diffeomorphic Demons** | 2015 | Li et al. | Spherical Demons for surface registration across time. | [Paper](https://pubmed.ncbi.nlm.nih.gov/25863529/) \| [Toolbox](https://www.nitrc.org/projects/sphericaldemons) |
| **MSM (Surface)** | 2018 | Bozek et al. (dHCP) | Multimodal Surface Matching for cortical folding alignment. | [Paper](https://pubmed.ncbi.nlm.nih.gov/29928965/) \| [FSL Tool](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/MSM) |
## 🧮 Core Algorithm: Kernel Regression
*As source code for classic Kernel Regression is often custom MATLAB scripts, we provide the core mathematical formulation used in these atlases.*

The construction typically solves for a weighted average template $T(t)$ at time $t$:

$$T(t) = \frac{\sum_{i=1}^{N} K_h(t - t_i) \cdot \phi_i \circ I_i}{\sum_{i=1}^{N} K_h(t - t_i)}$$

* $K_h$: A Gaussian kernel function (determines the "window size" of age).
* $t_i$: Age of subject $i$.
* $\phi_i$: Deformation field aligning subject $i$ to the template.
* $I_i$: Image of subject $i$.

## 📊 Comparison: Discrete vs. Continuous

| Feature | Discrete (Stage-wise) | Continuous (Kernel Regression) |
| :--- | :--- | :--- |
| **Time Representation** | Binned (e.g., Week 24, 25) | Continuous Variable $t$ |
| **Smoothness** | "Jumps" between bins (See Fig 2 in paper) | Smooth biological trajectory |
| **Data Efficiency** | Low (needs data per bin) | High (shares info across ages) |
| **Implementation** | Simple Averaging | Complex Regression Loop |

## 💡 Practical Notes
* **For Surface Atlases:** The **dHCP** project uses the MSM (Multimodal Surface Matching) framework, which is available as part of the **FSL** software library.
* **For Volumetric 4D Atlases:** Most current research has moved to Deep Learning (Stage 5) to approximate the Kernel Regression process more efficiently (e.g., using Conditional GANs or INRs).
