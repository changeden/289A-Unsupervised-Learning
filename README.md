# 289A-Unsupervised-Learning




# Analyzing Memorization in Vision Diffusion Models

This repository contains the code and experimental results for our project: **"Analyzing Memorization in Vision: Diffusion Model"**, conducted at UC Davis as part of the EEC289A course. The study investigates how diffusion models balance generalization and memorization, especially in the context of semiconductor layout pattern generation.

## 🌟 Overview

Diffusion models have shown remarkable performance in generative tasks, but recent concerns point toward their potential to memorize training data—posing risks to data privacy and originality. This project explores:

- How diffusion models (DDPMs) may memorize or generalize on layout datasets.
- Metrics for quantifying memorization: **SSIM**, **Entropy**, and **Mutual Information (MI)**.
- Behavior of models trained on **IC layout data**, with inserted rare patterns for robustness testing.

## 📂 Dataset
https://drive.google.com/drive/home

We use grayscale IC layout datasets (`MetalSet` and `ContactSet`) containing:
- Real-world printed and target photolithography patterns
- Images resized to **128×128**
- Normalized pixel intensities `[0,1]`

Each image reflects contact/via/metal shapes typical in semiconductor fabrication—ideal for testing memorization in structured data.

## 🧠 Model Pipeline

We adopt a **Latent Diffusion Model** pipeline:
- **AutoencoderKL**: Encodes and decodes image features into latent space
- **UNet2DModel**: Trained with **DDPM** (Denoising Diffusion Probabilistic Model) schedules
- Training performed on **NVIDIA GPU** with batch size 32 for 5–10 epochs
- Loss terms: **L1 reconstruction loss** + **Entropy regularization**

## 📏 Metrics

To detect memorization risk, we use:

| Metric | Description |
|--------|-------------|
| **SSIM** | Measures visual similarity (structure, luminance, contrast) |
| **Entropy** | Measures image complexity / diversity |
| **Mutual Information (MI)** | Captures statistical dependency between training and generated images |

These metrics enable quadrant-based interpretation of memorization risk.

## 📊 Results

Our analysis reveals:
- High SSIM + Low Entropy indicates high memorization risk
- MI complements SSIM to reveal hidden structural similarities
- Rare patterns are sometimes memorized more aggressively than common ones

We provide scatter plots and heatmaps to visualize entropy-SSIM and SSIM-MI relationships.

## ✅ Conclusion

This work presents a **scalable framework** for post-hoc memorization analysis in generative models. It’s especially relevant to:
- IC layout generation tasks
- Generative AI safety and privacy audits
- Research on generalization behavior in diffusion-based architectures

## 📄 Citation

If you use or reference this work, please cite:

