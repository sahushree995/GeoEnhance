# GeoEnhance — See Beyond Resolution
GeoEnhance | See Beyond Resolution — AI-powered 4× super-resolution of Sentinel-2 satellite imagery using EDSR and SwinIR, with RGB+NIR processing and PSNR, SSIM, and SAM evaluation.
### Super-Resolution Mapping from Medium-Resolution Satellite Imagery

GeoEnhance is a deep learning-based satellite image super-resolution project that enhances **Sentinel-2 RGB+NIR imagery by 4×** using EDSR and SwinIR architectures.

## Technologies Used
Python, PyTorch, TensorFlow/Keras, OpenCV, Rasterio, NumPy, Matplotlib, Kaggle GPU.

## Dataset
**SEN2NAIPv2**
- **Synthetic:** Initial SwinIR pretraining.
- **Crosssensor:** Fine-tuning and evaluation using Sentinel-2 and NAIP image pairs.
- **Split:** 6,372 training, 800 validation, and 828 testing samples.
- **Resolution:** 130×130 → 520×520 pixels (4×).

## Models
- **EDSR:** Residual CNN, fine-tuned for 20 epochs.
- **SwinIR:** Shifted-window Transformer, synthetic pretraining followed by 10 epochs of Crosssensor fine-tuning.
- **Bicubic:** Conventional interpolation baseline.

## Results

| Model | PSNR (dB) ↑ | SSIM ↑ | SAM (°) ↓ |
|---|---:|---:|---:|
| Bicubic | 35.6678 | 0.8624 | 2.3939 |
| EDSR | 35.9009 | **0.8663** | 2.3090 |
| SwinIR (Pretrained) | 35.3985 | 0.8639 | 2.5190 |
| SwinIR (Fine-tuned) | **35.9150** | 0.8652 | **2.3028** |

*Evaluated on 828 Crosssensor test samples. EDSR results are preliminary because possible overlap with its earlier training data cannot be excluded.*

## Image Post-Processing
To improve visual clarity, two enhancement pipelines were tested:

1. **Luminance CLAHE + Unsharp Masking:** Improved local contrast and emphasized existing edges.
2. **Bilateral Denoising + CLAHE + Controlled Sharpening:** Reduced noise while enhancing visible boundaries.

Post-processing was applied only to RGB display images. Original model predictions were retained for PSNR, SSIM, and SAM evaluation. These techniques cannot recover spatial details absent from the input.

## Project Features
- 4× multispectral satellite image super-resolution.
- EDSR vs. SwinIR visual and quantitative comparison.
- RGB and zoomed image visualization.
- Localhost image-upload and before/after slider interface *(planned)*.

## Future Scope
Improved crosssensor alignment, geographically diverse testing, and optimized local inference.

