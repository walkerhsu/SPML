# Universal Attack

## Introduction

This directory contains the implementation of a **universal adversarial perturbation attack** on pre-trained CIFAR-100 models. Unlike targeted or untargeted attacks that generate image-specific perturbations, universal attacks create a single perturbation that can fool the model on multiple different images. All pre-trained models can be found in the [pytorchcv repository](https://github.com/osmr/imgclsmob/blob/master/pytorch/pytorchcv/model_provider.py).

## Structure

- `universal_attack.ipynb`: The main Jupyter notebook to generate universal adversarial perturbations. The model(s) to attack can be specified in this file.

- `requirements.txt`: The requirements file listing necessary packages.

- `cifar-100_eval/`: Directory containing the original 500 CIFAR-100 inference images.

- `universal.png`: Visualization of the universal perturbation pattern.

- `resnet20_universal.png`: Visualization of attack results on ResNet-20.

- `resnet110_universal.png`: Visualization of attack results on ResNet-110.

- `resnet164bn_universal.png`: Visualization of attack results on ResNet-164-BN.

## Attack Method

The universal attack generates a single perturbation pattern that can be added to any image to cause misclassification. Key characteristics:

- **Image-agnostic**: The same perturbation works across different images
- **Model-specific tuning**: Optimized for particular model architectures
- **Epsilon constraint**: Maintains imperceptibility (L∞ norm ≤ 8/255)

### Tested Models

The attack has been tested on the following CIFAR-100 models:
- `resnet20_cifar100`
- `resnet110_cifar100`
- `resnet164bn_cifar100`

## Usage

1. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run the universal attack notebook:
   ```bash
   jupyter notebook universal_attack.ipynb
   ```

3. The universal perturbation will be generated and visualizations will be saved as PNG files.

## Requirements

- torchattacks
- pytorchcv
- numpy
- torch
- torchvision
- tqdm
- pillow

## Results

The generated visualizations show:
- The universal perturbation pattern itself (`universal.png`)
- Examples of the attack applied to different models
- Accuracy degradation on each tested model architecture

## Notes

- Universal perturbations are particularly interesting because they reveal model-specific vulnerabilities
- The same perturbation can significantly reduce accuracy across an entire dataset
- These attacks are useful for understanding the decision boundaries learned by neural networks
