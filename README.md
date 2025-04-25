# fsl-fingerprint-recognition
[![Open Notebook in nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.org/github/Mahdi-Savoji/fsl-fingerprint-recognition/blob/main/fsl-fingerprint-recognition.ipynb)


# Few-Shot Learning (FSL) with Pretrained Base Model and Triplet Loss  

## 📌 Project Overview  
This project implements **Few-Shot Learning (FSL)** using a pretrained base model and **triplet loss** for image classification. The model is trained on a support set and evaluated on a query set with limited labeled examples.  

---

## 📊 Dataset Summary  
### Main Dataset  
- **Total Images**: `800`  
- **Image Shape**: `(128, 128, 3)`  
- **Labels Shape**: `(800,)`  

### Support Set (Training)  
- **Images Shape**: `(25, 128, 128, 3)`  
- **Labels Shape**: `(25,)`  

### Query Set (Testing)  
- **Images Shape**: `(25, 128, 128, 3)`  
- **Labels Shape**: `(25,)`  
- **Unique Labels**: `[3, 4, 5, 6, 8]`  

### Siamese Training (Triplet Generation)  
- **Total Triplets**: `400`  
- **Anchor/Positive/Negative Shapes**: `(400, 128, 128, 3)`  
- **Unique Labels**: `[0, 1, 2, 7, 9]`  

---

## 🧠 Model Architecture  
**Model Type**: Siamese Network with Triplet Loss  
**Base Model**: Pretrained Functional Model  

### Model Summary  
```python
Model: "functional_7"
┏━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━┓
┃ Layer (type)        ┃ Output Shape      ┃ Param #    ┃
┡━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━┩
│ InputLayer          │ (None, 128, 128, 3) │ 0         │
│ Functional (Base)   │ (None, 256)       │ 4,377,507  │
│ Lambda (Distance)   │ (None, 1)         │ 0          │
│ Concatenate         │ (None, 2)         │ 0          │
└─────────────────────┴───────────────────┴────────────┘

```
#### Single-image Inference Performance: 2.4473 sec (128×128 RGB input)
