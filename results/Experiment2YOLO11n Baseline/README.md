# Experiment 2: YOLO11n Baseline

## Overview

This experiment evaluates a YOLO11n object detection baseline on the football detection dataset with four classes:

- ball
- goalkeeper
- player
- referee

The model was trained with Ultralytics YOLO using the existing YOLO-format dataset and evaluated on the held-out test split.

## Training Configuration

| Item | Value |
|---|---|
| Model | YOLO11n |
| Pretrained weights | `yolo11n.pt` |
| Image size | 960 |
| Epochs | 50 |
| Batch size | 8 |
| Device | CUDA:0 |
| Dataset format | YOLO |
| Classes | 4 |

The main training artifacts are stored in this directory, including:

- `args.yaml`
- `results.csv`
- `results.png`
- `confusion_matrix.png`
- `confusion_matrix_normalized.png`
- `BoxPR_curve.png`
- `BoxF1_curve.png`
- `weights/best.pt`
- `weights/last.pt`

Note: the training run directory was reused during earlier interrupted runs, so `results.csv` may contain appended epoch rows from multiple attempts. The final model checkpoint and test-set results below are the primary reference.

## Test Set Results

The best checkpoint was evaluated on the test split:

```text
weights: weights/best.pt
split: test
images: 25
instances: 599
```

### Overall Metrics

| Metric | Value |
|---|---:|
| Precision | 0.795 |
| Recall | 0.806 |
| mAP50 | 0.802 |
| mAP50-95 | 0.567 |

### Per-Class Metrics

| Class | Precision | Recall | mAP50 | mAP50-95 |
|---|---:|---:|---:|---:|
| ball | 0.648 | 0.292 | 0.352 | 0.103 |
| goalkeeper | 0.911 | 1.000 | 0.948 | 0.749 |
| player | 0.890 | 0.986 | 0.988 | 0.794 |
| referee | 0.730 | 0.946 | 0.919 | 0.620 |

Full test artifacts are stored in `test/`, including:

- `test/test_summary.json`
- `test/confusion_matrix.png`
- `test/confusion_matrix_normalized.png`
- `test/BoxPR_curve.png`
- `test/val_batch*_labels.jpg`
- `test/val_batch*_pred.jpg`

## Key Findings

- The YOLO11n baseline performs strongly on `player`, `goalkeeper`, and `referee`.
- The main weakness is `ball` detection.
- Ball recall is only 0.292 on the test set, indicating that many football instances are missed.
- The overall score is strongly influenced by the large number of player instances.

## Recommended Next Steps

1. Add more ball-focused training examples, especially small, distant, blurred, partially occluded, and airborne balls.
2. Audit the dataset for missing ball labels.
3. Increase input resolution to 1280 for small-object experiments.
4. Compare YOLO11n with YOLO11s under the same dataset split and test protocol.
5. Keep future experiment directories unique to avoid appended `results.csv` histories.
