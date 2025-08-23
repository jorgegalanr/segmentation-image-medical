# segmentation-image-medical

# 🩺 Medical Image Segmentation (Otsu · Canny · GMM)

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-informational)
![scikit-image](https://img.shields.io/badge/scikit--image-0.23-green)
![Status](https://img.shields.io/badge/status-ready-brightgreen)

Unsupervised segmentation pipeline for medical-like grayscale images using:
**Gaussian denoising → Otsu thresholding → Canny edges → Gaussian Mixture Models (GMM) → Connected Components**.  
The goal is to provide a clean, reproducible baseline you can extend with morphology or DL models.

---

🎯 Objectives

Provide a baseline for classical, unsupervised segmentation.

Make results reproducible and easy to compare.

Keep the code simple & modular (src/segmentation.py + CLI in src/run_all.py).

---

🧠 Methods

Load & Denoise: grayscale + Gaussian blur (ksize=3 by default).

Otsu Thresholding: global threshold for foreground/background.

Canny Edges: structural edges (useful for visualization or post-processing).

GMM (k=2): pixel-wise mixture model; foreground = component with higher mean.

Connected Components: labels regions; saved as a colored map.

You can add morphology (opening/closing), change GMM components, or combine masks (Otsu ∧ GMM) in segmentation.py.

## 🚀 Quick start
```bash
git clone https://github.com/jorgegalanr/segmentation-image-medical.git
cd segmentation-image-medical
pip install -r requirements.txt

# put a few PNG/JPG/TIF images here:
#   data/sample/

python src/run_all.py --input data/sample --out reports/figures
