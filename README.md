# MSPS Dataset

**MSPS** is an expert-annotated dataset for pixel-level defect segmentation in monocrystalline silicon photovoltaic (PV) cells. The images were acquired using electroluminescence (EL) imaging under practical manufacturing conditions.

This repository accompanies the manuscript:

> **DACN: Dynamic Adjustment Contrast Network for Photovoltaic Cell Defect Segmentation**  

## Dataset overview

- **Task:** binary semantic segmentation of PV-cell defects
- **Images:** 1,500 EL images
- **Resolution:** 640 × 590 pixels
- **Official split:** 1,000 training images and 500 test images
- **Cell type:** monocrystalline silicon PV cells
- **Representative defects:** busbar breaks, black spots, and cracks
- **Challenging characteristics:** minute targets, low contrast, large scale variation, irregular boundaries, and severe foreground–background imbalance

## Annotation protocol

Each image was independently annotated at the pixel level by two PV-domain experts. When their annotations disagreed, a third expert reviewed the case and resolved the discrepancy. This procedure was used to improve annotation consistency and reliability.

## Dataset characteristics

| Characteristic | Value |
|---|---:|
| Mean defect footprint | 128 pixels² |
| Median defect footprint | 114 pixels² |
| Defect-size range | 1–821 pixels² |
| Mean background-to-defect pixel ratio | 2020:1 |
| Approximate defect-pixel proportion | 0.05% |
| Defects with irregular or jagged contours | 62.1% |

These properties make MSPS especially suitable for studying segmentation under extreme class imbalance and for evaluating sensitivity to very small, low-contrast defects.

## Download

The public dataset download links will be added here after the release package is uploaded.

- **Baidu Netdisk:https://pan.baidu.com/s/1KXiSdl19XimXRJOVZskjsQ 提取码: zcmk 
- **Alternative mirror:** coming soon

To preserve comparability with the accompanying paper, users should retain the official 1,000/500 training–test split when reporting benchmark results.

## Intended use

MSPS is intended for academic research on topics including:

- photovoltaic-cell defect segmentation;
- small-object and low-contrast segmentation;
- class-imbalanced learning;
- boundary-aware segmentation;
- robust industrial visual inspection.

The dataset should not be interpreted as directly providing electrical power-loss prediction, lifetime estimation, or field-deployment validation.

## Citation

If you use MSPS in your research, please cite the accompanying paper. Complete bibliographic information and a ready-to-copy BibTeX entry will be added after publication.

> Chuhan Wang and Shenshen Zhao, “DACN: Dynamic Adjustment Contrast Network for Photovoltaic Cell Defect Segmentation,” manuscript submitted to *Applied Energy*.

## License

The dataset license will be announced together with the downloadable release package. Until then, no reuse license is granted by this repository.

## Updates

- Repository created under the official maintainer account.
- Dataset download links and release-package details are pending.
