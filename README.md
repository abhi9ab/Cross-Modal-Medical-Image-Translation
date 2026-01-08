# Cross-Modality Medical Image Translation (MRI ↔ CT)

This repository contains an unsupervised deep learning framework for bidirectional medical image translation between MRI and CT modalities using **CycleGAN**. This project is specifically designed to generate high-fidelity **Synthetic CT (sCT)** from MRI scans to enable MRI-only radiotherapy planning, effectively reducing patient radiation exposure and clinical costs.



## 🚀 Key Features
* **Unpaired Training:** Operates without the need for perfectly aligned MRI-CT image pairs, utilizing cycle-consistency constraints.
* **ResUNet Architecture:** Features a ResNet-9 generator that preserves deep anatomical features and mitigates gradient vanishing.
* **SSIM-Enhanced Training:** Beyond standard $L_1$ and Adversarial losses, an explicit **Structural Similarity (SSIM) Loss** is integrated to ensure anatomical integrity.
* **Medical Domain Optimized:** Built using the **MONAI** (Medical Open Network for AI) framework for specialized medical data augmentation and intensity transforms.

## 🏗️ Technical Architecture
* **Generators:** ResNet-based models with 9 residual blocks and Instance Normalization.
* **Discriminators:** 70x70 PatchGAN with **Spectral Normalization** to ensure training stability and realistic local textures.
* **Training Strategy:** 60 epochs with a starting learning rate of 0.0002, utilizing a **Cosine Annealing** scheduler and the **Adam** optimizer.

## 📊 Results & Evaluation
The model demonstrates high fidelity in structural preservation. While the CT-to-MRI cycle shows higher stability, the MRI-to-CT translation successfully recovers skeletal structures necessary for dose calculation.

| Metric | MRI Cycle ($MRI \rightarrow CT \rightarrow MRI$) | CT Cycle ($CT \rightarrow MRI \rightarrow CT$) |
| :--- | :--- | :--- |
| **Mean SSIM** | 0.7660 | **0.9173** |
| **Peak SSIM** | 0.8511 | **0.9262** |
| **Mean PSNR** | ~24.5 dB | ~29.8 dB |



## 🛠️ Installation
Ensure you have the following dependencies installed:
```bash
pip install torch torchvision monai matplotlib numpy
```

📚 References

    Yu, L., et al. (2025). "AI-enhanced PET/CT image synthesis using CycleGAN for improved ovarian cancer imaging," Polish Journal of Radiology, vol. 90.

    Bahloul, M. A., et al. (2024). "Advancements in synthetic CT generation from MRI: A review of techniques," Frontiers in Radiology.

    SciTePress (2024). "CT to MRI Image Translation Using CycleGAN: A Deep Learning Approach for Cross-Modality Medical Imaging."

    Zhu, J.-Y., et al. (2017). "Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks," ICCV.



Development Team: [Abhinab Das](https://github.com/abhi9ab), [Abhishek S U](https://github.com/Abhiajay1802), [Abhinav Pandey](https://github.com/Abhinav2656), Priyanshu Thakur
