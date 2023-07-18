# Development project of land price predictor

This is a research project in "Advanced Pattern Recognition" course at Waseda University.
Please have a look at our [presentation slides](https://docs.google.com/presentation/d/1ES83LWEMLCCrgeAkCpD9SoQUxrxuLRViNE9mzScT_w4/edit?usp=sharing) and [presentation video](https://drive.google.com/file/d/1qeR6TDPkrS0NyKKdIV0YCTqgOLFb2g3U/view?usp=sharing)
to know backgrounds, motivations, methods, results, discussions of this project.

**Try Demo In Colab Now**


[![Try Demo In Colab Now](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/t0d4/land-price-estimator/blob/main/try_landnet.ipynb)

## Overview

This system predicts land price from a satellite image. It works as follows:

1. Image Segmentation Model (SegFormer or Unet) converts a satellite image into a segmentation map, based on the usage of each area (e.g. Building, Road, Agriculture, ...etc)
1. LandNet Model (the architecture we devised) receives both RGB satellite image and segmentation map, and predicts the land price by utilizing them

<img src="https://github.com/t0d4/land-price-estimator/assets/37496476/0961eb4a-5994-419c-90ca-56a8fab36295" height=60% width=60%>

## LandNet

LandNet, which we devised, is a model that can effectively processes both RGB satellite images and multi-channel segmentation maps.
The architecture of LandNet is described in the figure below:

<img src="https://github.com/t0d4/land-price-estimator/assets/37496476/d20ea943-4053-4717-a97c-f9508df13115" height=70% width=70%>

## Links

- [Our HuggingFace Organization](https://huggingface.co/wu-pr-gw)
- [Our Final Presentation Slides](https://docs.google.com/presentation/d/1ES83LWEMLCCrgeAkCpD9SoQUxrxuLRViNE9mzScT_w4/edit?usp=sharing)
- [Our Final Presentation Video](https://drive.google.com/file/d/1qeR6TDPkrS0NyKKdIV0YCTqgOLFb2g3U/view?usp=sharing)
