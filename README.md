# MSPS Dataset

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21549573.svg)](https://doi.org/10.5281/zenodo.21549573)

**MSPS (Monocrystalline Silicon Photovoltaic Cell Defect Segmentation)** is an expert-annotated dataset for pixel-level defect segmentation in monocrystalline silicon photovoltaic cells. It contains production-line electroluminescence (EL) images with minute, low-contrast, multi-scale, and irregular defects.

This repository accompanies the manuscript:

> **DACN: Prediction-Conditioned Intermediate Representation Adjustment for Photovoltaic Cell Defect Segmentation**  
> Shenshen Zhao, Yumeng Hao, Chuhan Wang, and Qidong Li

## Dataset overview

| Item | Description |
|---|---|
| Task | Binary semantic segmentation of PV-cell defects |
| Number of images | 1,500 EL images |
| Image resolution | 640 × 590 pixels |
| Official split | 1,000 training images and 500 test images |
| Cell type | Monocrystalline silicon PV cells |
| Representative defects | Busbar breaks, black spots, and cracks |
| Main challenges | Minute targets, low contrast, large scale variation, irregular boundaries, and severe foreground–background imbalance |

## Acquisition and construction

The data were derived from an on-site EL inspection workflow developed with a PV-cell manufacturer. An industrial EL camera captures full cell-string images, which are divided into two-cell crops at a resolution of 640 × 590 pixels. MSPS contains 1,500 representative crops selected from this production-line workflow.

The images retain the difficult characteristics encountered in manufacturing, including extremely sparse defect pixels, blurred boundaries, irregular shapes, and substantial variation in defect size.

## Annotation protocol

Each image was independently annotated at the pixel level by two PV-domain experts. Their annotations were compared to identify disagreements. Cases with discrepancies were reviewed by a third expert to improve annotation consistency and accuracy.

## Quantitative characteristics

| Characteristic | Value |
|---|---:|
| Mean defect footprint | 128 pixels² |
| Median defect footprint | 114 pixels² |
| Defect-size range | 1–821 pixels² |
| Mean background-to-defect pixel ratio | 2020:1 |
| Approximate defect-pixel proportion | 0.05% |
| Defects with irregular or jagged contours | 62.1% |

These characteristics make MSPS suitable for studying small-target segmentation, class-imbalanced learning, boundary-aware modeling, and robust industrial visual inspection.

## Download

The archival dataset release is available from Zenodo:

- **Zenodo:** [https://doi.org/10.5281/zenodo.21549573](https://doi.org/10.5281/zenodo.21549573)

Additional download mirrors:

- **Baidu Netdisk:** [Download MSPS](https://pan.baidu.com/s/1KXiSdl19XimXRJOVZskjsQ) — access code: `zcmk`
- **Google Drive:** [Download MSPS](https://drive.google.com/file/d/1X3F0fwZMI4bk8dXYewu9eBVJDeEz6eoY/view?usp=sharing)

For direct comparison with the accompanying paper, please retain the official split of 1,000 training images and 500 test images.

## On-site inspection context

In the accompanying study, DACN was integrated into local inspection software. For each two-cell crop, the software converts the predicted mask into a defect-area ratio:

```text
R = number of predicted defect pixels / total number of pixels × 100%
```

The manufacturer-defined downstream grading rule used in the study is:

| Grade | Defect-area ratio |
|---|---:|
| Grade A | R ≤ 0.01% |
| Grade B | 0.01% < R ≤ 0.10% |
| Grade C | R > 0.10% |

These A/B/C grades are outputs of the downstream inspection workflow. **They are not additional ground-truth labels provided by MSPS**, and the thresholds should not be interpreted as universal industry standards.

## Reference results

The accompanying paper reports the following results on the fixed MSPS test set:

| Method | Backbone | mIoU | FPS |
|---|---|---:|---:|
| DACN | ResNet-50 | 89.30% | 60 |
| DACN-Lite | ShuffleNetV2 | 87.40% | 239 |

The throughput values were measured on the GPU platform reported in the manuscript (NVIDIA RTX 3090 Ti).

## Intended use and limitations

MSPS is intended for academic research on:

- photovoltaic-cell defect segmentation;
- small-object and low-contrast segmentation;
- class-imbalanced learning;
- boundary-aware segmentation;
- robustness analysis and industrial visual inspection.

The dataset and accompanying results do not demonstrate electrical power-loss prediction, lifetime estimation, or deployment on resource-constrained edge hardware. MSPS does not provide output-power, resistance, or lifetime measurements.

## Citation

If you use MSPS in your research, please cite **both the dataset record and the accompanying DACN manuscript**.

Dataset:

```bibtex
@dataset{zhao2026msps,
  author    = {Zhao, Shenshen and Hao, Yumeng and Wang, Chuhan and Li, Qidong},
  title     = {MSPS: Monocrystalline Silicon Photovoltaic Cell Defect Segmentation Dataset},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.21549573},
  url       = {https://doi.org/10.5281/zenodo.21549573}
}
```

Accompanying manuscript:

```bibtex
@unpublished{zhao2026dacn,
  author = {Zhao, Shenshen and Hao, Yumeng and Wang, Chuhan and Li, Qidong},
  title  = {DACN: Prediction-Conditioned Intermediate Representation Adjustment for Photovoltaic Cell Defect Segmentation},
  year   = {2026},
  note   = {Manuscript submitted to Applied Energy}
}
```

The manuscript entry will be updated with its final journal, volume, pages, and DOI after publication.

## License

MSPS is released under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0). You may share and adapt the dataset provided that appropriate credit is given and the Zenodo dataset record is cited.

## Repository updates

- Added the DOI-bearing Zenodo archival release.
- Added the CC BY 4.0 reuse license and ready-to-copy citation entries.
- Retained the Baidu Netdisk and Google Drive download mirrors.
- Updated the dataset description, authorship, acquisition workflow, on-site inspection context, limitations, and reference results to match the latest manuscript.
