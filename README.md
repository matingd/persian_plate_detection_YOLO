## 📖 Introduction

A YOLOv8-based pipeline for **Persian license plate and digit detection** using the Persian Plate Detection dataset. The repo includes both full-plate detection and individual digit recognition.

* **Models**: YOLOv8n for plate detection, YOLOv8s for digit detection  
* **Tasks**:  
  - **Plate Detection**: Localize entire license plates  
  - **Digit Detection**: Recognize individual characters within each plate  
---

## 🏗️ Architecture

We leverage the Ultralytics YOLOv8 framework for efficient, real-time detection. Key components:

1. **Backbone & Neck**: CSPDarknet and PANet for feature extraction and fusion  
2. **Head**: Single-stage detector predicting bounding boxes, classes, and objectness  
3. **Losses**:  
   - Box loss (CIoU)  
   - Classification loss (BCE)  
   - Distribution focal loss (DFL) for precise bounding 
---

## 🛠️ Setup & Installation

**Prerequisites**

```bash
python >=3.8,<3.11
pip install -r requirements.txt
```

**Data**

Download Persian Plate Detection dataset from 
```
import kagglehub

# Download latest version
data_path = kagglehub.dataset_download("nimapourmoradi/car-plate-detection-yolov8")

print("Path to dataset files:", data_path)
```

Download Persian Car Plates Digits Detection dataset from 
```
import kagglehub

# Download latest version
path = kagglehub.dataset_download("nimapourmoradi/persian-car-plates-digits-detection-yolov8")

print("Path to dataset files:", path)
```

---

## 📊 Predicted images

<table>
  <tr>
    <td><img src="test images/plate1_detected.jpg" width="360"/></td>
    <td><img src="test images/plate2_detected.jpg" width="360"/></td>
  </tr>
  <tr>
    <td><img src="test images/plate3_detected.jpg" width="360"/></td>
    <td><img src="test images/plate4_detected.jpg" width="360"/></td>
  </tr>
</table>

---

## 📊 Benchmarks & Metrics for plate ditection

<table>
  <tr>
    <td colspan="3" align="center"><img src="assets/yolo_map50_95_curve.png" width="600"/></td>
  </tr>
  <tr>
    <td><img src="assets/yolo_recall_curve.png" width="480"/></td>
    <td><img src="assets/yolo_validation_map50.png" width="480"/></td>
  </tr>
  <tr>
    <td><img src="assets/yolo_training_losses.png" width="480"/></td>
    <td><img src="assets/yolo_precision_curve.png" width="480"/></td>
  </tr>
</table>

---

## 📊 Benchmarks & Metrics for digits ditection

<table>
  <tr>
    <td colspan="3" align="center"><img src="assets/digits_map_curves.png" width="600"/></td>
  </tr>
  <tr>
    <td><img src="assets/digits_precision_recall.png" width="480"/></td>
    <td><img src="assets/digits_training_losses.png" width="480"/></td>
  </tr>
</table>

---

## 🎯 Training & Validation
## Plate Detection (YOLOv8n)
```
yolo train model=yolov8n.pt data=configs/plate.yaml epochs=40 imgsz=640
```
- **Best mAP@0.5**: 0.995
- **Val Precision**: 0.991
- **Val Recall**: 1.000

## Digit Detection (YOLOv8s)
```
yolo train model=yolov8s.pt data=configs/digits.yaml epochs=50 imgsz=640
```
- **Best mAP@0.5**: 0.983
- **Val Precision**: 0.970
- **Val Recall**: 0.985

---

## 📝 License
- **Code License**: This repository’s **code** is released under the MIT License.
- **Dataset License**: Persian Plate Detection & Persian Car Plates Digits Detection dataset from Kaggle, subject to Kaggle’s dataset license terms.

---

## 🤝 Contributing & Contact
Feel free to reach out by opening an issue or pull request. For direct questions, you may also contact:
* **Author**: Matin Gharehdaghi matingd.work@gmail.com

Feel free to open issues or PRs for improvements!
