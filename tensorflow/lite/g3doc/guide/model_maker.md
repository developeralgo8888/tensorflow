# TensorFlow Lite Model Maker

## Overview

The TensorFlow Lite Model Maker library simplifies the process of training a
TensorFlow Lite model using custom dataset. It uses transfer learning to reduce
the amount of training data required and shorten the training time.

## Supported Tasks

The Model Maker library currently supports the following ML tasks. Click the
links below for guides on how to train the model.

Supported Tasks                                                                                                                            | Task Utility
------------------------------------------------------------------------------------------------------------------------------------------ | ------------
Image Classification [guide](https://www.tensorflow.org/lite/tutorials/model_maker_image_classification)                                   | Classify images into predefined categories.
Text Classification [guide](https://www.tensorflow.org/lite/tutorials/model_maker_text_classification)                                     | Classify text into predefined categories.
BERT Question Answer [guide](https://www.tensorflow.org/lite/tutorials/model_maker_question_answer)                                        | Find the answer in a certain context for a given question with BERT.
Recommendation [demo](https://github.com/tensorflow/examples/blob/master/tensorflow_examples/lite/model_maker/demo/recommendation_demo.py) | Recommend items based on the context information for on-device scenario.

## End-to-End Example

Model Maker allows you to train a TensorFlow Lite model using custom datasets in
just a few lines of code. For example, here are the steps to train an image
classification model.

```python
from tflite_model_maker import image_classifier
from tflite_model_maker.image_classifier import DataLoader

# Load input data specific to an on-device ML app.
data = DataLoader.from_folder('flower_photos/')
train_data, test_data = data.split(0.9)

# Customize the TensorFlow model.
model = image_classifier.create(train_data)

# Evaluate the model.
loss, accuracy = model.evaluate(test_data)

# Export to Tensorflow Lite model and label file in `export_dir`.
model.export(export_dir='/tmp/')
```

For more details, see the
[image classification guide](https://www.tensorflow.org/lite/tutorials/model_maker_image_classification).

## Installation

There are two ways to install Model Maker.

*   Install a prebuilt pip package.

```shell
pip install tflite-model-maker
```

If you want to install nightly version, please follow the command:

```shell
pip install tflite-model-maker-nightly
```

*   Clone the source code from GitHub and install.

```shell
git clone https://github.com/tensorflow/examples
cd examples/tensorflow_examples/lite/model_maker/pip_package
pip install -e .
```

## Python API Reference

You can find out Model Maker's public APIs in
[API reference](https://www.tensorflow.org/lite/api_docs/python/tflite_model_maker).
