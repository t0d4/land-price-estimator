# Implementation of Segmentation models

## SegFormer

`train-segformer.ipynb` finetunes [SegFormer-B2](https://huggingface.co/nvidia/mit-b2), the encoder of which is pretrained with ImageNet, using [LoveDA](https://github.com/Junjue-Wang/LoveDA) dataset.
This notebook uses huggingface's 🤗transformers to conduct finetuning.
This notebook can run either on physical client or on Google Colaboratory.

## UNet

`UNet.ipynb` contains *from-scratch* implementation of [U-Net: Convolutional Networks for Biomedical Image Segmentation](https://arxiv.org/abs/1505.04597).