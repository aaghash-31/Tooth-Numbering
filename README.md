## **Tooth Detection using YOLOv8**

 ## **Project Overview**
 
This project trains a YOLOv8 object detection model to detect and number teeth in panoramic dental X-ray images.
The dataset contains ~500 images with YOLO-format annotations. The goal is to train a robust model that can accurately detect and classify teeth.

 ## **Repository Structure**
```
tooth-numbering/
│── data.yaml              # Dataset configuration file
│── Tooth_numbering.ipynb  # Training, Post-processing & visualization           
│── requirements.txt       # Required dependencies
│── README.md              # Project documentation
```

 ## **Environment Setup**
 
You can set up the environment in **Google Colab** or locally.
**1. Clone Repository**
```bash
git clone https://github.com/<your-username>/tooth-detection-yolov8.git
cd tooth-detection-yolov8
```
**2. Install Dependencies**
```bash
pip install -r requirements.txt
```
**3. Dataset Structure**
```
dataset/
│── images/
│   ├── train/
│   ├── val/
│   └── test/
│── labels/
│   ├── train/
│   ├── val/
│   └── test/
│── data.yaml
```

Update `data.yaml` paths before training.

 Training the Model
 
Run training with:
```bash
python train.py
```

Or directly with YOLOv8:
```bash
yolo task=detect mode=train model=yolov8n.pt data=data.yaml epochs=50 imgsz=640
```
 ## **Evaluation**
After training, evaluate the model:
```bash
yolo task=detect mode=val model=runs/detect/train/weights/best.pt data=data.yaml
```

This will generate:
- Confusion Matrix
- Precision, Recall, mAP metrics
- Validation results in `runs/detect/val/`
  




