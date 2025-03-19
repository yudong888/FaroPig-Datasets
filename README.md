# FaroPigSeg & FaroPigReID-33: Datasets for Pig Segmentation and Reidentification

FaroPigSeg & FaroPigReID-33 are public datasets for pig segmentation and reidentification introduced in the paper [Housed Pig Identification and Tracking for Precision Livestock Farming](https://web.ub.edu/en/home). Both datasets are fully uploaded to our server, and here on GitHub we only keep several sample for demonstrating the dataset structure. For full datasets, please click [FaroPigSeg (150MB)](https://data.chalearnlap.cvc.uab.cat/FaroPig/FaroPigSeg.zip) and [FaroPigReID-33 (12GB)](https://data.chalearnlap.cvc.uab.cat/FaroPig/FaroPigReId.zip). 

**Note**: Our datasets are to be used for research purposes only, and any commercial use is strictly prohibited. If you find our datasets useful, please cite our article with the citation below.

The datasets were created with the support of the University of Barcelona and AGCO Corporation, and all the images were collected in a commercial pig finishing farm. The right to collect data and make datasets public has been granted by the company and the farmers.

## FaroPigSeg

The dataset FaroPigSeg is created for the instance segmentation task introduced in the paper. It contains 1518 annotated pig images, and more than 16,000 pig instances were labeled in total. The images were collected from different pens of the farm, and the labels are in the YOLO format.

![FaroPigSeg Image Samples](FaroPigSeg/SegSamples.png)

### Dataset Structure

All images and their corresponding annotations are randomly divided into three folders according to a certain ratio: train, val, and test.

```plaintext
FaroPigSeg
├── train/
│   ├── images/
│   └── labels/
├── val/
│   ├── images/
│   └── labels/
├── test/
│   ├── images/
│   └── labels/
└── data.yaml
```

- **train**: Contains 70% of all the images and corresponding labels.
- **val**: Contains 20% of all the images and corresponding labels.
- **test**: Contains 10% of all the images and corresponding labels.
- **data.yaml**: List of classes and configuration of the paths for training.

### Annotation Format (YOLO Segmentation)

Each annotation file, found within the `labels` folders, corresponds to an image file (same name, `.txt` extension).

Format:
\<class_id\> \<x1\> \<y1\> \<x2\> \<y2\> ... \<xn\> \<yn\>

- **\<class_id\>**: Integer representing the class index (always 0 as we only have one class).
- **\<x, y\> pairs**: Normalized (0 to 1) polygon coordinates outlining the object.

### Download

[FaroPigSeg Dataset](https://data.chalearnlap.cvc.uab.cat/FaroPig/FaroPigSeg.zip) (150MB)

## FaroPigReID-33

The dataset FaroPigReID-33 is created for the pig reidentification task introduced in the paper. It is taken from three video clips with around 1620, 16200, and 2700 frames respectively, and it has 33 valid identities in total. The process of creating the dataset is semi-automatic by combining SAM with the point tracker Co-tracker, and then a filtering procedure was conducted to remove the individuals with low diversity and richness. 
![FaroPigReID Image Samples](FaroPigReID-33/ReIDSamples.png)

At last, we capped the dataset with 4000 frames per individual by uniformly selecting the frames of every individual in the temporal axis. The final dataset contains 33 identities, with around 300 to 4,000 masks per individual, as shown in the following figure.

![Bar Chart](FaroPigReID-33/dataset_4000.png)

### Dataset Structure

The final dataset consists of frames taken from video clips, annotation, and cropped images of every identity and its corresponding masks.

```plaintext
FaroPigReID-33
├── Galleries/
│   ├── 2023-09-28T15_59_48Z-left_2160_9720/
│   │   ├── Images/
│   │   │   ├── A/
│   │   │   ├── B/
│   │   │   │   ...
│   │   │   └── I/
│   │   └── Masks/
│   │       ├── A/
│   │       ├── B/
│   │       │   ...
│   │       └── I/
│   ├── 2024-01-05T09_43_39Z-left_14700_29369/
│   └── 2024-02-27T14_54_53Z-left_15660_27000/
├── Frames/
│   ├── 2023-09-28T15_59_48Z-left_2160_9720/
│   ├── 2024-01-05T09_43_39Z-left_14700_29369/
│   └── 2024-02-27T14_54_53Z-left_15660_27000/
├── dataset_im_filtered_ssl.csv
└── dataset_im_filtered_ssl_10folds_allbase.csv
```

- **Galleries**: Directory of the images cropped according to the bounding boxes of the individuals and its corresponding masks. Inside the images and masks folder, all the images and masks are categorized according to identity label.
- **Frames**: The original images extracted from the videos.
- **dataset_im_filtered_ssl.csv**: The collection of all the annotations.
- **dataset_im_filtered_ssl_10folds_allbase.csv**: The collection of all the annotations with 10-folds study that conducted in the paper.

The elements from the Galleries and Frames directories are distributed by video clips, using the `{year}-{month}-{day}T{hour}_{minute}_{second}Z-{camera}_{start_frame}_{end_frame}/` notation.

### Annotation Format

All the annotations have been saved in `dataset_im_filtered_ssl.csv`.

Format:
\<path\> \<label\> \<width\> \<height\> \<xmin\> \<xmax\> \<ymin\> \<ymax\> \<valid\> \<main_path\>

- **\<path\>**: The image path corresponding to the annotation.
- **\<label\>**: The identity label of the individual.
- **\<width\> \<height\>**: Dimension of the bounding box of the individual.
- **\<xmin\> \<xmax\> \<ymin\> \<ymax\>**: Bounding box location of the individual in the frame.
- **\<valid\>**: Validity of the annotation (1.0=valid, 0.0=invalid). It indicates a human-based annotation selection according to the visibility of the pig, the quality of the annotation and its size.
- **\<main_path\>**: The frame path corresponding to the annotation.

In addition, for `dataset_im_filtered_ssl_10folds_allbase.csv`
- **\<folds\>**: The fold in which the image is assigned. As we performed a 10-fold cross-validation, the fold assigned refers to the fold where the image belongs to the test set.
- **\<split_x\>**: Assignement of the image per each fold configuration (train, val, test). "x" stands for the fold configuration name. 

**Note**: In the \<path\> column, we only listed the path of the images. If you need the path of the masks, please change "Images" to "Masks".

**Example**:
- `"Images/D/id_D_frame_00002160_img.png"` is the image path of the identity D, and Its corresponding mask path is `"Masks/D/id_D_frame_00002160_img.png"`.

### Download

[FaroPigReID-33 Dataset](https://data.chalearnlap.cvc.uab.cat/FaroPig/FaroPigReId.zip) (12GB)

## License

Both datasets FaroPigSeg and FaroPigReID-33 are licensed under the Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0).

You are free to use, share, and modify the datasets for non-commercial purposes only.

Full license details: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

## Citation

To be added after publishing.

```plaintext
@article{Compte:ESA:2015,
author={Albert Compte and Yudong Yan and Xavier Cortés and Sergio Escalera and Julio C. S.
Jacques-Junior},
journal={Expert Systems with Application},
title={Housed Pig Identification and Tracking for Precision Livestock
Farming},
year={2025},
volume={},
number={},
pages={},
doi={},
ISSN={}
}
```