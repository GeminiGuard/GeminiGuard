# GeminiGuard: Cooperative Defense against Adversarial Attacks

This is repository for paper GeminiGuard: Cooperative Defense against Adversarial Attacks

## Requirements
we mainly require the Python=3.6, keras=2.1.3, tensorflow-gpu=1.12.0, numpy, pandas, scikit-learn,cv2.
Detailed packages are shown in requirements.yaml

## Structure
The "json" directory contains the config files of all experiments.
The generated adversarial examples are saved in "adversarial" directory.
We save all the trained model in "model" directory.
The "data" directory is used for saving dataset.


## Quick Usage
We provide the weights of model.
You can follow the following steps to generate the adversarial examples and detect them.

### Download the Models Weights.
Download model weights from ???, and unzip them to the "model" directory.

### Get into the 'src' Directory.

``cd src``

### Generate Adversarial Examples on Unprotected Model.
Use ``scripts/attack_existing.py`` to generate the adversarial examples on unprotected model.

``python scripts/attack_existing.py -c svhn_res.json -a``

To change the attack methods, please modify the 'adversarial_type' item in json files. We support five attacks, and please use 'pgd', 'fgsm', 'CW', 'jsma', and 'deepfool' to set the item.

### Generate the Adversarial Examples on Enhanced Model.
Use ``scripts/attack_new.py`` to generate the adversarial examples on enhanced.

``python scripts/attack_existing.py -c svhn_concat_res.json -a``

The json files that contain "concat" means they are used for experiments of defending againist adversarial example generation.

### Defend against Attacks.
Use ``scripts/defend.py`` to defend against attacks.

``python scripts/defend.py -c svhn_res.json -t 0.05``

``python scripts/defend.py -c svhn_concat_res.json -t 0.05``

Above two command can be used to defend against existing adversarial examples and new adversarial examples.
Please generate the corresponding adversarial examples first.
The attack method can also be set by modifying 'adversarial_type' item in json file.

## Detailed Usage.
We provide the detail scripts to train the classifier and regulator.

