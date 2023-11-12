# python-yolo-training-with-jupyter-notebooks

## Table of Contents

+ [Summary](#summary)
+ [References](#references)
+ [How to use](#how-to-use)

## Summary

Repository demonstrating how to train a custom CNN model based on yolo-v4-tiny architecture. This can be utilized for image classification. image localization, image segmentation or object detection applications.

[![Open custom-yolov4-tiny-training.ipynb in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MGTheTrain/python-yolo-training-with-jupyter-notebooks/blob/main/notebooks/custom-yolov4-tiny-training.ipynb)

## References

- [Github repository of Techzizou - yolov4-tiny-custom_Training](https://github.com/techzizou/yolov4-tiny-custom_Training/tree/main)
- [Medium post by Techzizou - Train a custom yolov4 tiny object detector using google colab](https://medium.com/analytics-vidhya/train-a-custom-yolov4-tiny-object-detector-using-google-colab-b58be08c9593)
- [Jupyter notebook of Techzizou](https://colab.research.google.com/drive/1hQO4nOoD6RDxdbz3C1YSiifTsyZjZpYm?usp=sharing#scrollTo=afZcMjuiLEUi)
- [darknet](https://github.com/AlexeyAB/darknet)

## How to use

### Step 0 - Labeling images
Add your images (e.g. .JPG files) to the [img folder](data-custom/img) and label your images. For labeling images utilize for example one of the following:
- [labelimg](https://github.com/tzutalin/labelImg#labelimg)
- [Yolo_mark](https://github.com/AlexeyAB/Yolo_mark)
Update the [train.txt](data-custom/train.txt) to include all the `JPG` files to train with. Also update the [obj.names file](data-custom/obj.names) to list your classes.

### Step 1 - Updating the yolov4-tiny-custom.cfg file
 Adjust in the [yolov4-tiny-custom.cfg](data-custom/yolov4-tiny-custom.cfg) the `width`, `height`, `batch`, `subdivision`, `max_batches`, `steps`, `classes` and `filters` values. Refer to [section 3(a) Create and upload the labeled custom dataset “obj.zip” file to the “yolov4-tiny” folder on your drive here](https://medium.com/analytics-vidhya/train-a-custom-yolov4-tiny-object-detector-using-google-colab-b58be08c9593) or copy the original file which can be found here [yolov4-tiny-custom.cfg](https://github.com/AlexeyAB/darknet/blob/master/cfg/yolov4-tiny-custom.cfg) and replace [this yolov4-tiny-custom.cfg](data-custom/yolov4-tiny-custom.cfg).

### Setp 2 - Uploading the custom-data folder to Google Drive
Upload the [data-custom folder](data-custom) to [Google Drive](https://www.google.com/intl/de/drive/).

### Setp 3 - Running code blocks of the custom Jupyter notebook in Google Colab
Open [custom-yolov4-tiny-training.ipynb in Colab](https://colab.research.google.com/github/MGTheTrain/python-yolo-training-with-jupyter-notebooks/blob/main/notebooks/custom-yolov4-tiny-training.ipynb) and run each code block

### Step 4 - Utilize your trained weights in the sample object detector app

Execute the following steps in order to initialize the git submodule object detector app:

```sh
git submodule init --update
cp <your download folder path>/yolov4-tiny-custom_best.weights python-object-detection-with-yolo-and-opencv/weights
cp data-custom/yolov4-tiny-custom.cfg file python-object-detection-with-yolo-and-opencv/cfg
cp data-custom/obj.names file python-object-detection-with-yolo-and-opencv/object-names
```

Update the code in [object_detector_app.py](https://github.com/MGTheTrain/python-object-detection-with-yolo-and-opencv/tree/main/object_detector_app.py) to refer to the `yolov4-tiny-custom_best.weights`, `yolov4-tiny-custom.cfg` and `data-custom/obj.names`, e.g.

```python
...
object_names = "object-names/obj.names"
classes = []
with open(object_names, "r") as f:
    classes = f.read().strip().split("\n")

weights_file = "weights/yolov4-tiny-custom_best.weights"
cfg_file = "cfg/yolov4-tiny-custom.cfg"
net = cv2.dnn.readNet(weights_file, cfg_file)
layer_names = net.getLayerNames()

output_layers = ["yolo_30", "yolo_37"]  # yolov4-tiny
...
```

Navigate trough the steps [in python-object-detection-with-yolo-and-opencv](https://github.com/MGTheTrain/python-object-detection-with-yolo-and-opencv/tree/main/) in order to launch the object detector app.