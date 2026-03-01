
# Vietnamese License Plate Recognition Benchmark
## YOLOv5 – YOLOv8 – YOLOv11 with Multi-Architecture OCR

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Framework](https://img.shields.io/badge/Framework-PyTorch-red)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 2. Experimental Results

## 2.1 Detection Benchmark

All detection models were trained under identical conditions:

- Resolution: 640×640  
- Epochs: 20  
- Optimizer: AdamW  
- Evaluation: Validation set  

### Detection Performance

| Model   | mAP@0.5 | mAP@0.5:0.95 | Precision | Recall |
|---------|---------|--------------|-----------|--------|
| YOLOv5  | 0.985   | 0.700        | 0.988     | 0.975  |
| YOLOv8  | 0.990   | 0.730        | 0.992     | 0.980  |
| **YOLOv11** | **0.994** | **0.752** | **0.995** | **0.985** |

### Key Observations

- YOLOv11 achieves the highest localization accuracy across all metrics.
- Consistent improvement from YOLOv5 → YOLOv11 in both mAP metrics.
- Precision–Recall balance indicates strong generalization.
- YOLOv8 offers an efficient trade-off between complexity and performance.

---

## 2.2 OCR Benchmark (Plate-Level Accuracy)

OCR methods were evaluated using full-plate exact match accuracy.

### OCR Performance

| OCR Method | YOLOv5 | YOLOv8 | YOLOv11 |
|------------|--------|--------|---------|
| Contours + CNN | 58.2% | 59.2% | 60.2% |
| YOLO + CNN | 75.2% | 76.4% | 77.9% |
| **CNN + CTC (Fast-Plate OCR)** | 97.3% | 98.1% | **98.9%** |

### Key Observations

- Segmentation-based pipelines are limited by character localization errors.
- YOLO-assisted segmentation improves recognition by ~18% over contour methods.
- Sequence-based CNN + CTC significantly outperforms classification approaches.
- Best end-to-end system: **YOLOv11 + Fast-Plate OCR (98.9% plate accuracy)**.

---

If you find this repository useful, consider giving it a star.
