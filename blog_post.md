<!-- omit in toc -->
# Reproduction of GenISP: Generalizing Image Signal Processing for Low-Light Object Detection
<!-- omit in toc -->
### Janaína Moreira-Kanaley & Taichi Uno

<!-- omit in toc -->
## Table of Content
<!-- TOC -->
- [Introduction](#introduction)
- [Data](#data)
- [CycleGAN](#cyclegan)
- [Results](#results)
- [Conclusions](#conclusions)
- [References](#references)
- [Who did what](#who-did-what)
<!-- TOC -->

## Introduction
Image translation maps an input image to an output image and has image applications such as photo enhancement (low-quality to high-qualityimages), style transfer (e. g. photo to painting), and object transfiguration (e. g. zebra to horse). Typically, it is approached by relying on using aligned pairs of images to train the model[[1](#CNN_Segmentation)], where paired annotations can be costly to define and limit the options of data to train the model with. 

Our studied approach, Cycle-consistent Generative Adversarial Network (CycleGAN), can learn to translate images from source to target without paired examples and serves as a general-purpose solution to image translation tasks [[2](#CycleGAN)]. CycleGAN learns to convert unpaired images from one domain to another (and vice versa) by enforcing cycle consistency that ensures that generated images maintain content consistency with the original images. 

As our first task, to validate that the model works as intended, we attempt to reproduce and confirm the results from CycleGAN presented in [[2](#CycleGAN)]. To achieve the first task, the model will be retrained with the paired labels <-> photos Cityscapes dataset[^1] from [[3](#Cityscapes_Dataset)]. This dataset consists of urban street "photos" as one domain and a simplified annotated version of the scenes segmented by classes or "labels" (e.g road, building, person) as the other. While the model can handle unpaired images, quantitative evaluations are carried out using this paired labels <-> photos dataset to measure its accuracy in generating a realistic scene or assigning the correct labels to the segmented sections of the cityscapes. For evaluation, the Fully Convolutional Network (FCN) score from  [[3](#FCN_score)] will be calculated and compared to results in the paper [[2](#CycleGAN)]. The score measures the pixel-level agreement between the predicted image from CycleGAN and the ground truth image pair. 

As our second task, to ensure that training the model works with new unpaired datasets from different domains, we compile two datasets to use for an object transfiguration task. The two chosen datasets consist of images of pandas[^2] and brown bears[^3] respectively. The idea behind this transfiguration task is that images of pandas should be relatively easy to transfigure to brown bears (and vice versa) as they are animals from the same family. Since none of the images come with a domain complementary pair, quantitative measures of the output's quality in terms of accuracy cannot be calculated using previous methods (FCN score) based on ground truth image pairs. 

Results from performing the two tasks will help validating whether CycleGAN serves as a translation model that can be easily suited for different domains without the costs associated with pairing datasets.

[^1]: https://www.cityscapes-dataset.com/dataset
[^2]: https://images.cv/dataset/panda-image-classification-dataset
[^3]: https://images.cv/dataset/brown-bear-image-classification-dataset

## Data

## CycleGAN

## Results

## Conclusions

## References
<a id="CNN_Segmentation">[1]</a> J. Long, E. Shelhamer, and T. Darrell, “Fully convolutional networks for semantic segmentation,”CoRR, vol. abs/1411.4038, 2014. arXiv: 1411.4038. [Online]. Available: http://arxiv.org/abs/1411.4038.

<a id="CycleGAN">[2]</a> J. Zhu, T. Park, P. Isola, and A. A. Efros, “Unpaired image-to-image translation using cycle-consistent adversarial networks,” CoRR, vol. abs/1703.10593, 2017. arXiv: 1703.10593. [Online]. Available: http://arxiv.org/abs/1703.10593.

<a id="Cityscapes_Dataset">[3]</a> M. Cordts, M. Omran, S. Ramos, et al., “The cityscapes dataset for semantic urban scene understanding,” CoRR, vol. abs/1604.01685, 2016. arXiv: 1604.01685. [Online]. Available: http://arxiv.org/abs/1604.01685.

<a id="FCN_score">[4]</a> P. Isola, J. Zhu, T. Zhou, and A. A. Efros, “Image-to-image translation with conditional adversarial networks,” CoRR, vol. abs/1611.07004, 2016. arXiv: 1611 . 07004. [Online]. Available: http://arxiv.org/abs/1611.07004.

## Who did what
| Who | What|
| --- | --- |
| Janaína Moreira-Kanaley | Make the model working, training the model on cityscapes, modifitcation of the evaluation script, output evaluation, traing the model with new datasets, work on blogpost, work on the story line |
| Taichi Uno    | Make the model working, modifitcation of the evaluation script, work on blogpost, work on the story line |
