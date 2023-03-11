# Gun Detection
This repository contains the implementation of a gun detection algorithm using YOLOv7. The algorithm is trained on a custom dataset consisting of images and videos of people carrying guns. The model is designed to detect the presence of a gun in an image or video frame and output the coordinates of the bounding box around the detected object.

## Requirements
* Google Colab account
* GPU accelerator
* Access to Google Drive

## Installation

1. Clone the repository to you drive using the command
```bash
%cd /content/gdrive/MyDrive
!git clone https://github.com/WongKinYiu/yolov7
```

2. Download the pre-trained weights for YOLOv7 from the official repository: 
```bash
!wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7x.pt
!wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt
```

3.Install the required packages by running:
```bash
!pip install -r requirements.txt
```

## Usage

### Training

To use the gun detection algorithm, follow the steps below:

1. Create a folder named data in your working directory.

2. Inside data, create a folder named custom_data and put your images and labels in it.

3. Create a YAML file named custom_data.yaml inside data with the following format:
```python
train: path/to/train/images
val: path/to/validation/images

nc: 1
names: ['helmet']
```


4. Train the model using the following command:
```python
!python train.py --device 0 --batch-size 16 --epochs 100 --img 640 640 --data data/custom_data.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/yolov7-custom.yaml --weight yolov7.pt --name yolov7-custom
```

5. The detect function returns the bounding box coordinates of the detected object. You can then use these coordinates to draw a bounding box around the object:
```python
for box in boxes:
    x, y, w, h = box
    cv2.rectangle(image, (x, y), (x+w, y+h), (0, 0, 255), 2)
```
You can adjust the batch-size, epochs, and other parameters as needed.

### Detection
1. Put the images you want to detect in a folder named testSamples inside data.

2. Run the following command to detect helmets in the images:
```python
!python detect.py --weight /content/gdrive/MyDrive/VisionIsAllYouNeed/yolov7/runs/train/yolov7-custom/weights/best.pt --conf 0.4 --img-size 640 --source data/testSamples/

```

## Dataset
The dataset used to train the gun detection algorithm is not publicly available due to legal and ethical considerations.

## Acknowledgements
This implementation of the gun detection algorithm using YOLOv7 is based on the work of WongKinYiu, available at https://github.com/WongKinYiu/yolov7. The pre-trained weights used in this implementation are also from the same repository.

## License
This project is licensed under the MIT License.
