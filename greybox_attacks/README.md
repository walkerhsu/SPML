## Homework1 - Graybox Attack

### 1. Introduction

In this homework, I implement a graybox attack on pre-trained model(s). All pre-trained models can be found in [this pytorchcv repo](https://github.com/osmr/imgclsmob/blob/master/pytorch/pytorchcv/model_provider.py). The goal of the attack is to generate adversarial examples that can fool the model(s). The attack is a graybox attack, which means that we can only access the output of the model and cannot access the model's architecture and parameters.

### 2. Structure

- `graybox_attack.ipynb`: The main python notebook file to generate adversarial examples. The model(s) to attack can be specified in this file.

- `adversarial_training.ipynb`: The main python notebook file to train the model(s) adversarially. The model(s) to train and the adversarial_examples to use can be specified in this file.

- `requirements.txt`: The requirements file to install the necessary packages.

- `cifar-100_eval.zip`: The zip file for the original 500 CIFAR100 inference images.

- `report/`: The report files to introduce the homework (written in LaTeX).

- `README.md`: The readme file to introduce the homework.

### 3. Usage

To generate the adversarial examples, please run the graybox_attack.ipynb file. 

To train the model(s) adversarially, please run the adversarial_training.ipynb file. The model(s) to attack and adversarially-train can be specified in the corresponding files.