# python-yolo-training-with-jupyter-notebooks

## Table of Contents

+ [Summary](#summary)
+ [References](#references)
+ [How to use](#how-to-use)

## Summary

Repository demonstrating how to train a custom CNN model based on yolo-v4-tiny architecture. This can be utilized for image classification. image localization, image segmentation or object detection tasks.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MGTheTrain/python-yolo-training-with-jupyter-notebooks/blob/main/notebooks/notebooks/custom-yolov4-tiny-training.ipynb)

## References

- [Train a custom yolov4 tiny object detector using google colab](https://medium.com/analytics-vidhya/train-a-custom-yolov4-tiny-object-detector-using-google-colab-b58be08c9593)
- [darknet](https://github.com/AlexeyAB/darknet)

## How to use

0. Add your images (e.g. .JPG files) to the [img folder](data-custom/img) and label your images. For labeling images utilize for example one of the following:
- [labelimg](https://github.com/tzutalin/labelImg#labelimg)
- [Yolo_mark](https://github.com/AlexeyAB/Yolo_mark)

1. Adjust in the [yolov4-tiny-custom.cfg](data-custom/yolov4-tiny-custom.cfg) the `width`, `height`, `batch`, `subdivision`, `max_batches`, `steps`, `classes` and `filters` values. Refer to [section 3(a) Create and upload the labeled custom dataset “obj.zip” file to the “yolov4-tiny” folder on your drive here](https://medium.com/analytics-vidhya/train-a-custom-yolov4-tiny-object-detector-using-google-colab-b58be08c9593) or copy the original file which can be found here [yolov4-tiny-custom.cfg](https://github.com/AlexeyAB/darknet/blob/master/cfg/yolov4-tiny-custom.cfg) and replace [this yolov4-tiny-custom.cfg](data-custom/yolov4-tiny-custom.cfg).

2. Run steps in the [custom-yolov4-tiny-training Jupyter Notebook](notebooks/custom-yolov4-tiny-training.ipynb) 