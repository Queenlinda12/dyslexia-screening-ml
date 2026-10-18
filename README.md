# Two Windows into Dyslexia
**Machine-learning screening from children's handwriting and reading-game play**
Sheja Queen Linda · African Leadership University · ML Final Project

📄 Report:   [Report](Report.pdf) · 🎥 Video: [add link] · 💾 Drive (models & logs): (https://drive.google.com/drive/folders/1otzYYGvvjDFKtjItnNcUhGqERP9MFmpG?usp=sharing)

## Overview
Dyslexia often goes unnoticed in schools without specialists. This project builds two low-cost screening tools (not diagnosis) to help teachers refer children early:
- **Module A – Handwriting:** classifies 208,372 letters as Normal / Reversal / Corrected (E01–E11)
- **Module B – Reading games:** predicts dyslexia from 3,644 children's game performance, tested on 1,395 unseen tablet users (G01–G08)

19 experiments across classic ML, CNNs and transfer learning, logged with Weights & Biases (offline) and TensorBoard.

## Results
| Model | Test macro-F1 | Test ROC-AUC |
|---|---|---|
| SVM on HOG features (E05) | 0.850 | 0.954 |
| **Regularised CNN (E08)** | **0.892** | **0.980** |
| MobileNetV2 fine-tuned (E11) | 0.772 | 0.930 |
| **Gradient Boosting, games (G05)** | 0.723 | **0.898** (0.621 on tablets) |

## Key findings
- 1 in 5 handwriting test images duplicated training images; removed before training
- 3,808 game values had lost their decimal point; repaired exactly
- Regularisation lowered validation scores but improved results on new handwriting
- The game model relied partly on age and a language flag, and missed half of 7–8-year-olds
- Tools must be re-validated on local (e.g. Rwandan) children before any use

## How to run
1. Open `Dyslexia_Screening_Two_Modules.ipynb` in Google Colab
2. Runtime → Change runtime type → **T4 GPU**
3. Runtime → **Run all** (datasets download automatically from Kaggle; about 1.5–2 hours)

Seeds are fixed for reproducibility; library versions are in `requirements.txt`.

## Repository
```
Dyslexia_Screening_Two_Modules.ipynb   notebook with all outputs
requirements.txt                       library versions
outputs/                               results CSVs, figures, TensorBoard & W&B logs
```

## Credits
Handwriting data: Isa et al., [Kaggle](https://www.kaggle.com/datasets/drizasazanitaisa/dyslexia-handwriting-dataset) · Game data: Rello et al., *PLOS ONE* 2020, [Kaggle](https://www.kaggle.com/datasets/luzrello/dyslexia) · MobileNetV2 (ImageNet weights) · AI assistance (Claude) for code and documentation.
