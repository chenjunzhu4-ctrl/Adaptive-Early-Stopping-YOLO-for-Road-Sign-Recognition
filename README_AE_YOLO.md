# AE-YOLO Experimental Code for Road Sign Recognition

AE-YOLO is an experimental project for **road sign recognition** with an **adaptive early-stopping training strategy**. This repository contains the notebook, experimental design, and supporting materials used to study the balance between **accuracy** and **efficiency** under different parameter settings.

## Introduction

Road sign recognition is an important task in autonomous driving and advanced driver-assistance systems. A practical model should not only recognize traffic signs accurately, but also maintain efficient training and inference under realistic road conditions.

This repository presents **AE-YOLO**, a road sign recognition method that combines a unified detection pipeline with an adaptive early-stopping strategy. The project focuses on two goals:

- improving the balance between **recognition accuracy** and **computational efficiency**
- validating robustness under more diverse road-sign conditions

The experiments are based on the **German Traffic Sign Recognition Benchmark (GTSRB)** dataset, which contains 43 traffic sign classes and substantial variation in scale, illumination, viewpoint, blur, and partial occlusion.

## Methodology

AE-YOLO follows three sequential steps:

### Step 1: Data Preparation and Preprocessing
We collect road sign images, annotate them with bounding boxes, convert them into the YOLO label format, and apply basic preprocessing such as resizing and augmentation. We then split the dataset into **training**, **validation**, and **test** subsets.

### Step 2: AE-YOLO Detection
AE-YOLO takes the processed road scene as input and performs road sign localization and classification through three components:

- **Backbone** for hierarchical feature extraction
- **Neck** for multi-scale feature fusion
- **Detection Head** for bounding-box and class prediction

This design allows the model to detect small and visually similar traffic signs under realistic road conditions.

### Step 3: Adaptive Early-Stopping Training
During training, AE-YOLO monitors validation performance and stops optimization when improvement becomes too small for a given patience window. This strategy reduces redundant epochs, saves training time, and keeps the best-performing model checkpoint.

## Experimental Factors

We use a **one-factor-at-a-time** strategy and vary only one factor in each experiment while keeping the others fixed. The current experiments study four factors:

1. **Filters**  
   Controls the number of convolution filters in the feature extraction stage.

2. **Kernel Size**  
   Controls the receptive field of the convolution operation.

3. **Dropout Rate**  
   Controls the strength of regularization during training.

4. **Pool Size**  
   Controls the downsampling scale in the pooling operation.

We evaluate these factors using two metrics:

- **Final Accuracy**
- **Training Time**

## Robustness Validation

In addition to the benchmark experiments, this project also includes a robustness validation setting using additional road sign images collected from online sources. The qualitative results show that AE-YOLO can still detect and label visible road signs in real-world scenes outside the benchmark dataset.

## Repository Structure

```text
.
├── traffic_sign_detection.ipynb
├── README.md
└── assets/                      # optional figures or screenshots
```

If you add more materials later, you can extend the structure with folders such as:

```text
├── models/
├── results/
├── figures/
└── technical_report/
```

## Dataset

This project uses the **GTSRB** dataset.

- Dataset name: **German Traffic Sign Recognition Benchmark (GTSRB)**
- Classes: **43**
- Source: Kaggle / benchmark site

Example dataset link:  
[GTSRB Dataset on Kaggle](https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign)

## Running the Notebook

1. Download the GTSRB dataset.
2. Place the dataset in the expected project directory.
3. Open `traffic_sign_detection.ipynb`.
4. Run the notebook cells in order:
   - data loading
   - preprocessing
   - model building
   - parameter experiments
   - result plotting
5. Save the generated tables and figures for the report.

## Main Findings

The current study shows that AE-YOLO improves the balance between **accuracy** and **efficiency** and maintains promising robustness under more diverse road-sign conditions. Across the reported factor groups, AE-YOLO improves final accuracy over the strongest baseline while preserving competitive training efficiency.

## Future Work

In future work, we will explore:

- a **stronger feature-extraction backbone** with better multi-scale representation and stronger small-object sensitivity
- a **more lightweight detection design** with faster inference, lower computational cost, and reduced parameter size

These directions may further improve recognition performance and generalization ability in complex real-world scenarios.

## Citation

If you use this repository, please cite the related paper or technical report.

```bibtex
@misc{zhu2026aeyolo,
  author = {Chenjun Zhu},
  title = {AE-YOLO: A Road Sign Recognition Method with Adaptive Early-Stopping Training},
  year = {2026},
  note = {Technical report and experimental code},
  url = {https://github.com/chenjunzhu4-ctrl/Adaptive-Early-Stopping-YOLO-for-Road-Sign-Recognition}
}
```

## Author

**Chenjun Zhu**  
GitHub: [chenjunzhu4-ctrl](https://github.com/chenjunzhu4-ctrl)

## References

1. Stallkamp, J., Schlipsing, M., Salmen, J., & Igel, C. (2012). *Man vs. computer: Benchmarking machine learning algorithms for traffic sign recognition*. Neural Networks, 32, 323-332.
2. Kaggle GTSRB dataset: https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign
3. GitHub repository: https://github.com/chenjunzhu4-ctrl/Adaptive-Early-Stopping-YOLO-for-Road-Sign-Recognition
