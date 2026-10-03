# Skin Lesion Segmentation with a Hybrid U-Net (ISIC 2016)

Segmentation of skin lesions in dermoscopic images, combining a **classical image processing pipeline** with a **deep learning U-Net**. The classical pipeline produces a coarse lesion mask, which is fed to the U-Net as a fourth input channel alongside the RGB image.

## Overview

| | |
|---|---|
| **Data** | ISIC 2016 Part 1 lesion segmentation challenge, 900 image–mask pairs (70/15/15 train/validation/test split) |
| **Pre-processing** | Gray-World colour constancy, hair removal (black-hat filtering + inpainting), CLAHE on the L channel (Lab), Gaussian smoothing, normalisation |
| **Classical segmentation** | Thresholding + morphological operations to generate a coarse lesion mask |
| **Clinical shape features** | Asymmetry and radial features extracted from the coarse mask |
| **Deep learning** | Hybrid U-Net with 4-channel input (RGB + coarse mask), Dice-based training |
| **Tools** | Python, OpenCV, scikit-image, NumPy, TensorFlow / Keras |

## Results

| Method | Dice |
|---|---|
| Classical coarse mask (threshold + morphology) | 0.71 |
| **Hybrid U-Net (best validation)** | **0.88** |

The hybrid U-Net reached a best validation accuracy of 95.3%. Segmentation quality was also measured with IoU, pixel accuracy and Hausdorff distance (HD95).

## How to run

Download the ISIC 2016 Part 1 training images and ground-truth masks, place the zip files in Google Drive, and run the notebook in Google Colab. The notebook locates and extracts the archives automatically. A GPU runtime is recommended.

```
pip install -r requirements.txt
```
