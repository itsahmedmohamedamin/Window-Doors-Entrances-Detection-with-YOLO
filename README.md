# Object Detection With YOLOv8

## This project provides a complete pipeline for training and running object detection models using YOLOv8, tailored for detecting windows and doors in images. It leverages datasets from Roboflow and Kaggle, and is designed to be run in a Google Colab environment.

# Features

* Download datasets from Kaggle and Roboflow
* Training a YOLOv8 model for window and door detection
* Detection with bounding boxes and class labels

# Prerequisites

* Google Colab account
* Kaggle API token
* Roboflow account with API key

# Installation

```
!pip install kaggle
!pip install ultralytics
!pip install roboflow
```

# Usage
## Setup

> First, upload your Kaggle API token as kaggle.json and adjust the paths and credentials accordingly in the script.

## Downloading the Dataset

> You can download datasets either from Kaggle or Roboflow:
```
# From Kaggle
download_from_kaggle('<dataset-name>', '/path/to/kaggle.json')

# From Roboflow
dataset = download_from_roboflow('workspace', 'project-name', version-number, 'your-roboflow-api-key')
```

## Model Training

> To train the model, specify the path to the dataset, batch size, number of epochs, and image size:

```
model = YOLO('yolov8m.yaml')
results = model.train(data='/content/data.yaml', batch=6, epochs=50, imgsz=640)
```

## Detection

> Load the trained model and perform detection on new images:

```
detector = YOLODetector('/path/to/best-model.pt', '/path/to/image.jpg')
result_image = detector.predict_and_detect()
detector.display_image(result_image)
```

## License

> This project is open-sourced under the MIT License.
