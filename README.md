# Vietnamese License Plate Recognition Benchmark

## YOLOv5 -- YOLOv8 -- YOLOv11 with Multi-Architecture OCR

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Framework](https://img.shields.io/badge/Framework-PyTorch-red)
![License](https://img.shields.io/badge/License-MIT-green)

------------------------------------------------------------------------

## 1. Overview

This repository presents a systematic benchmark study for Vietnamese
License Plate Recognition (LPR), evaluating three generations of YOLO
detectors alongside multiple OCR architectures under identical training
and evaluation protocols.

The benchmark is designed to ensure fairness, reproducibility, and
real-world applicability.

------------------------------------------------------------------------

## 2. Experimental Results

### 2.1 Detection Benchmark

All detection models were trained under identical conditions (640×640
resolution, 20 epochs, AdamW optimizer). Performance is reported on the
validation set.

  Model         mAP@0.5     mAP@0.5:0.95   Precision   Recall
  ------------- ----------- -------------- ----------- -----------
  YOLOv5        0.985       0.700          0.988       0.975
  YOLOv8        0.990       0.730          0.992       0.980
  **YOLOv11**   **0.994**   **0.752**      **0.995**   **0.985**

**Observations:**

-   YOLOv11 achieves the highest localization accuracy across all
    metrics.
-   The improvement from YOLOv5 → YOLOv11 shows consistent gains in both
    mAP@0.5 and mAP@0.5:0.95.
-   Precision--Recall balance indicates strong generalization without
    overfitting.
-   YOLOv8 provides a strong trade-off between architectural simplicity
    and performance.

------------------------------------------------------------------------

### 2.2 OCR Benchmark (Plate-Level Accuracy)

OCR methods were evaluated using full-plate exact match accuracy.

  OCR Method                       YOLOv5   YOLOv8   YOLOv11
  -------------------------------- -------- -------- -----------
  Contours + CNN                   58.2%    59.2%    60.2%
  YOLO + CNN                       75.2%    76.4%    77.9%
  **CNN + CTC (Fast-Plate OCR)**   97.3%    98.1%    **98.9%**

**Observations:**

-   Character-wise classification approaches are limited by segmentation
    errors.
-   YOLO-assisted character segmentation improves performance by
    \~17--18% over contour-based methods.
-   The sequence-based CNN + CTC architecture significantly outperforms
    classification pipelines.
-   The best end-to-end configuration (YOLOv11 + Fast-Plate OCR)
    achieves **98.9% plate accuracy**, approaching near-perfect
    recognition under real-world conditions.

------------------------------------------------------------------------

### 2.3 Overall Best Configuration

**Detector:** YOLOv11\
**Recognizer:** Fast-Plate OCR (CNN + BiLSTM + CTC)

Final Plate Accuracy: **98.9%**\
Detection mAP@0.5: **0.994**

This combination minimizes error propagation between detection and
recognition stages while maintaining real-time feasibility.

------------------------------------------------------------------------

## 3. Dataset

-   8,259 annotated detection images
-   3,763 OCR samples
-   32-character Vietnamese alphanumeric set
-   Collected from real-world RTSP traffic camera streams

------------------------------------------------------------------------

## 4. Training Configuration

### Detection

-   Resolution: 640×640
-   Epochs: 20
-   Optimizer: AdamW (lr=0.002)
-   Batch size: 16

### OCR

-   Epochs: 100
-   Optimizer: AdamW (lr=0.0005)
-   Loss: CTC (for sequence modeling)

------------------------------------------------------------------------

## 5. Paper

The full research paper is available in:

paper/License_Plate_Recognize.pdf

------------------------------------------------------------------------

## 6. Citation

``` bibtex
@article{VietnameseLPR2026,
  title={A Comparative Benchmark Study for Vietnamese License Plate Recognition},
  author={Tran Ngoc Quang and Doan Dang Khoa and Vo Hoang Lam},
  year={2026}
}
```

------------------------------------------------------------------------

## Authors

Tran Ngoc Quang\
Doan Dang Khoa\
Vo Hoang Lam

FPT University -- Major of Artificial Intelligence

------------------------------------------------------------------------

If you find this repository useful, consider giving it a star.
