# 🍩 Pastry Object Detection using YOLOv11  

## 📌 Project Overview  
This project focuses on **object detection** applied to pastry products, including **pain au chocolat, éclair, muffin, donut, and tart**. The goal is to fine-tune **YOLOv11**, a state-of-the-art object detection model, to accurately detect and classify these pastries within images.  

This project was entirely **developed and trained using Google Colab**, leveraging its cloud-based GPU acceleration for efficient model training.  

We collected and annotated a **small dataset (100 images)**, conducted multiple training experiments with different hyperparameter configurations, and evaluated the model’s performance using quantitative and qualitative metrics.  

---

## 🚀 Features  
- ✅ **Fine-tuned YOLOv11 model** for pastry detection.  
- ✅ **Custom dataset** with annotated images.  
- ✅ **Data augmentation** using **Albumentations** to enhance generalization.  
- ✅ **Hyperparameter optimization** through multiple training attempts.  
- ✅ **Evaluation and visualization** of model performance on test images.  

---

## 📂 Dataset Structure  
The dataset consists of **100 images**, split as follows:  

- **Training set**: 70 images  
- **Validation set**: 20 images  
- **Test set**: 10 images  

Each image is labeled with bounding boxes and stored in YOLO format. The dataset includes five classes:  

1. **Pain au chocolat**  
2. **Éclair**  
3. **Muffin**  
4. **Donut**  
5. **Tart**  

---

## ⚙️ Installation  

### 1️⃣ Clone the repository  
```bash
git clone https://github.com/akremjomaa/Pastry-Object-Detection.git
cd Pastry-Object-Detection
```

### 2️⃣ Install dependencies  
```bash
pip install ultralytics albumentations opencv-python matplotlib
```

---

## 🏋️‍♂️ Model Training  

To train the YOLOv11 model, run the following command:  
```python
from ultralytics import YOLO

# Load the pretrained YOLOv11 model
model = YOLO("yolo11n.pt")

# Train the model
model.train(data="dataset_yolov11/data.yaml", epochs=50, imgsz=640, batch=16, patience=10, lr0=0.01, lrf=0.0001)
```

---

## 📊 Evaluation  

Once the model is trained, evaluate its performance using:  
```python
# Load best model
best_model = YOLO("runs/detect/train/weights/best.pt")

# Validate the model
metrics = best_model.val()
print(f"mAP50-95: {metrics.box.map}")
```

### **Results Analysis**
- 📌 **Confusion matrix** shows correct and incorrect classifications.  
- 📌 **F1-score curve** helps determine the optimal confidence threshold.  
- 📌 **Visual predictions** on test images to assess model accuracy.  

---

## 🎯 Predictions on Test Images  

Run the model on new images:  
```python
from PIL import Image

# Load test image
test_image = Image.open("dataset_yolov11/test/images/sample.jpg")

# Predict
results = best_model.predict(source=test_image, save=True)
```

The predictions are stored in the `runs/detect/predict/` directory.


---


## 📜 License  
This project is open-source and available under the **MIT License**.  

---

## 👤 Author  
**Akrem JOMAA**  
📧 Contact: [akrem.jomaa@univ-lyon2.fr](mailto:akrem.jomaa@univ-lyon2.fr)  
🔗 LinkedIn: [akremjomaa](www.linkedin.com/in/akremjomaa)  
📂 GitHub: [github.com/akremjomaa](https://github.com/akremjomaa)  

---

🚀 **If you find this project useful, don't forget to star ⭐ the repository!**  
