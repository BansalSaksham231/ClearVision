# 📌 Clear Vision: Image Super-Resolution using GANs

**🔗 Application Link**: [Clear-Vision](https://clear-vision-pro.streamlit.app/)  
**⚠️ Recommended Input**: Upload images ≤128×128 (ideal: 64×64). Models upscale inputs to 128×128.  
**🧪 Sample Corrupted Images (64×64)**: [Google Drive Link](https://drive.google.com/drive/folders/1bzkac88TPpf9ozlXfy3wUcl_Vyu6VxHj?usp=sharing)

---

## 📄 Project Overview

This project explores deep learning techniques for **image super-resolution** using GAN-based models:

| Model    | Description |
|----------|-------------|
| **SRGAN**  | Classic Super-Resolution GAN using pixel, perceptual, and adversarial losses. |
| **SRWGAN** | Extension of SRGAN integrating **Wasserstein loss** for more stable and high-quality results. |

**Goal**: Reconstruct high-resolution (HR) images from low-resolution (LR) inputs, enabling practical applications in:
- Surveillance
- Autonomous vehicles
- Image enhancement tools
- Medical imaging

---

## 🧪 Corruption Techniques

To simulate real-world degradation, LR images were subjected to:

- **Motion Blur**: Simulates camera motion via convolution with motion kernels.
- **JPEG Compression**: Introduces artifacts typical of lossy storage/transmission.
- **Polygon Masking**: Random occlusions mimicking sensor damage or object obstruction.

**Corruption Strategy**:
- ✅ 30% images: All 3 corruptions
- ✅ 30% images: Any 2 corruptions
- ✅ 30% images: Any 1 corruption
- ✅ 10% images: Clean (for baseline testing)

---

## 🚀 Model Output Resolution

Both models upscale input images by a factor of 2×:

- **Input LR**: 64×64  
- **Output SR**: 128×128

---

## 🧠 Training Details

- **Dataset**: 10,000 RGB images (128×128) from [CelebA-HQ Resized](https://www.kaggle.com/datasets/badasstechie/celebahq-resized-256x256)  
- **Split**: 80% training, 20% validation  
- **Hardware**: Kaggle P100 GPU  
- **Losses Used**:
  - **Content Loss**: MSE
  - **Perceptual Loss**: VGG feature loss
  - **Adversarial Loss**:
    - Binary Crossentropy (SRGAN)
    - Wasserstein (SRWGAN)

---

## 📊 Evaluation Metrics

| Model   | PSNR ↑ | SSIM ↑ | FID ↓ | LPIPS ↓ |
|---------|--------|--------|-------|---------|
| SRGAN   | 28.01  | 0.900  | 50.34 | 0.0371  |
| SRWGAN  | 28.28  | 0.903  | 42.09 | 0.0364  |

> ↑ Higher is better &nbsp;&nbsp;&nbsp;&nbsp; ↓ Lower is better

---


<h2>💻 Tech Stack / Frameworks</h2>

<ul>
  <li><strong>Machine Learning & Image Enhancement:</strong><br>
      <code>TensorFlow</code> – Used to train and run the models that enhance image quality.
  </li>
  <br>
  <li><strong>Web Interface:</strong><br>
      <code>HTML</code> <br><code>CSS</code>
      <code>Streamlit</code> – A fast and interactive web app framework used to deploy the Clear Vision interface for uploading images and displaying results.
  </li>
  <br>
  <li><strong>Data Handling:</strong><br>
      <code>NumPy</code>– For efficient data preprocessing, image array manipulation, and metric computation.
  </li>
  <br>
  <li><strong>Visualization:</strong><br>
      <code>Matplotlib</code>– Used to display image quality visually.
  </li>
  <br>
  <li><strong>Image Processing:</strong><br>
       <code>OpenCV</code> – For reading, resizing, and applying filters to images before and after super-resolution.
  </li>
</ul>



## 📚 References

- [SRGAN Paper](https://arxiv.org/abs/1609.04802)
- [WGAN Paper](https://arxiv.org/abs/1701.07875)
