# 🦅 Aerial Object Classification & Detection (Bird vs. Drone)

## 📌 Project Overview
This project delivers a deep learning-based computer vision solution engineered to identify and distinguish between birds and drones in aerial imagery. By combining a **Custom CNN classification model**, **Transfer Learning**, and real-time **YOLOv8 Object Detection**, this system addresses critical needs in airspace safety, security surveillance, and wildlife monitoring. The final models are accessible via an interactive web interface built with **Streamlit**.

---

## 🛠️ Skills Acquired & Demonstrated
* **Deep Learning & Computer Vision:** Designing convolutional networks and implementing object detection pipelines.
* **Framework Proficiency:** Building pipelines using **TensorFlow/Keras** or **PyTorch**.
* **Advanced Data Augmentation:** Improving model robustness against variations in lighting, rotation, and scale.
* **State-of-the-Art Detection (YOLOv8):** Training an end-to-end model with normalized bounding-box coordinates.
* **Model Serialization & Deployment:** Exporting best-performing weights and building an interactive Streamlit UI.

---

## 🌍 Domain
* Aerial Surveillance & Security
* Aerospace Safety & Airspace Management
* Wildlife Monitoring & Environmental Conservation

---

## 📝 Problem Statement
The growth of low-altitude drone usage introduces serious challenges regarding security breaches, restricted airspace violations, and hazards near airport runways. Simultaneously, distinguishing small unmanned aerial vehicles (UAVs) from birds using automated monitoring systems remains difficult due to visual similarities at high altitudes. This project provides an automated tool to classify and localize these objects to ensure airspace safety and prevent accidents.

---

## 📊 Real-Time Business Use Cases

### 🛡️ Security & Defense Surveillance
* Detects and flags unauthorized drones in restricted airspaces or military zones to initiate prompt defense responses.

### 🛫 Airport Bird-Strike Prevention
* Monitors runway airspaces continuously for incoming bird flocks or rogue drones to safeguard commercial flights.

### 💨 Wildlife Protection & Green Energy
* Prevents bird collisions at wind farms by automatically triggering deterrent systems when avian activity is detected.

### 🔬 Environmental Research
* Automates wildlife census workflows by tracking local bird migrations using high-resolution aerial video streams.

---

## 📦 Dataset Characteristics & Structure

### 🗂️ 1. Image Classification Dataset (Binary: Bird / Drone)
* **Format:** RGB Images (`.jpg`)
* **Resolution Target:** Resized and normalized to \(224 \times 224\) pixels.
* **Data Splits:**
  * **Train Set:** 1,414 Bird images | 1,248 Drone images
  * **Validation Set:** 217 Bird images | 225 Drone images
  * **Test Set:** 121 Bird images | 94 Drone images

### 🎯 2. Object Detection Dataset (YOLOv8 Format)
* **Total Scale:** 3,319 images matching corresponding layout labels (`.txt` files).
* **Label Layout:** `<class_id> <x_center> <y_center> <width> <height>` (normalized values).
* **Data Splits:** Train (2,662) | Validation (442) | Test (215).

---

## 🔧 Project Workflow & Core Architecture

### Phase 1: Preprocessing & Data Augmentation
* Normalized pixel channels to `[0, 1]` ranges.
* Implemented ImageNet channel normalization scripts for transfer learning architectures.
* Applied pipeline augmentation fields: random rotations, horizontal/vertical flips, zoom modifications, and brightness adjustments.

### Phase 2: Classification Engine Construction
* **Custom CNN Architecture:** Sequential Convolution blocks paired with Batch Normalization, Dropout configurations, Max Pooling layers, and Dense output heads.
* **Transfer Learning:** Fine-tuned state-of-the-art pretrained structures (e.g., ResNet50, MobileNet, or EfficientNetB0).
* **Training Management:** Leveraged `EarlyStopping` and `ModelCheckpoint` callbacks monitoring Validation Loss.

### Phase 3: Object Detection Node (YOLOv8 Optional Path)
* Configured target data pointers inside a custom `data.yaml` layout map.
* Initiated YOLOv8 network training, tuning spatial configuration bounds.
* Validated tracking bounding boxes using Mean Average Precision metrics (\(mAP_{50}\) and \(mAP_{50-95}\)).

### Phase 4: Production Deployment
* Consolidated classification weights and localized detection checkpoints.
* Built a **Streamlit** user interface that processes real-time image uploads, exposes confidence scores, and plots diagnostic target bounding boxes.

---

## 📂 Repository Layout
```text
├── data/                  # Classification folders & YOLOv8 structured maps
├── models/                # Saved weights (.h5, .pt, or .onnx files)
├── notebooks/             # Preprocessing notebooks, training trials, and valuation charts
├── src/                   # Helper components (data loaders, augmentations, evaluation utilities)
├── app/                   # Streamlit production front-end code
├── requirements.txt       # Python environment dependencies layout
└── README.md              # Project documentation file
```

---

## 🚀 Getting Started

### Prerequisites
* Python 3.8+
* Modern GPU with CUDA acceleration configuration (Highly Recommended for YOLOv8)
