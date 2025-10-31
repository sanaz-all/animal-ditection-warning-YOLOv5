
# 🐾 Animal Detection and Driver Alert System using YOLOv5

A university-level AI project that implements a real-time animal detection system using **YOLOv5s** to assist drivers by providing alerts when animals or pedestrians appear in dangerous proximity on rural or wildlife-prone roads.

---

## 📌 Project Overview

This system aims to reduce vehicle-animal collisions by detecting animals and estimating their distance from the camera in a video stream. The model is based on **YOLOv5s**, which outperforms traditional methods like HOG + Cascade Classifier as discussed in the IEEE paper:

> _"A Practical Animal Detection and Collision Avoidance System Using Computer Vision Technique"_

## 🚀 How It Works

This animal detection and warning assistant system works through the following pipeline:

1. **Load Pretrained Model (YOLOv5s):**  
   The pretrained `yolov5s.pt` model is loaded using `torch.hub` from the official [Ultralytics YOLOv5 repo](https://github.com/ultralytics/yolov5).

2. **Open Input Video:**  
   The input video is read frame-by-frame using OpenCV’s `cv2.VideoCapture()`.

3. **Resize Each Frame:**  
   Each frame is resized to a fixed resolution of **1280x720** to standardize input and improve distance estimation.

4. **Run YOLOv5 Detection:**  
   Each frame is passed to the YOLOv5 model which returns:
   - **Bounding boxes**
   - **Class labels**
   - **Confidence scores**

5. **Filter Detected Classes:**  
   Only animal-related and human-related classes (like `person`, `dog`, `cow`, `horse`, etc.) are kept for further processing.

6. **Estimate Distance:**  
   An approximate distance to each animal is calculated based on:
   - The size of the bounding box
   - Known average width of real animals
   - Basic camera perspective math (simplified for demonstration)

7. **Draw Danger Zone:**  
   A red "danger region" is drawn in the lower area of the frame — if an animal is detected within this zone and is close enough, a warning is triggered.

8. **Trigger Warnings and Braking Simulation:**  
   - If distance < threshold → `ALERT` is shown on screen  
   - Simulated braking command is activated (can be extended to real braking systems in advanced vehicles)

9. **Save the Output Video:**  
   The final processed video with annotations is saved using OpenCV’s `cv2.VideoWriter()` for review or demo purposes.

---

## 🧪 Evaluation

This system improves upon methods used in the IEEE paper:

> **"A Practical Animal Detection and Collision Avoidance System Using Computer Vision Technique"**

### 🔬 Comparison Table

| Method                   | Detection Accuracy | Real-Time Performance | Robustness |
|--------------------------|--------------------|------------------------|------------|
| HOG + Cascade Classifier | ❌ Low             | ❌ Slow                | ❌ Weak     |
| YOLOv5s (Ours)           | ✅ High            | ✅ Real-Time           | ✅ Strong   |

<img src="https://github.com/masoudjawnf/animal-detection-warning-yolov5/blob/main/HOG%2BCascade%20Vs%20YOLOv5%20.jpg?raw=true" width="500" style="margin-left:20px; display:block;" />




---

## 📦 Libraries Used

| Library    | Purpose                                    | Installation Command              |
|------------|--------------------------------------------|-----------------------------------|
| OpenCV     | Image/video processing                     | `pip install opencv-python`       |
| PyTorch    | Load YOLOv5 model and deep learning        | `pip install torch torchvision`   |
| NumPy      | Numerical operations                       | `pip install numpy`               |
| Matplotlib | (Optional) plotting/debugging              | `pip install matplotlib`          |

---

## 🧠 Use Cases

- Rural or wildlife-heavy highways  
- Smart vehicle alert systems  
- AI-enhanced driver assistance  
- Traffic camera animal filtering

---

## 📁 Dataset & Model

- Model: [YOLOv5s pretrained weights](https://github.com/ultralytics/yolov5/releases)
- Classes: COCO (80 object types including animals & humans)
- No custom training required.

---

## 🤖 Future Improvements

- Use depth sensors or stereo cameras for more accurate distance
- Train model with custom animal dataset for regional accuracy
- Add sound-based alerts and integration with car systems

---

## 📄 License

[MIT License](LICENSE)

---

## ✍️ Author

Developed by MasoudJanfeshan  
A university AI project demonstrating practical machine vision.

---

### 🤝 Contributors
- [SanazAllahyari](https://github.com/Sanaz-all)
- [MasoudJanfashan](https://github.com/MasoudJanfashan)
