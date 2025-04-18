# F1-Overtake-Classification

#  Formula 1 Overtake Detection using YOLOv5 & Computer Vision

This project focuses on detecting and classifying **types of overtakes in Formula 1 race videos** using custom-trained YOLOv5 models, **Centroid Tracking**, and **Edge-Based Line Detection (Canny + Hough Transform)**.

---

## Objective

To identify F1 cars and classify overtaking maneuvers such as:
- **DRS Overtakes**
- **Outside Line Overtakes**
- **Squeezing Defender**
- **Corner Overtakes**

---

##  Input

- YouTube race highlight videos
- Frames extracted at **5 FPS** using OpenCV

---

##  Preprocessing

- **Noise Reduction:** Gaussian Blur
- **Normalization:** Standard pixel scaling
- **Color Space Analysis:** Hue-based filtering for car/team color detection
- **Background Subtraction:** Remove track background artifacts
- **Bounding Boxes:** For team-specific car annotation

---

## Detection Model

- **Model:** YOLOv5 (custom-trained)
- **Classes:** Ferrari, Red Bull, Mercedes, etc.
- **Purpose:** Detect and localize F1 cars with team-specific labels

---

##  Tracking

- **Technique:** Centroid Tracking (via Euclidean distance)
- **Why?:** Lightweight, real-time, perfect for smooth, consistent detections from YOLO
- **Alternative Methods Considered:** Kalman Filter (too complex), DeepSORT (overkill for this use case)

---

##  Overtake Classification Logic

| Overtake Type          | Detection Method                       |
|------------------------|----------------------------------------|
| DRS Overtake           | Centroid movement: back to front       |
| Outside Line Overtake  | Lateral centroid shift across lanes    |
| Squeezing Defender     | Canny Edge + Hough Line + Car Proximity |
| Corner Overtake        | Canny Edge + Hough + Curved Trajectories |

---

##  Performance Metrics

### 1. Accuracy & Precision
- **Overall Accuracy:** 77.4%
- **DRS Overtake:** 81.2%
- **Outside Line:** 74.6%
- **Squeezing Defender:** 75.1%
- **Corner Overtake:** 78.3%

### 2. Recall
- High recall in Corner and DRS Overtakes (≈ 80%)

### 3. F1-Score
- Balanced across all classes (75%–80%)

---

##  Sample Visualizations

-  Bounding boxes for detected cars
-  Tracked centroids across frames
-  Overtake annotations (classified type)
-  Heatmap (Confusion Matrix) of classification results

---
