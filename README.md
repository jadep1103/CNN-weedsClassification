# CNN Weeds Classification

Deep learning-based weed classification system using a custom Convolutional Neural Network (CNN) trained on the CottonWeedID15 dataset, capable of identifying 15 weed species for precision agriculture applications.

## 🌿 Overview

This project implements a computer vision solution for automated weed classification using a custom CNN architecture.  
It aims to support precision agriculture by enabling targeted herbicide application, reducing chemical usage, and improving crop management.

### Detected Weed Species
- **Carpetweeds**
- **Crabgrass**
- **Eclipta**
- **Goosegrass**
- **Morningglory**
- **Nutsedge**
- **PalmerAmaranth**
- **PricklySida**
- **Purslane**
- **Ragweed**
- **Slicklepod**
- **SpottedSpurge**
- **SpurredAnoda**
- **Swinecress**
- **Waterhemp**

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- TensorFlow 2.x
- CUDA-compatible GPU recommended

### Installation
```bash
# Clone repository
git clone <repository-url>
cd CNN-weedsClassification

# Create virtual environment
python -m venv myenv
source myenv/bin/activate  # On Windows: myenv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Dataset

Dataset is available from this drive: 


## 🔧 Training

### Train the CNN Model
```bash
# Open the training notebook
jupyter notebook algo_cnn.ipynb
```
Training uses:
- **Batch size**: 64  
- **Image size**: 200×200  
- **Optimizer**: Adam  
- **Loss**: SparseCategoricalCrossentropy  
- **Epochs**: 10

The model is saved as `.h5` after training.

## 📈 Results

Based on the final training:
- **Accuracy**: ~97% on validation set  
- **Loss**: Smooth convergence over 10 epochs  
- **Dataset augmentation** increased image count from **5,187** to **16,426** through:
  - Internet-sourced images
  - Random rotations
  - Scaling
  - Color adjustments

### Training Curves
- Accuracy increases steadily with epochs  
- Loss decreases consistently without overfitting

## ⚙️ Model Architecture
```
Input: 200x200 RGB
Rescaling (1./255)
Conv2D(128, kernel=3) + ReLU + MaxPooling
Conv2D(64, kernel=3)  + ReLU + MaxPooling
Conv2D(32, kernel=3)  + ReLU + MaxPooling
Conv2D(16, kernel=3)  + ReLU + MaxPooling
Flatten
Dense(64) + ReLU
Dense(15) + Softmax
```

## Possible Applications
- **Precision Agriculture**: Automated weed mapping
- **Field Monitoring**: Weed density assessment
- **Drone Integration**: Aerial crop surveillance
- **Research**: Weed species recognition studies

## 📊 Evaluation
Evaluation is done in `algo_cnn_eval.ipynb`, which includes:
- Confusion matrix generation
- Class-wise accuracy analysis
- Example predictions on reference images

## 🛠 Difficulties & Improvements
- **Challenges**:
  - Limited dataset size → risk of overfitting
  - Similar appearance between certain weed species
- **Solutions**:
  - Extensive data augmentation
  - Hyperparameter tuning
- **Future Improvements**:
  - Test with deeper CNN architectures
  - Experiment with transfer learning (e.g., ResNet, EfficientNet)
  - Merge datasets for broader coverage

## 📁 Project Structure
```
CNN-weedsClassification/
├── algo_cnn.ipynb         # Training pipeline
├── algo_cnn_eval.ipynb    # Evaluation and inference
├── datasets/              # Dataset location
├── Ref_Images/            # Reference samples
└── requirements.txt       # Dependencies
```
