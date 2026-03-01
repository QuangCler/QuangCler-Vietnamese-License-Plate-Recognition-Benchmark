
<div align="center">

# 🇻🇳 Vietnamese License Plate Recognition Benchmark  
### YOLOv5 · YOLOv8 · YOLOv11 + Multi-Architecture OCR

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Framework](https://img.shields.io/badge/Framework-PyTorch-red)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Research-orange)

</div>

---

## 📌 Overview

This repository presents a **systematic benchmark study** for Vietnamese License Plate Recognition (LPR), comparing three generations of YOLO detectors and multiple OCR architectures under identical experimental conditions.

---

# 📊 Experimental Results

## 🚘 Detection Benchmark

**Training Configuration**
- Resolution: 640×640
- Epochs: 20
- Optimizer: AdamW
- Batch size: 16
- Evaluation: Validation set

### Detection Performance

| Model     | mAP@0.5 | mAP@0.5:0.95 | Precision | Recall |
|-----------|---------|--------------|-----------|--------|
| YOLOv5    | 0.985   | 0.700        | 0.988     | 0.975 |
| YOLOv8    | 0.990   | 0.730        | 0.992     | 0.980 |
| **YOLOv11** | **0.994** | **0.752** | **0.995** | **0.985** |

**Analysis**
- YOLOv11 achieves the highest localization performance.
- Progressive gains observed from YOLOv5 → YOLOv11.
- Strong Precision–Recall balance confirms stable convergence.

---

## 🔤 OCR Benchmark (Plate-Level Accuracy)

### OCR Performance

| OCR Method | YOLOv5 | YOLOv8 | YOLOv11 |
|------------|--------|--------|---------|
| Contours + CNN | 58.2% | 59.2% | 60.2% |
| YOLO + CNN | 75.2% | 76.4% | 77.9% |
| **CNN + CTC (Fast-Plate OCR)** | 97.3% | 98.1% | **98.9%** |

**Analysis**
- Segmentation-based pipelines are limited by character localization errors.
- YOLO-assisted segmentation improves accuracy by ~18%.
- CNN + CTC significantly outperforms classification pipelines.
- Best configuration: **YOLOv11 + Fast-Plate OCR (98.9%)**.

---

# 🧠 Best End-to-End Configuration

Detector: YOLOv11  
Recognizer: Fast-Plate OCR (CNN + BiLSTM + CTC)

- mAP@0.5: 0.994
- Plate Accuracy: 98.9%
- Real-time inference capable

---

# 📂 Dataset

- 8,259 detection images
- 3,763 OCR samples
- 32 Vietnamese alphanumeric characters
- Real-world RTSP traffic camera data

---

# 📜 Citation

```bibtex
@article{VietnameseLPR2026,
  title={A Comparative Benchmark Study for Vietnamese License Plate Recognition},
  author={Tran Ngoc Quang and Doan Dang Khoa and Vo Hoang Lam},
  year={2026}
}
```

---

<div align="center">

⭐ If you find this repository useful, consider giving it a star.

</div>
