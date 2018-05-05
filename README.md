# Tensorflow Image Classifier

## Requirements
In order to run this program, you need Python 2.7. 
You also need to install the tensorflow module via pip. To do this type in the following command into your shell:
```
pip install tensorflow
```
## Overview
This image classifier works with categorized images of flowers (daisies, dandelions, roses, sunflowers, and tulips). The dataset is included within this repository. To classify an image, run the following code in your shell:
```
python -m scripts.label_image \
    --graph=tf_files/retrained_graph.pb  \
    --image=your/image/path.jpg
```
Where your/image/path is replaced by the path of the image. This will output the elapsed time in seconds, along with the categories and their corresponding confidence values, where the confidence values are percentages deeming the model's decision on the image. The categories are displayed in the order of their confidence. So, the first category in the list is the model's "decision"

You are welcome to replace the image set with a dataset of your choosing, so long as you follow the existing directory structure. To train the model, type in the following command into your shell:
```
IMAGE_SIZE=224
ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"
python -m scripts.retrain \
  --bottleneck_dir=tf_files/bottlenecks \
  --model_dir=tf_files/models/"${ARCHITECTURE}" \
  --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}" \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --architecture="${ARCHITECTURE}" \
  --image_dir=tf_files/your-image-directory/
```
Where 'your-image-directory' is replaced with the directory of photos located in 'tf_files'. Training the network will take 30 minutes to an hour, depending on the processing power of your machine. Once trained, follow the above steps to test images.

## From tensorflow-for-poets README
This repo contains code for the "TensorFlow for poets 2" series of codelabs.

There are multiple versions of this codelab depending on which version 
of the tensorflow libraries you plan on using:

* For [TensorFlow Lite](https://www.tensorflow.org/mobile/tflite/) the new, ground up rewrite targeted at mobile devices
  use [this version of the codelab](https://codelabs.developers.google.com/codelabs/tensorflow-for-poets-2-tflite) 
* For the more mature [TensorFlow Mobile](https://www.tensorflow.org/mobile/mobile_intro) use 
  [this version of the codealab](https://codelabs.developers.google.com/codelabs/tensorflow-for-poets-2).


This repo contains simplified and trimmed down version of tensorflow's example image classification apps.

* The TensorFlow Lite version, in `android/tflite`, comes from [tensorflow/contrib/lite/](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/contrib/lite).
* The Tensorflow Mobile version, in `android/tfmobile`, comes from [tensorflow/examples/android/](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android).

The `scripts` directory contains helpers for the codelab. Some of these come from the main TensorFlow repository, and are included here so you can use them without also downloading the main TensorFlow repo (they are not part of the TensorFlow `pip` installation).

