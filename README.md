## The source code for "Text-Enhanced Data-free Approach for Federated Class-Incremental Learning" accepted by CVPR 2024.
## Paper link: https://arxiv.org/abs/2403.14101

This repository contains modifications to the original LANDER code to address limitations related to communication overhead and training load.

### Original Code
The original implementation can be found [here](https://github.com/tmtuan1307/LANDER) .

### Objective
The primary limitation addressed in this work is the need to store and transfer a large amount of synthetic data from the server to the client, thereby increasing communication costs and the training load for the client. 

### Contributions
code changes are made in lander.py file in methods folder

1. Reducing Communication Overhead
#### Entropy-Based Image Selection:
- Calculated the entropy of each image by first computing the probabilities using the logits (output of ResNet).
- Stored the calculated entropies in dictionaries(for images and entropies separatel) where keys represent classes and values are tuples of images and their corresponding entropies.
- Selected and stored only half of the images with the lowest entropy, reducing the number of images sent to the client by half.
2. Adding Proximal Term in Loss Function
#### Proximal Term in Local Fine-Tune Method:
- Introduced a proximal term to penalize the difference between the current model parameters and the teacher model parameters.
- Updated the loss function to include the proximal term
3. Additional Methods in ImagePool Class
#### store_lowest_entropy_images:

- Deleted all previously stored synthesized images.
- Selected and stored only half of the images with the lowest entropy.
#### folder_size:

- Calculated the size of the folder containing the stored images.

### Usage
To use this modified implementation, clone the repository and follow the instructions in the original README.


This work builds upon the original LANDER implementation. I acknowledge the authors of the original paper and implementation for their contributions.

