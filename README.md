# MST++ Implementation and Annotation for Plant Disease Detection

This repository contains an implementation of the **MST++ (Multi-stage Spectral-wise Transformer)** for spectral reconstruction, applied to a potato leaf disease dataset. The project pipeline includes training the spectral reconstruction model and a comprehensive inference workflow that annotates RGB images, converts them to Hyperspectral Images (HSI), and visualizes bounding box annotations on both modalities.

## 📌 Project Overview

The project is divided into two main modules:
1. **Training (`training/`)**: Trains the MST++ model to reconstruct hyperspectral information from RGB images using the ARAD-1K dataset.
2. **Annotation & Inference (`rgb_to_hsi/`)**: 
    * Annotates RGB potato leaf images to generate bounding box coordinates.
    * Converts RGB images to HSI using the trained MST++ model.
    * Visualizes the disease annotation on both the original RGB and the reconstructed HSI.

## 🛠️ Getting Started

### Prerequisites
* **Python 3.8** is strictly required.
* **Git**

### Installation

1. Clone the repository:
   ```
   git clone https://github.com/shaShvat07/mtp.git
   cd mtp
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

---

## 📂 Dataset Structure

Ensure your datasets are organized as follows before running the scripts. The project uses the **ARAD-1K** dataset for spectral training and the **New Plant Diseases Dataset (Potato)** from Kaggle for disease annotation.

```
├── mst_plus_plus
│   └── dataset
│       ├── split_txt
│       ├── Test_RGB
│       ├── Train_RGB
│       └── Train_Spec
│
└── potato-dataset
    ├── Potato___Early_blight
    ├── Potato___healthy
    └── Potato___Late_blight
```

---

## 🚀 Usage Guide

### 1. Training the Model

To train the MST++ spectral reconstruction model:

1. Navigate to the training directory:
   ```
   cd training
   ```
2. Open the Jupyter Notebook located in this folder.
3. Run **all cells** sequentially to start the training process.
4. Once training is complete, the best model checkpoint (`.pth` file) will be tell by the code, you need to copy it from the checkpoints.

### 2. Annotation and RGB-to-HSI Conversion

This module handles the annotation of disease spots, generation of coordinate labels, and spectral reconstruction.

**Preparation:**
1. Copy the **best model file** (`.pth`) generated from the training step.
2. Paste it into the `best_model/` directory inside `rgb_to_hsi`.

**Execution:**
1. Navigate to the directory:
   ```
   cd rgb_to_hsi
   ```
2. Run the main notebook:
   ```
   jupyter notebook index.ipynb
   ```
3. **Manual Input Required:** During execution, you will be prompted to enter:
   * The file path location of the input dataset.
   * The directory path where you want to store the output.

**What this script does:**
* **Annotates** the RGB image and generates bounding box coordinates.
* **Saves** these coordinates into a `.txt` file with corresponding labels.
* **Converts** the RGB image to an HSI image using the pre-trained MST++ model.
* **Visualizes** the bounding box annotations overlaid on both the original RGB image and the reconstructed HSI image.

---

## 📄 References & Citation

This project implements the **MST++** architecture. If you use this code or model, please credit the original paper:

**MST++: Multi-stage Spectral-wise Transformer for Efficient Spectral Reconstruction**  
*Yuanhao Cai, Jing Lin, Haoqian Wang, Qijing Li, Huaian Chen, Lei Zhang, Radu Timofte, Luc Van Gool*  
In *CVPR Workshops (CVPRW)*, 2022.

[[Paper Link]](https://openaccess.thecvf.com/content/CVPR2022W/NTIRE/papers/Cai_MST_Multi-Stage_Spectral-Wise_Transformer_for_Efficient_Spectral_Reconstruction_CVPRW_2022_paper.pdf)
