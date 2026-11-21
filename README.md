# Merging Multi-Domain Datasets for Generalized Forensic Evidence Detection

This repository contains the code, configurations, and paper for evaluating baseline and architecturally enhanced YOLOv8-m and YOLO11-m object detection models on a unified 48-class forensic evidence dataset.

## Key Findings

- **YOLO11-m baseline** achieves the best overall performance (mAP@50 = 0.973, mAP@50-95 = 0.882) with the fewest parameters (20.1M) and lowest computation (68.0 GFLOPs)
- Architectural enhancements **degraded** performance for both model families
- Cross-domain analysis reveals smart-device classes achieve near-perfect detection (mAP@50 > 0.99), while crime-scene classes show greater variability
- Pareto analysis confirms both baselines dominate their enhanced counterparts on the accuracy-efficiency frontier

## Repository Structure

```
.
├── paper/
│   ├── main_v3.tex          # LaTeX source
│   └── Refs.bib             # Bibliography (25 references)
├── configs/
│   ├── yolov8m_baseline.yaml
│   ├── yolov8m_enhanced.yaml
│   ├── yolo11m_baseline.yaml
│   ├── yolo11m_enhanced.yaml
│   └── SCALE_REFERENCE.md   # Official scaling multipliers
├── notebooks/
│   ├── 01_full_training_pipeline.ipynb   # Training (4 models x 3 seeds)
│   ├── 02_analysis_and_plots.ipynb       # Figures and analysis
│   └── 03_test_eval_and_samples.ipynb    # Test-set evaluation
├── figures/                  # Final paper figures (PDF + PNG)
└── results/                  # Result CSVs
```

## Dataset

The unified dataset merges two sources into a 48-class schema:
- **Crime Scene (DS1):** 38 classes (IDs 0-8 original + IDs 9-37 reserved) covering guns, knives, blood, documents, personal objects, and suspicious persons
- **Smart Devices (DS2):** 10 classes (IDs 38-47) covering cameras, thermostats, smart speakers, and smart LED bulbs

Total: **11,795 images** split 70/20/10 (8,256 train / 2,359 val / 1,180 test)

## Training Configuration

- **Epochs:** 150
- **Batch size:** 8
- **Image size:** 640 x 640
- **Optimizer:** SGD with cosine LR schedule (lr0=0.01, lrf=0.01)
- **Seeds:** 42, 123, 7 (all results reported as mean +/- std)
- **Hardware:** Google Colab Pro, NVIDIA L4 GPU

## How to Reproduce

1. Upload the dataset to Google Drive at `/content/drive/MyDrive/ForensicsDataset/merged_dataset/`
2. Open `notebooks/01_full_training_pipeline.ipynb` in Google Colab
3. Run all cells (skip-if-done logic prevents redundant training)
4. Run `notebooks/03_test_eval_and_samples.ipynb` for test-set evaluation
5. Run `notebooks/02_analysis_and_plots.ipynb` to regenerate figures

## Authors

Chiamaka Femi-Adeyinka, Tosin Akinsowon, Jeffrey Berg, Juli Dutta, Van Vung Pham

Department of Computer Science, Sam Houston State University

## Citation

If you use this work, please cite:

```bibtex
@article{femiadeyinka2026forensic,
  title={Merging Multi-Domain Datasets for Generalized Forensic Evidence Detection},
  author={Femi-Adeyinka, Chiamaka and Akinsowon, Tosin and Berg, Jeffrey and Dutta, Juli and Pham, Van Vung},
  year={2026}
}
```
