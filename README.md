# python-yolo-training-with-jupyter-notebooks

## Table of Contents

+ [Summary](#summary)
+ [References](#references)
+ [How to use](#how-to-use)

## Summary

Repository demonstrating how to train a custom CNN model based on yolo-v4-tiny architecture. This can be utilized for image classification. image localization, image segmentation or object detection tasks.

## References

- [Train a custom yolov4 tiny object detector using google colab](https://medium.com/analytics-vidhya/train-a-custom-yolov4-tiny-object-detector-using-google-colab-b58be08c9593)

## How to use

0. Add your images (e.g. .JPG files) to the [img folder](data-custom\img) and label your images. For labeling images utilize for example one of the following:
- [labelimg](https://github.com/tzutalin/labelImg#labelimg)
- [Yolo_mark](https://github.com/AlexeyAB/Yolo_mark)

1. Adjust in the [yolov4-tiny-custom.cfg](data-custom\yolov4-tiny-custom.cfg) the `width`, `height`, `batch`, `subdivision`, `max_batches` and `steps` values. Refer to [section 3(a) Create and upload the labeled custom dataset “obj.zip” file to the “yolov4-tiny” folder on your drive here](https://medium.com/analytics-vidhya/train-a-custom-yolov4-tiny-object-detector-using-google-colab-b58be08c9593)