# Gun Detection
This repository contains the implementation of a gun detection algorithm using YOLOv7. The algorithm is trained on a custom dataset consisting of images and videos of people carrying guns. The model is designed to detect the presence of a gun in an image or video frame and output the coordinates of the bounding box around the detected object.

## Installation

1. Clone the repository using the command
```bash
git clone https://github.com/username/Gun-Detection.git
```

2. Install the required packages using
```bash
pip install -r requirements.txt
```

3. Download the pre-trained weights for YOLOv7 from the official repository: 
https://github.com/WongKinYiu/yolov7

## Usage
To use the gun detection algorithm, follow the steps below:

1. Import the necessary packages:
```python
import cv2
import numpy as np
from yolov7.detect import Detect
```

2. Initialize the Detect object:

```python
detect = Detect()
```

3. Load the input image or video frame:
```python
image = cv2.imread("image.jpg")
```

4. Detect the presence of a gun in the image or video frame:
```python
boxes = detect(image)
```

5. The detect function returns the bounding box coordinates of the detected object. You can then use these coordinates to draw a bounding box around the object:
```python
for box in boxes:
    x, y, w, h = box
    cv2.rectangle(image, (x, y), (x+w, y+h), (0, 0, 255), 2)
```

6. Display the output image:
```python
cv2.imshow("Output", image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## Dataset
The dataset used to train the gun detection algorithm is not publicly available due to legal and ethical considerations.

## Acknowledgements
This implementation of the gun detection algorithm using YOLOv7 is based on the work of WongKinYiu, available at https://github.com/WongKinYiu/yolov7. The pre-trained weights used in this implementation are also from the same repository.

## License
This project is licensed under the MIT License
