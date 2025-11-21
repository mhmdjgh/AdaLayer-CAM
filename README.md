# AdaLayer-CAM

This repository contains the official implementation of the paper:
"AdaLayer-CAM: Adaptive Multi-Layer Method for Visualization and Explanation of CNNs".

# AdaLayer-CAM: Adaptive Multi-Layer Method for Visualization and Explanation of CNNs

This repository provides the **official PyTorch implementation** of the paper:

**"AdaLayer-CAM: Adaptive Multi-Layer Method for Visualization and Explanation of CNNs"**  
M. J. GhaderiPoor, L. PourMohammadBagher, Z. Rahimi  
(2025 — under review)

---

## 🚀 Run the Demo (Google Colab)

The simplest way to try AdaLayer-CAM is through Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](
https://colab.research.google.com/github/<your-username>/AdaLayer-CAM/blob/main/notebooks/AdaLayerCAM_Demo.ipynb
)

*(Replace `<your-username>` and the notebook path once your repository is live.)*

---

## 📘 Overview

**AdaLayer-CAM** is a fully multi-layer Class Activation Map (CAM) method designed to produce **cleaner, sharper, and more reliable** visual explanations for CNN-based models.

Unlike Grad-CAM or LayerCAM, AdaLayer-CAM:

- Utilizes **all convolutional layers** (not just one or a few)
- Computes **activation-energy-based adaptive layer weights**
- Fuses per-layer CAMs through a stable **Soft-ReLU (sigmoid) fusion**
- Produces high-quality CAMs with reduced noise and improved object localization

This implementation includes:
- Core AdaLayer-CAM modules  
- Baseline methods (Grad-CAM, Grad-CAM++, Score-CAM, LayerCAM)  
- Evaluation scripts  
- Visualization utilities  
- A Colab demo notebook  

---

## ✨ Features

- Fully multi-layer CAM aggregation  
- Adaptive per-layer weighting using activation energy  
- Soft-ReLU fusion for stable and noise-resistant heatmaps  
- Plug-and-play PyTorch implementation  
- Preconfigured scripts for ImageNet and Pascal VOC  
- Colab-ready example notebook  

---

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/AdaLayer-CAM.git
cd AdaLayer-CAM
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

Minimum dependencies:

```
torch>=2.0
torchvision>=0.15
numpy
matplotlib
opencv-python
pillow
tqdm
```

---

## ⚡ Quick Start

A minimal working example:

```python
import torch
import torchvision.models as models
from src.adalayer_cam.adalayer_cam import AdaLayerCAM
from src.utils.visualization import visualize_cam_on_image

# Load a pretrained model
model = models.resnet50(weights=models.ResNet50_Weights.IMAGENET1K_V1)
model.eval()

# Initialize AdaLayer-CAM (all convolutional layers)
adalayer_cam = AdaLayerCAM(model=model, target_layers="all")

# Your input tensor (1 × 3 × H × W) normalized for ImageNet
input_tensor = ...

# Compute CAM (target_class=None → uses predicted class)
cam_map = adalayer_cam(input_tensor, target_class=None)

# Visualize CAM overlay
output_img = visualize_cam_on_image(input_tensor, cam_map)
output_img.save("adalayer_cam_result.png")
```

More examples are available in:

- `examples/simple_inference.py`
- `notebooks/AdaLayerCAM_Demo.ipynb`

---

## 📁 Project Structure

```
AdaLayer-CAM/
│
├── src/
│   ├── adalayer_cam/
│   │   ├── adalayer_cam.py
│   │   ├── cam_base.py
│   │   ├── grad_cam.py
│   │   ├── score_cam.py
│   │   └── layer_cam.py
│   └── utils/
│       ├── visualization.py
│       ├── metrics.py
│       └── data.py
│
├── examples/
│   └── simple_inference.py
│
├── notebooks/
│   └── AdaLayerCAM_Demo.ipynb
│
├── experiments/
│   ├── configs/
│   └── run_imagenet.py
│
├── assets/
│   └── figures/
│
├── requirements.txt
├── CITATION.cff
├── LICENSE
└── README.md
```

---

## 📊 Reproducing Experimental Results

### 1. Configure dataset paths
Modify the config files located in:

```
experiments/configs/
```

### 2. Run ImageNet evaluation

```bash
python experiments/run_imagenet.py \
  --config experiments/configs/resnet50_imagenet.yaml \
  --method adalayer_cam
```

### Implemented metrics

- Average Drop (%)  
- Insertion AUC  
- Deletion AUC  
- Pointing Game accuracy  

---

## 📝 Citation

If you use this work, please cite:

```bibtex
@article{GhaderiPoor2025AdaLayerCAM,
  title={AdaLayer-CAM: Adaptive Multi-Layer Method for Visualization and Explanation of CNNs},
  author={GhaderiPoor, MohammadJavad and PourMohammadBagher, Latifeh and Rahimi, Zahra},
  year={2025},
  journal={...}
}
```

---

## 📄 License

MIT License.

---

## 📬 Contact

For questions or collaborations:

- **MohammadJavad GhaderiPoor** — mohammadjavadghaderipoor@gmail.com  
- **Latifeh PourMohammadBagher** — l_pmb@atu.ac.ir  
- **Zahra Rahimi** — za.rah@atu.ac.ir


## Example Results

<p align="center">
  <img src="images/image1.png" width="28%">
  <img src="images/image3.png" width="28%">
</p>



coming soon...
