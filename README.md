# ⚽ Football Player Detection with YOLO26 Nano

A computer vision project for **football player and football detection** using the **YOLO26 Nano** object detection model.

> 🚧 **Project Status:** In Progress
>
> Replace this line with the current project status, for example:
> `Completed` / `In Progress` / `Experimental`

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

* ⚽ Football detection
* 🧍 Player detection
* 🎯 Bounding-box based object detection
* 🧠 YOLO26 Nano architecture
* 📊 Model evaluation using Precision, Recall and mAP
* 🚀 Image inference
* 🎥 Video inference — **TODO: confirm whether implemented**

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
| Device      | `TODO: optionally describe as CUDA/GPU without mentioning specific hardware`  |
| Ultralytics | `8.4.114`                                                                     |

> 📝 **TODO:** If you changed any training parameter manually, add it to this table.

---

# 📊 Dataset

## Dataset Description

> 📝 **TODO: Describe the dataset here.**

Include:

* Dataset source: `TODO`
* Dataset type: `TODO`
* Total number of images: `TODO`
* Number of classes: `2`
* Classes: `player`, `football`
* Annotation format: `YOLO`
* Image resolution: `TODO`

### Dataset Source

> 📝 **TODO:** Add the dataset source/link here if publicly available.

`TODO — Dataset URL`

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

> 📝 **TODO:** Replace this structure with the actual dataset structure if it is different.

---

## 📈 Dataset Statistics

> 📝 **TODO:** Complete the table using the actual dataset statistics.

| Split      |  Images | Instances |
| ---------- | ------: | --------: |
| Train      |  `TODO` |    `TODO` |
| Validation |  `TODO` |    `TODO` |
| Test       | **520** | **2,903** |

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

> 📝 **TODO:** Add other important training settings if you intentionally configured them.

---

# 📉 Training Results

> 📝 **TODO: Add your training result image here.**

Recommended file:

```text
results.png
```

Example:

```markdown
![Training Results](results.png)
```

### 📊 Training Curves

> 📝 **TODO:** Add the training curves/results image.

```markdown
![Training Curves](path/to/results.png)
```

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

> 📝 **TODO:** Add your own explanation here.

Possible points to discuss:

* Why player detection performs better
* Why football detection is more difficult
* Small object detection
* Occlusion
* Motion blur
* Different camera angles
* Similarity between football and background
* Dataset imbalance

---

# 🖼️ Detection Results

> 📝 **TODO: Add prediction examples here.**

Place your output images inside a folder such as:

```text
results/
├── detection_01.jpg
├── detection_02.jpg
├── detection_03.jpg
└── detection_04.jpg
```

Then add them to the README:

```markdown
## 🔎 Detection Examples

![Detection Example 1](results/detection_01.jpg)

![Detection Example 2](results/detection_02.jpg)

![Detection Example 3](results/detection_03.jpg)
```

> ⭐ **Recommended:** Add 3–6 good examples showing both successful player and football detections.

---

# 🎥 Video Detection

> 📝 **TODO: Complete this section only if you performed detection on videos.**

Describe:

* Input video format
* Output video format
* Whether inference is frame-by-frame
* Whether tracking is used
* Approximate FPS if measured

Example:

```text
Input Video
     ↓
YOLO26 Nano
     ↓
Object Detection
     ↓
Bounding Boxes
     ↓
Output Video
```

---

# 🚀 Inference

## Image Inference

> 📝 **TODO:** Add your actual inference code here.

```python
from ultralytics import YOLO

model = YOLO("path/to/best.pt")

results = model.predict(
    source="path/to/image.jpg",
    imgsz=320,
    conf=0.25
)
```

### Run Prediction

```bash
python predict.py
```

> 📝 **TODO:** Replace this command with the actual command used in your project.

---

# 📁 Project Structure

> 📝 **TODO: Replace this with your actual project structure.**

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
│   └── TODO
│
├── src/
│   └── TODO
│
├── requirements.txt
└── README.md
```

> ⚠️ **TODO:** Keep only the folders that actually exist in your project structure — remove anything that doesn't.

---

# ⚙️ Installation

## Requirements

> 📝 **TODO:** Add your actual Python and package requirements.

Recommended format:

```text
Python >= TODO
Ultralytics == TODO
PyTorch == TODO
OpenCV == TODO
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

> 📝 **TODO:** If you don't have a `requirements.txt`, list the packages you installed so this section can be completed.

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

> 📝 **TODO:** Specify whether the model weights are included in the GitHub repository or not.

Possible options:

### Option 1 — Local Weights

```text
weights/
└── best.pt
```

### Option 2 — Download

```markdown
Download the trained weights from:

TODO — Link
```

> ⚠️ If you are not including the weights file in GitHub, explain here how to obtain it.

---

# 🛠️ Technologies

* 🐍 Python
* 🔥 PyTorch
* 🧠 Ultralytics
* 🎯 YOLO26 Nano
* 👁️ Computer Vision
* 📦 OpenCV — **TODO: confirm**
* 📊 NumPy — **TODO: confirm**

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

> 📝 **TODO:** Describe the main challenges of the project.

Possible challenges:

* ⚽ Small football objects
* 🧍 Multiple players in a single frame
* 👥 Overlapping players
* 🌫️ Motion blur
* 📷 Different camera perspectives
* 🌱 Complex football-field backgrounds
* ⚖️ Class imbalance
* 🔍 Low-resolution football objects

---

# 🚧 Limitations

> 📝 **TODO:** Based on your results, describe the limitations.

For example:

* Football detection performance is lower than player detection.
* Small objects are harder to detect.
* The model was trained for only 10 epochs.
* Detection performance may vary across different camera angles and lighting conditions.

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

> 📝 **TODO:** Add a short personal conclusion about what you learned from the project.

---

# 👨‍💻 Author

**TODO — Your Name**

* GitHub: `TODO`
* LinkedIn: `TODO`
* Email: `TODO`

---

# ⭐ Acknowledgements

This project uses the **Ultralytics YOLO** framework for object detection.

> 📝 **TODO:** Add dataset author/source and other references here.

---

# 📜 License

> 📝 **TODO:** Choose a license for the repository.

Examples:

```text
MIT License
Apache License 2.0
GPL-3.0
```

If you do not want to specify a license yet:

```text
License: Not specified
```

