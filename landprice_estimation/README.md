# Training of land price estimation model

## Prepare data

### 1. Make directories

First of all, make a directory named `dataset` in the same directory where this README is located.

Then, make directories named `images` and `masked_images` in the `dataset` directory.

### 2. Collect satellite images and land prices

Collect satellite images of Japanese inhabited areas, each of which is associated with the land price of the area. **Images should be in PNG format.**

Save the satellite images in `./dataset/images`.

### 3. Make segmentation maps from the satellite images

Make segmentation maps using the notebook named `generate_segmap_with_segformer.ipynb`. This notebook will load SegFormer model we finetuned, and convert your satellite images into segmentation maps. Generated segmentation maps will be saved in `./dataset/masked_images`.

### 4. Make a data catalogue

Make a CSV file named `data_catalogue.csv`, each row of which is comprised of
- `img_filename`: file name of satellite image
- `mask_filename`: file name of segmentation map
- `landprice`: land price

This CSV will look like the following example:

|img_filename|mask_filename|landprice|
|:---:|:---:|:---:|
|satellite017532.png|satellite017532_masked.png|37800.0|
|satellite019827.png|satellite019827_masked.png|206000.0|
|satellite022953.png|satellite022953_masked.png|70900.0|
|satellite020755.png|satellite020755_masked.png|105000.0|
|satellite005165.png|satellite005165_masked.png|211000.0|

Finally, your `dataset` directory should look like the directory tree below:

```
.
└── dataset/
    ├── images/
    │   ├── satellite000000.png
    │   ├── satellite000001.png
    │   └── ...
    ├── masked_images/
    │   ├── satellite000000_masked.png
    │   ├── satellite000001_masked.png
    │   └── ...
    └── data_catalogue.csv
```

## Train our landprice estimator (LandNet) with your data

Open `train-landprice-estimator.ipynb`. This notebook will do the following:

1. Separate data in `data_catalogue.csv` into train, val, test subsets.
1. Define `Dataset` and `DataLoader`.
1. Define `LandNet`.
1. Train `LandNet`. At the end of every epoch, validation is conducted and its result will be written to a CSV file created at `./checkpoints/{datetime}/landnet_val_epochxx.csv`
1. Test `LandNet`. Test result will be written to a CSV file created at `./checkpoints/{datetime}/landnet_test.csv`

## Notes

According to our observations, the *logarithm* of land price seems to follow the normal distribution. So, we employed RMSLE (Rooted Mean Squared Logarithmic Error), which measures the disparity between the logarithms of prediction value and true value. However, this loss function is known to penalize much more when prediction value is smaller than true value, than the case where prediction value is greater than true value. This makes the model tend to predict higher price than true value. This behavior remains to be improved.