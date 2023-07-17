# Development project of land price predictor

This is a research project in "Advanced Pattern Recognition" course at Waseda University.

## Overview

This system predicts land price from a satellite image. It works as follows:

1. Image Segmentation Model (SegFormer or Unet) converts a satellite image into a segmentation map, based on the usage of each area (e.g. Building, Road, Agriculture, ...etc)
1. LandNet Model (the architecture we devised) receives both RGB satellite image and segmentation map, and predicts the land price by utilizing them

PICTURE

## Try it now

LINK

## Links

- [Our HuggingFace Organization](https://huggingface.co/wu-pr-gw)
- [Our Final Presentation Slides](https://docs.google.com/presentation/d/1ES83LWEMLCCrgeAkCpD9SoQUxrxuLRViNE9mzScT_w4/edit?usp=sharing)