# SPML - Security and Privacy in Machine Learning

This repository contains implementations of various adversarial attacks on machine learning models, focusing on CIFAR-100 image classification. The project explores different attack strategies to understand model vulnerabilities and improve robustness.

## Repository Structure

### [target_attack/](target_attack/)
Implementation of **targeted adversarial attacks** that force models to misclassify images to a specific target class.

- **Attack Method**: DIFGSM (Diverse Input Fast Gradient Sign Method)
- **Key Feature**: Uses ensemble of models for improved black-box transferability
- **Goal**: Generate adversarial examples that are misclassified as a specific target class

[→ Read more about Target Attack](target_attack/README.md)

### [universal_attack/](universal_attack/)
Implementation of **universal adversarial perturbation attacks** that create a single perturbation pattern effective across multiple images.

- **Attack Method**: Universal Perturbation
- **Key Feature**: Image-agnostic perturbation that works on multiple samples
- **Goal**: Find a single perturbation that reduces model accuracy across an entire dataset

[→ Read more about Universal Attack](universal_attack/README.md)

### [greybox_attacks/](greybox_attacks/)
Implementation of **greybox attacks** where the attacker has partial knowledge of the model (output only, no architecture/parameters).

- **Attack Method**: Query-based attacks with model outputs
- **Key Feature**: Adversarial training implementation included
- **Goal**: Generate adversarial examples and train robust models

[→ Read more about Greybox Attack](greybox_attacks/README.md)

## Common Requirements

All attack implementations use the following core dependencies:

- **PyTorch**: Deep learning framework
- **torchattacks**: Library for adversarial attacks
- **pytorchcv**: Pre-trained CIFAR models
- **torchvision**: Image processing utilities
- **numpy**: Numerical computing
- **tqdm**: Progress bars
- **pillow**: Image I/O

See individual `requirements.txt` files in each directory for specific versions.

## Dataset

All attacks are evaluated on CIFAR-100, a dataset consisting of:
- 100 classes of images
- 32x32 pixel RGB images
- 500 evaluation images provided in `cifar-100_eval.zip`

## Attack Constraints

All attacks maintain imperceptibility constraints:
- **L∞ norm**: ≤ 8/255 (pixel values in 0-1 range after normalization)
- This ensures perturbations are not easily visible to human observers

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/walkerhsu/SPML.git
   cd SPML
   ```

2. Choose an attack type and navigate to its directory:
   ```bash
   cd target_attack/  # or universal_attack/ or greybox_attacks/
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the Jupyter notebook for the chosen attack:
   ```bash
   jupyter notebook
   ```

## Pre-trained Models

All attacks use pre-trained models from the [pytorchcv model zoo](https://github.com/osmr/imgclsmob/blob/master/pytorch/pytorchcv/model_provider.py). Models with `_cifar100` suffix are used for CIFAR-100 attacks.

Example models include:
- ResNet variants (ResNet-20, ResNet-110, ResNet-164-BN)
- PreResNet variants
- SEResNet variants
- DenseNet variants
- DIA-ResNet variants

## Key Concepts

### Targeted Attack
Forces the model to classify an input as a specific target class chosen by the attacker.

### Universal Perturbation
A single perturbation pattern that can be added to many different images to cause misclassification.

### Greybox Attack
The attacker can query the model and observe outputs but does not have access to model architecture or parameters.

### Ensemble Attack
Uses multiple models simultaneously to generate adversarial examples with better transferability across different architectures.

## Contributing

This repository is part of a machine learning security course project. Each attack implementation includes:
- Jupyter notebooks with detailed explanations
- Visualization of attack results
- Configuration files with attack parameters

## References

- [pytorchcv Models](https://github.com/osmr/imgclsmob/blob/master/pytorch/pytorchcv/model_provider.py)
- [torchattacks Library](https://github.com/Harry24k/adversarial-attacks-pytorch)
- CIFAR-100 Dataset

## License

Please refer to individual files and notebooks for specific licensing information.
