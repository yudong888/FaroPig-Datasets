# FaroPigSeg: Dataset for Pig Segmentation

FaroPigSeg is public dataset for pig segmentation introduced in the paper [Housed Pig Identification and Tracking for Precision Livestock Farming](https://web.ub.edu/en/home). The datasets is fully uploaded to our server, and here on GitHub we only keep several sample for demonstrating the dataset structure. For full dataset, please click [FaroPigSeg (150MB)](https://data.chalearnlap.cvc.uab.cat/FaroPig/FaroPigSeg.zip).

**Note**: Our dataset is to be used for research purposes only, and any commercial use is strictly prohibited. If you find our dataset useful, please cite our article with the citation below.

The dataset was created with the support of the University of Barcelona and AGCO Corporation, and all the images were collected in a commercial pig finishing farm. The right to collect data and make datasets public has been granted by the company and the farmers.

## FaroPigSeg

The dataset FaroPigSeg is created for the instance segmentation task introduced in the paper. It contains 1518 annotated pig images, and more than 16,000 pig instances were labeled in total. The images were collected from different pens of the farm, and the labels are in the YOLO format.

![FaroPigSeg Image Samples](SegSamples.png)

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