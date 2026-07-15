Piano Triad Recognizer

This is an AI that when you test a file of a hand playing one triad it can detect which triad it is.

## Features

* Classifies piano triads from images
* Uses a custom-trained ResNet-18 ONNX model
* Built with the NVIDIA Jetson Inference framework
* Includes a custom dataset and label file

## Prerequisites

Before running this project, install and build the NVIDIA Jetson Inference framework on your Jetson device.

You'll also need:

* NVIDIA Jetson device
* Python 3
* Jetson Inference
* A trained `resnet18.onnx` model
* `labels.txt`

## Project Structure

```text
Piano-Triad-Recognizer/
├── data/
│   └── piano/
│       ├── train/
│       ├── val/
│       ├── test/
│       └── labels.txt
├── models/
│   └── resnet18.onnx
├── README.md
```

## Getting Started

1. Clone this repository:

```bash
git clone https://github.com/ravenmoon903/Piano-Triad-Recognizer.git
```

2. Change into the project directory:

```bash
cd Piano-Triad-Recognizer
```

3. Ensure Jetson Inference is installed and built on your Jetson device.

4. Place the trained model (`resnet18.onnx`) in the `models/` directory if it is not already included.

## Running the Classifier

Example command:

```bash
imagenet.py \
  --model=models/resnet18.onnx \
  --labels=data/piano/labels.txt \
  --input_blob=input_0 \
  --output_blob=output_0 \
  data/piano/test/d_maj/dmaj.JPEG \
  pianooutput.jpg
```

Change the d_maj and dmaj.JPEG to desired chord and image respectfully in order to test it.
The output image (`pianooutput.jpg`) will contain the predicted piano triad. The terminal will also have a prediction in it.

## Dataset

The dataset is organized into:

* `train/` – images used to train the model
* `val/` – validation images used during training
* `test/` – images used to evaluate the model

Each class has its own folder (for example, `d_maj`, `c_maj`, etc.).

## Acknowledgements

This project was created using NVIDIA's Jetson Inference image classification workflow with a custom piano triad dataset for a class.
