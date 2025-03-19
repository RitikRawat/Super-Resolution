# 🖼️ Image Super-Resolution using SRGAN and Self-Supervised Learning

A project exploring advanced techniques for enhancing image resolution using **Super-Resolution Generative Adversarial Networks (SRGAN)** and **Self-Supervised Learning (SSL)** with CNNs.

---

## 📖 Introduction

Image Super-Resolution (ISR) is the task of reconstructing a high-resolution (HR) image from a low-resolution (LR) one. It has wide applications in medical imaging, satellite imaging, security, and media restoration.

This project implements and compares two advanced approaches:
- **SRGAN**: A GAN-based architecture trained to generate photorealistic HR images from LR inputs.
- **Self-Supervised Learning + CNNs**: Uses unlabeled data and pretext tasks to train a model to recover HR images by learning meaningful representations without direct supervision.

---

## 🎯 Objectives

- Develop a model that enhances image resolution by **up to 4×**.
- Preserve fine details while **minimizing visual artifacts**.
- Compare **perceptual quality** and **storage efficiency** of traditional and learning-based methods.
- Explore the effect of training strategies like **adversarial training** and **contrastive learning**.

---

## 🧠 Methods

### 🔹 1. Super-Resolution GAN (SRGAN)

- **Generator**:
  - Residual blocks with skip connections.
  - Upsampling via pixel-shuffle layers.
- **Discriminator**:
  - CNN-based binary classifier to distinguish real HR vs. fake HR images.
- **Loss Functions**:
  - **Content Loss**: Perceptual loss using VGG features.
  - **Adversarial Loss**: Binary cross-entropy from the discriminator.
- **Training Strategy**:
  - Alternate training of generator and discriminator (typical GAN setup).
  - Perceptual tuning improves fine textures and details.

### 🔹 2. Self-Supervised Learning for Super-Resolution (SSLSR)

- **Architecture**:
  - A deep CNN trained using a **pretext task**: recover a randomly degraded image.
  - Uses transformations like blur, downsampling, and noise addition.
- **Learning Objective**:
  - Train model to reconstruct original high-res patches from augmented low-res ones.
- **Advantages**:
  - Doesn’t require HR-LR image pairs.
  - Utilizes large-scale unlabeled datasets.

---

## 📊 Results

| Model     | PSNR (↑) | SSIM (↑) | Visual Quality | Storage Savings |
|-----------|----------|----------|----------------|------------------|
| Bicubic   | 23.1     | 0.60     | Blurry         | -                |
| SRGAN     | 28.5     | 0.82     | Sharp & clear  | 75% (vs. raw HR) |
| SSLSR     | 27.8     | 0.79     | Smooth & clean | 70% (vs. raw HR) |

- SRGAN achieved **sharp textures** and better detail, though at higher compute cost.
- SSL-based model was more efficient, generalized well without needing paired data.
- Both models provided **significant storage savings** by generating HR images on-the-fly.

---

## 🧪 Evaluation Metrics

- **PSNR (Peak Signal-to-Noise Ratio)**: Measures pixel-wise accuracy.
- **SSIM (Structural Similarity Index)**: Measures structural similarity and perceptual quality.
- **Visual Inspection**: Comparison with original HR images.

---

## 🗃️ Dataset

- **DIV2K**: High-quality images used for training and validation.
- Downsampled images used as LR input using bicubic degradation.

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/your-username/image-super-resolution.git
cd image-super-resolution
