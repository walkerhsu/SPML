# Target Attack

## Introduction

This directory contains the implementation of a **targeted adversarial attack** on pre-trained CIFAR-100 models. The goal is to generate adversarial examples that cause the model to misclassify images to a specific target class. All pre-trained models can be found in the [pytorchcv repository](https://github.com/osmr/imgclsmob/blob/master/pytorch/pytorchcv/model_provider.py).

## Structure

- `target_attack.ipynb`: The main Jupyter notebook to generate targeted adversarial examples. The model(s) to attack can be specified in this file.

- `ml2023-hw10.ipynb`: Reference implementation notebook from ML2023 homework 10, containing examples of FGSM attacks and ensemble methods.

- `requirements.txt`: The requirements file listing necessary packages.

- `cifar-100_eval/`: Directory containing the original 500 CIFAR-100 inference images.

- `adv_imgs/`: Directory where generated adversarial images are saved.

- `attack_info.txt`: Configuration information about the attack parameters used.

## Attack Method

The implementation uses **DIFGSM (Diverse Input Fast Gradient Sign Method)** attack with the following parameters:

- **Attack**: DIFGSM
- **Epsilon**: 0.01568627450980392 (equivalent to 8/255 for normalized images)
- **Decay**: 0.9
- **Steps**: 90
- **Model Type**: Ensemble of multiple models for better transferability

### Ensemble Models

The attack leverages an ensemble of the following CIFAR-100 models to improve black-box transferability:
- `resnet110_cifar100`
- `preresnet164bn_cifar100`
- `seresnet110_cifar100`
- `densenet40_k36_bc_cifar100`
- `diaresnet110_cifar100`

## Usage

1. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run the target attack notebook:
   ```bash
   jupyter notebook target_attack.ipynb
   ```

3. The generated adversarial images will be saved in the `adv_imgs/` directory.

## Requirements

- torchattacks
- pytorchcv
- numpy
- torch
- torchvision
- tqdm
- pillow

## Notes

- The epsilon constraint ensures that the perturbation is imperceptible to humans (L∞ norm ≤ 8/255).
- The target class is set to class 0 for all images in the default configuration.
- The attack uses an ensemble approach to improve transferability across different model architectures.
