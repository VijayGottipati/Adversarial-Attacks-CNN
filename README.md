# Adversarial-Attacks-CNN

This repository contains the implementation of adversarial attacks on deep neural networks for image classification, specifically targeting ResNet-34 and evaluating transferability to DenseNet-121.

## 📋 Project Overview

This project implements and evaluates three different adversarial attack methods:
- **FGSM (Fast Gradient Sign Method)**: Single-step gradient-based attack
- **PGD (Projected Gradient Descent)**: Multi-step iterative attack
- **Patch Attack**: Localized adversarial perturbations on image patches

The attacks are tested on ImageNet-style datasets using pre-trained models to demonstrate the vulnerability of deep learning models to adversarial examples.

## 🎯 Objectives

1. Implement three different adversarial attack algorithms
2. Evaluate attack effectiveness on ResNet-34
3. Test transferability of adversarial examples to DenseNet-121
4. Analyze perturbation constraints and model robustness
5. Generate adversarial datasets for further research

## 🛠️ Technical Implementation

### Attack Methods

#### 1. FGSM Attack
- **Epsilon (L∞)**: 0.02 (normalized)
- Single-step gradient ascent
- Fast but less effective than iterative methods

#### 2. PGD Attack
- **Epsilon (L∞)**: 0.02 (normalized)
- **Steps**: 10 iterations
- **Step Size**: 0.002
- More effective iterative refinement of FGSM

#### 3. Patch Attack
- **Epsilon**: 0.3 (normalized)
- **Patch Size**: 32×32 pixels
- **Steps**: 10 iterations
- Localized perturbations on random image patches

### Models Evaluated
- **Primary Target**: ResNet-34 (ImageNet pre-trained)
- **Transfer Target**: DenseNet-121 (ImageNet pre-trained)

## 📊 Key Results

### Attack Effectiveness (ResNet-34)
- **Baseline Accuracy**: ~70% Top-1, ~93% Top-5
- **FGSM Attack**: Significant accuracy drop
- **PGD Attack**: More effective than FGSM
- **Patch Attack**: Localized but effective perturbations

### Transferability Analysis
- Adversarial examples generated for ResNet-34 tested on DenseNet-121
- Demonstrates cross-model vulnerability
- Important for understanding real-world attack scenarios

## 🔧 Requirements

```python
torch>=1.9.0
torchvision>=0.10.0
numpy
matplotlib
PIL
json
```

## 📁 Project Structure

```
DeepLearning-FinalProject/
├── dl-final.ipynb          # Main implementation notebook
├── README.md               # This file
└── TestDataSet/            # Dataset directory (when available)
    ├── labels_list.json    # ImageNet class labels
    └── [class_folders]/    # Image data organized by class
```

## 🚀 Usage

### Running the Notebook

1. **Setup Environment**:
   ```bash
   pip install torch torchvision numpy matplotlib pillow
   ```

2. **Prepare Dataset**:
   - Place your test dataset in `TestDataSet/` directory
   - Ensure `labels_list.json` contains class mappings
   - Organize images in class-specific subdirectories

3. **Execute Attacks**:
   ```python
   # The notebook automatically:
   # 1. Loads pre-trained models
   # 2. Applies all three attack methods
   # 3. Evaluates model performance
   # 4. Generates adversarial datasets
   # 5. Tests transferability
   ```

### Configuration Parameters

```python
EPSILON_LINF = 0.02      # L∞ constraint for FGSM/PGD
EPSILON_PATCH = 0.3      # Patch attack constraint
PATCH_SIZE = 32          # Patch dimensions
PGD_STEPS = 10           # PGD iterations
```

## 📈 Output Analysis

The implementation provides:

1. **Accuracy Metrics**: Top-1 and Top-5 accuracy for all attack scenarios
2. **Perturbation Analysis**: L∞ norm verification for constraint compliance
3. **Visualizations**: Side-by-side comparison of original vs adversarial images
4. **Adversarial Datasets**: Generated datasets saved for future use
5. **Transferability Results**: Cross-model attack success rates

## 🔍 Key Features

- **GPU Acceleration**: Automatic CUDA detection and utilization
- **Batch Processing**: Efficient batch-wise attack generation
- **Constraint Verification**: Automatic perturbation bound checking
- **Comprehensive Evaluation**: Multiple metrics and visualizations
- **Dataset Generation**: Saves adversarial examples for reuse

## 📚 Research Applications

This implementation is suitable for:
- Adversarial robustness research
- Defense mechanism development
- Model vulnerability assessment
- Educational purposes in adversarial ML

## ⚠️ Ethical Considerations

This code is intended for:
- ✅ Academic research and education
- ✅ Improving model robustness
- ✅ Understanding ML security

**Not intended for**:
- ❌ Malicious attacks on production systems
- ❌ Unauthorized model manipulation

## 🤝 Contributing

Feel free to contribute by:
- Adding new attack methods
- Improving evaluation metrics
- Enhancing visualization capabilities
- Optimizing performance

## 📄 License

This project is for educational and research purposes. Please ensure responsible use and cite appropriately in academic work.

## 📞 Contact

For questions or collaboration opportunities, please reach out through the repository's issue tracker.

---

*This project demonstrates the importance of adversarial robustness in deep learning and provides a foundation for further research in this critical area of AI security.*
