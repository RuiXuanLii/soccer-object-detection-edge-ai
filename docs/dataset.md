# 📊 Dataset Description - Football Player Detection

## 📌 Overview

This project uses an open-source dataset for football player detection:

👉 Source: https://huggingface.co/datasets/martinjolif/football-player-detection

The dataset contains annotated images from football matches, designed for object detection tasks including players and other related entities.

---

## 🧠 Task Definition

This project focuses on **object detection in football scenes**, with the goal of identifying:

- Player
- Referee
- (Optional / dataset-dependent) Other classes

The dataset provides bounding box annotations in YOLO format.

---

## 📁 Dataset Structure

After downloading, the dataset is organized as follows:
images/
├── train/
├── val/
├── test/

labels/
├── train/
├── val/
├── test/

Each image has a corresponding `.txt` annotation file in YOLO format.

---

## 🏷️ Annotation Format (YOLO)

Each label file follows the format:
<class_id> <x_center> <y_center> <width> <height>

Where:
- `class_id`: integer representing category
- coordinates are normalized (0–1)

Example:0 0.512 0.433 0.120 0.300

---

## 🧾 Class Mapping

The class mapping used in this project:

| Class ID | Class Name |
|----------|------------|
| 0        | player     |
| 1        | referee    |
| 2        | spectator (if applicable) |

> ⚠️ Note: Final class set depends on dataset version and preprocessing.

---

## 🔄 Data Preprocessing

Before training in Edge Impulse:

- Images are resized to model input size (e.g. 96x96 or 160x160)
- YOLO annotations are converted to bounding boxes compatible with Edge Impulse format
- Dataset is split into:
  - Training set
  - Validation set
  - Test set

---

## ⚠️ Dataset Limitations

- Data comes from a **single football match**
- High frame similarity (video-derived images)
- Possible overfitting risk due to temporal correlation
- Limited diversity in lighting, stadium, and camera angles

---

## 📈 Implications for Model Training

Due to dataset characteristics:

- Model may learn scene-specific patterns
- Generalization to other matches may be limited
- Additional data from other matches is recommended

---

## 🚀 Future Improvements

To improve robustness:

- Add multiple match datasets
- Include different stadium environments
- Add augmentation (blur, brightness, rotation)
- Balance class distribution (especially referee / spectator)

---

## 📚 Source

- Dataset: https://huggingface.co/datasets/martinjolif/football-player-detection
- License: Follow original dataset license on Hugging Face
