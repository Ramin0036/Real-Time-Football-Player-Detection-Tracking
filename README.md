# ⚽ Real-Time Football Player Detection with YOLO26 Nano

A real-time computer vision project for detecting **football players** and the **football** in video streams using the **YOLO26 Nano** object detection model.

The model is trained on a custom football detection dataset and used for frame-by-frame object detection on football videos.

> 🚧 **Project Status:** `In Progress`

---

## 📌 Overview

This project focuses on detecting **football players** and the **football** in football-related images using the YOLO26 Nano object detection architecture.

The model was trained on a custom football detection dataset and evaluated on a separate test set.

### 🎯 Detection Classes

| Class      | Description            |
| ---------- | ----------------------- |
| `player`   | Football players        |
| `football` | Football / soccer ball  |

---

## ✨ Features

- ⚽ Football detection
- 🧍 Player detection
- 🎯 Bounding-box based object detection
- 🧠 YOLO26 Nano architecture
- 📊 Model evaluation using Precision, Recall and mAP
- 🎥 Video-based object detection
- ⚡ Real-time frame-by-frame inference
- 🖥️ GPU-accelerated inference using CUDA

---

## 🧠 Model

### YOLO26 Nano

The project uses the **YOLO26 Nano (`yolo26n.pt`)** model as the base architecture.

| Parameter   | Value                                                                        |
| ----------- | ----------------------------------------------------------------------------- |
| Model       | `YOLO26 Nano`                                                                 |
| Task        | Object Detection                                                              |
| Pretrained  | `Yes`                                                                         |
| Input Size  | `320 × 320`                                                                   |
| Epochs      | `10`                                                                          |
| Batch Size  | `128`                                                                         |
| Optimizer   | `Auto`                                                                        |
| Workers     | `0`                                                                           |
| Device      | `CUDA GPU`
| Ultralytics | `8.4.114`                                                                     |

---

# 📊 Dataset

## Dataset Description

The dataset used in this project is the **Football Player Detection YOLOv8** dataset, obtained from Kaggle.

The dataset contains football-related images annotated for object detection. The annotations follow the **YOLO format** and include two object classes: `player` and `football`.

### 🎯 Dataset Information

| Property                  | Value                            |
| ------------------------- | -------------------------------- |
| Dataset                   | Football Player Detection YOLOv8 |
| Source                    | Kaggle                           |
| Task                      | Object Detection                 |
| Classes                   | `player`, `football`             |
| Annotation Format         | YOLO                             |
| Original Image Resolution | `1280 × 12808`                    |
| Dataset Type              | Football / Sports Images         |

### 🔗 Dataset Source

The original dataset is available on Kaggle:

[Football Player Detection YOLOv8](https://www.kaggle.com/datasets/iasadpanwhar/football-player-detection-yolov8)

---

## 📁 Dataset Structure

```text
dataset/
│
├── train/
│   ├── images/
│   └── labels/
│
├── val/
│   ├── images/
│   └── labels/
│
├── test/
│   ├── images/
│   └── labels/
│
└── data.yaml
```

---

## 📈 Dataset Statistics

The dataset was divided into training, validation, and test subsets.

| Split      |     Images |  Instances |
| ---------- | ---------: | ---------: |
| Train      | **10,308** | **48,810** |
| Validation |    **972** |  **2,903** |
| Test       |    **520** |  **2,903** |
| **Total**  | **11,800** | **54,616** |

---

## 🎯 Classes

| Class      | Description            |
| ---------- | ---------------------- |
| `player`   | Football players       |
| `football` | Football / soccer ball |

The dataset contains significantly more `player` annotations than `football` annotations. This class imbalance is one of the factors that can make football detection more challenging.

---

## 🏷️ Annotation Format

The dataset uses the **YOLO annotation format**.

Each image has a corresponding `.txt` annotation file containing the object class and normalized bounding-box coordinates.

The annotation format follows:

`class_id x_center y_center width height`

For example:

`1 0.512 0.431 0.125 0.245`

Where:

* `class_id` → Object class identifier
* `x_center` → Normalized bounding-box center X
* `y_center` → Normalized bounding-box center Y
* `width` → Normalized bounding-box width
* `height` → Normalized bounding-box height

All bounding-box coordinates are normalized to the range `[0, 1]`.

---

## 🖼️ Image Resolution

The original images have a resolution of:

**1280 × 1280**

During model training, the images were resized to:

**320 × 320**

using the `imgsz=320` training configuration.

---

# 🏋️ Training

The YOLO26 Nano model was fine-tuned on the football detection dataset using the Ultralytics framework.

### Training Configuration

```python
from ultralytics import YOLO

model = YOLO("yolo26n.pt")

result = model.train(
    data="path/to/data.yaml",
    epochs=10,
    imgsz=320,
    batch=128,
    workers=0,
    device=0
)
```

### Training Details

| Parameter          | Value        |
| ------------------- | ------------ |
| Epochs              | `10`         |
| Image Size          | `320 × 320`  |
| Batch Size          | `128`        |
| Workers             | `0`          |
| Pretrained Model    | `yolo26n.pt` |
| Number of Classes   | `2`          |

---

# 📉 Training Results

<img width="2400" height="1200" alt="results" src="https://github.com/user-attachments/assets/8f97ea0e-1cdd-46f5-bbbb-896f09ab985e" />

### 📊 Training Curves

<img width="2250" height="1500" alt="BoxF1_curve" src="https://github.com/user-attachments/assets/f3875907-1eec-4df3-a73e-a378970f395d" /><img width="2250" height="1500" alt="BoxR_curve" src="https://github.com/user-attachments/assets/29eae288-e26f-415e-9755-303c4808d666" />
<img width="2250" height="1500" alt="BoxPR_curve" src="https://github.com/user-attachments/assets/702ebd8d-3768-49a8-8e7a-6b1d5a0ce835" />
<img width="2250" height="1500" alt="BoxP_curve" src="https://github.com/user-attachments/assets/d4e5a368-3896-4ef5-8423-58021c394f91" />


---

# 🔍 Model Evaluation

The trained model was evaluated on the **test split** containing:

* **520 images**
* **2,903 annotated instances**

### Overall Results

| Metric    |      Score |
| --------- | ---------: |
| Precision | **76.62%** |
| Recall    | **58.61%** |
| mAP@50    | **61.48%** |
| mAP@50-95 | **36.19%** |

---

## 📊 Per-Class Results

| Class      |  Precision |     Recall |     mAP@50 |  mAP@50-95 |
| ---------- | ---------: | ---------: | ---------: | ---------: |
| `football` | **69.20%** | **29.00%** | **32.20%** | **14.90%** |
| `player`   | **84.10%** | **88.30%** | **90.80%** | **57.50%** |

### 🧠 Results Analysis

The model performs significantly better at detecting **players** than the football itself.

---

# 🎥 Detection Results

The trained **YOLO26 Nano** model was used for real-time object detection on football videos.

The model processes video frames sequentially and detects two object classes:

- 🧍 `player`
- ⚽ `football`

For each detected object, the model generates a bounding box, predicted class, and confidence score.

## ⚡ Real-Time Detection

The model achieved an inference speed of approximately **28 FPS** during video detection.

This allows the trained model to perform real-time football object detection on video streams.

### 🎬 Detection Pipeline

Input Video  
↓  
Video Frame  
↓  
YOLO26 Nano  
↓  
Object Detection  
↓  
Bounding Boxes + Confidence  
↓  
Output Frame  
↓  
Output Video

## 📹 Detection Output

The trained model was applied to football video footage to detect players and the football in each frame.

The output video contains bounding boxes around the detected objects, along with their predicted class labels and confidence scores.

### 🎯 Detected Objects

| Class | Description |
|---|---|
| 🧍 `player` | Detected football players |
| ⚽ `football` | Detected football |

### 📊 Detection Performance

| Metric | Value |
|---|---:|
| Model | YOLO26 Nano |
| Input | Football Video |
| Output | Annotated Video |
| Inference Speed | **28 FPS** |
| Detection Classes | **2** |

## 🎥 Output Video

The final output of the project is an annotated football video with real-time detection of players and the football.

The model processes the video at approximately **28 FPS** and generates bounding boxes for the detected objects.

### ▶️ Detection Demo

> 📌 The following video demonstrates the real-time detection performance of the trained YOLO26 Nano model.

**Output Video:** 

<img width="692" height="388" alt="video2 - Copy_02" src="https://github.com/user-attachments/assets/cec7a4c2-91d3-406e-b9a2-74b6765e0d86" />

---

# 🚀 Inference

The trained **YOLO26 Nano** model was used for object detection and tracking on football videos.

The inference pipeline uses **ByteTrack** to maintain object identities across consecutive video frames, enabling consistent tracking of detected players and footballs.

## 🎥 Video Detection & Tracking

The trained model was applied to a football video using the Ultralytics tracking API.

```python
from ultralytics import YOLO

best_model = YOLO("path/to/best.pt")

results = best_model.track(
    source="path/to/video.mp4",
    save=True,
    show=True,
    tracker="bytetrack.yaml"
)

---

# 📁 Project Structure

```text
football_players_detection/
│
├── dataset/
│   └── football_players_detection/
│       ├── train/
│       ├── val/
│       ├── test/
│       └── data.yaml
│
├── runs/
│   └── detect/
│       └── ...
│
├── weights/
│   └── best.pt
│
├── notebooks/
│   └── Footbal-Players-Detection-Yolo26n.ipynb
│
└── README.md
```

---

# ⚙️ Installation

## Requirements

Recommended format:

```text
Python >= 3.13.9
Ultralytics == 8.4.114
PyTorch == 2.13.0+cu130
```

---

# ▶️ How to Run

## 1. Clone the Repository

```bash
git clone TODO
cd TODO
```

> 📝 **TODO:** Replace with your GitHub repository URL and repository name.

## 2. Install Dependencies

```bash
pip install -r requirements.txt
```

## 3. Run Inference

```bash
TODO
```

## 4. Train the Model

```bash
TODO
```

---

# 📦 Model Weights

```text
weights/
└── best.pt
```

---

# 🛠️ Technologies

* 🐍 Python
* 🔥 PyTorch
* 🧠 Ultralytics
* 🎯 YOLO26 Nano
* 👁️ Computer Vision

---

# 📚 Evaluation Metrics

### Precision

Measures how many of the detected objects are actually correct.

### Recall

Measures how many of the actual objects were successfully detected.

### mAP@50

Mean Average Precision at an IoU threshold of 0.50.

### mAP@50-95

Mean Average Precision averaged over IoU thresholds from 0.50 to 0.95.

---

# 🔬 Challenges

* ⚽ Small football objects
* 🧍 Multiple players in a single frame
* 👥 Overlapping players
* 📷 Different camera perspectives
* 🔍 Low-resolution football objects

---

# 🔮 Future Improvements

> 📝 **TODO:** Select the improvements you actually want to mention.

Possible improvements:

* [ ] Increase training epochs
* [ ] Increase input resolution
* [ ] Improve football annotations
* [ ] Add more football images
* [ ] Handle small-object detection
* [ ] Apply stronger data augmentation
* [ ] Experiment with larger YOLO models
* [ ] Add object tracking
* [ ] Evaluate on real match videos
* [ ] Optimize inference speed

---

# 📌 Conclusion

This project demonstrates the use of **YOLO26 Nano** for detecting football players and footballs in football-related images.

The model achieved:

* **76.62% Precision**
* **58.61% Recall**
* **61.48% mAP@50**
* **36.19% mAP@50-95**

The results show strong performance for **player detection**, while **football detection** remains a more challenging task due to the small size and visual characteristics of the ball.

---

# 👨‍💻 Author

**Ramin Allahverdizadeh**

* GitHub: Ramin0036
* Email: Ramin.allahverdizadeh1998@gmail.com
