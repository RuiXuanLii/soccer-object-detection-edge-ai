# ⚽ Edge AI Football Player Detection

## 📌 Project Overview

This project develops a lightweight **edge-deployable object detection system** for football match scenes using Edge Impulse.

The system focuses on detecting key entities in football videos, including:

- Ball
- Player
- Referee
- Goalkeeper

The goal is to explore how well lightweight edge models can perform in real-world sports environments under computational constraints.

---

## 🎯 Objectives

This project aims to:

- Build a real-time football scene object detection system
- Deploy a lightweight model on edge devices using Edge Impulse
- Evaluate performance under constrained hardware conditions
- Analyze failure cases in complex sports environments
- Explore future improvements using generative AI models

---

## 📊 Dataset

The dataset is sourced from Hugging Face:

👉 https://huggingface.co/datasets/martinjolif/football-player-detection

### Characteristics:
- Real football match images (frame-based extraction)
- YOLO-format bounding box annotations
- Single-match dataset (limited diversity)
- Strong temporal correlation between samples

### Classes:
| Class | Description |
|------|-------------|
| ball | Football ball |
| player | Field players |
| referee | Match referee |
| goalkeeper | Goalkeeper |

---

## ⚙️ Model Pipeline

1. Image preprocessing (224×224 resizing)
2. Edge Impulse image processing block
3. FOMO object detection model (MobileNetV2-0.35 backbone)
4. Model quantization (INT8)
5. Edge deployment optimization (EON Compiler)

---

## 🧠 Model Configuration

- Framework: Edge Impulse
- Model: FOMO (Faster Objects, More Objects)
- Backbone: MobileNetV2 (0.35 width multiplier)
- Input size: 224 × 224
- Output classes: 4
- Optimized format: INT8 quantized model

---

## 📈 Experimental Results

### Validation Performance

- Precision (non-background): **0.95**
- Recall (non-background): **0.62**
- F1 Score: **0.75**

---

### Per-Class Behavior (Key Observations)

- **Player**: strongest performance (~68% correct classification)
- **Ball**: moderate performance, high background confusion (~36.6% correct)
- **Referee**: weak detection performance (~12.9%)
- **Goalkeeper**: failed detection in most cases (0% recall)

---

### Test Set Performance

- Average F1 score: ~70–75%
- Range: 56% – 82%

---

### Model Efficiency (Edge Deployment)

- Inference time: **3276 ms**
- RAM usage: **562.0 kB**
- Flash usage: **81.4 kB**
- Runtime: EON Compiler (RAM optimized)

---

### Float32 Baseline (Unoptimized)

- Accuracy: **25.68%**

This shows that **quantization is essential for stable edge performance**.

---

## 🔍 Key Findings

- The model performs reasonably well for the **player class**, but struggles with minority classes.
- Severe **class imbalance and dataset bias** affect performance.
- Strong **background confusion** indicates limited feature separability.
- Goalkeeper and referee classes are underrepresented or difficult to generalize.

---

## ⚠️ Limitations

- Dataset is derived from a single football match
- High temporal redundancy between frames
- Limited scene diversity (lighting, camera angle, stadium)
- Class imbalance across categories
- Potential overfitting to match-specific features

---

## 🚀 Future Work

To improve model performance and generalization, the project will explore:

### 1. Data Expansion
- Multi-match datasets
- More diverse stadium environments

### 2. Model Improvements
- Comparison with YOLOv8n / lightweight detection models
- Improved augmentation strategies

### 3. 🔥 Generative AI Integration (Planned)

The project group will further investigate the integration of **generative AI models**, including:

- Synthetic data generation for underrepresented classes
- Data augmentation using diffusion-based image generation
- Scene diversification using generative models
- Potential improvement of detection robustness via synthetic training data

The hypothesis is that:
> Generative models may improve model generalization by enriching dataset diversity and reducing class imbalance.

---

## 🧪 Technologies Used

- Edge Impulse
- FOMO (MobileNetV2 backbone)
- YOLO-format dataset
- Hugging Face Datasets
- TensorFlow Lite (Edge deployment)

---

## 📚 Dataset Source

- https://huggingface.co/datasets/martinjolif/football-player-detection

---

## 👥 Project Status

- Dataset integration ✔
- Baseline model training ✔
- Evaluation completed ✔
- Generative AI extension (planned ⏳)

---

## 📄 License

For academic and research purposes. Dataset follows original Hugging Face license.

## 📄 License

This project follows the dataset license provided by Hugging Face and is intended for academic / research use.
