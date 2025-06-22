# 🧠 YOLOv8 Object Detection on Custom Dataset

This repository demonstrates how to train, validate, and use a YOLOv8 object detection model using the [Ultralytics YOLOv8](https://docs.ultralytics.com/) framework on a custom dataset.

## 📁 Project Structure

```
yolov8-custom-object-detection/
├──train
├──valid
├── test
├── data.yaml
└── README.md
```

## 📦 Requirements

Install the Ultralytics package and other dependencies:

```bash
pip install ultralytics
```

(Optionally, create and activate a virtual environment):

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

## 📁 Dataset Format

- Your dataset should follow the YOLO format:
  - Each image must have a corresponding `.txt` file in the `labels/` folder.
  - Each line in the label file: `class_id x_center y_center width height` (normalized format).

- Create a `data.yaml` file like this:

```yaml
train: ./datasets/custom_dataset/images/train
val: ./datasets/custom_dataset/images/val

nc: 1  # Number of classes
names: ['small']
```

## 🏋️‍♂️ Training the Model

Run the training command:

```bash
yolo detect train \
    model=yolov8n.pt \
    data=data.yaml \
    epochs=100 \
    imgsz=640 \
    batch=16 \
    name=custom_yolov8
```

## ✅ Model Validation

After training, you can validate the model:

```bash
yolo detect val \
    model=runs/detect/custom_yolov8/weights/best.pt \
    data=data.yaml
```

## 🔍 Inference / Prediction

Run inference on new images or a folder of images:

```bash
yolo detect predict \
    model=runs/detect/custom_yolov8/weights/best.pt \
    source=path/to/image_or_folder \
    conf=0.25
```

## 📊 Results

- Training results are saved in the `runs/detect/custom_yolov8/` directory.
- Includes metrics (precision, recall, mAP), loss graphs, and prediction images.

## 🛠 Tips

- Resize images to a consistent size (e.g., 640x640).
- Ensure class balance for better accuracy.
- Always double-check annotations before training.

## 📚 References

- [Ultralytics YOLOv8 Documentation](https://docs.ultralytics.com/)
- [YOLOv8 GitHub Repository](https://github.com/ultralytics/ultralytics)

## ✍️ Author

**Muhammad Naeem Mumtaz**  
📧 [engrnaeem.9298@gmail.com](mailto:engrnaeem.9298@gmail.com)  
🔗 [LinkedIn](https://www.linkedin.com/in/muhammad-naeem-mumtaz-awan-59bab9202/)
