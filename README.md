# Team Polyphenols

## Team Members
- **Savannah Gong** - [GitHub Profile](https://github.com/savannahgong)
- **Sally Hong** - [GitHub Profile](https://github.com/hongsally)
- **Amrit Randev** - [GitHub Profile](https://github.com/amrandev)
- **Zoya Shamak** - [GitHub Profile](https://github.com/zoyas)

---

## Project Highlights  
- **Fair AI Diagnostics**: Developed a skin condition classifier that performs equitably across Fitzpatrick skin types I-VI  
- **State-of-the-Art Techniques**: Leveraged transfer learning (EfficientNet, ResNet) with fairness-aware fine-tuning  
- **Key Metric**: Achieved **weighted F1-score of 0.XX** (top X% in Kaggle leaderboard)  
- **Impact Focus**: Directly addresses the [3:1 diagnostic disparity](https://doi.org/10.1038/s41591-020-0842-1) for darker skin tones in dermatology AI  

---

## Setup & Execution  
### Installation  
```bash
git clone https://github.com/your-repo/polyphenols.git
pip install -r requirements.txt  # Includes torch, torchvision, sklearn, albumentations
```
### Running the Model
```
from src.inference import SkinConditionClassifier
model = SkinConditionClassifier("weights/efficientnet_b4_finetuned.pth")
prediction = model.predict("path_to_image.jpg")  # Returns (class_name, confidence, skin_tone_adjusted_score)
```


---

## Project Overview
This project is part of the **Spring 2025 AI Studio**, a collaboration between **Break Through Tech** and the **Algorithmic Justice League (AJL)**. The goal is to build an inclusive machine learning model to classify **21 skin conditions** across diverse skin tones. The model will be evaluated using a **weighted average F1 score**, ensuring fairness and accuracy for all skin tones. This work addresses the underperformance of dermatology AI tools for darker skin tones, aiming to reduce health disparities and improve diagnostic accuracy.

---

## Data Exploration
### Dataset
The dataset includes images of skin conditions across diverse skin tones. Key steps in data exploration:
- **Class Distribution**: Analyzing the distribution of skin conditions to identify imbalances.
- **Skin Tone Representation**: Ensuring diverse skin tones are adequately represented.
- **Data Augmentation**: Expanding the dataset using techniques like flipping, rotation, and color adjustments.

### Key Challenges
- **Imbalanced Classes**: Some skin conditions may be underrepresented.
- **Fairness**: Ensuring the model performs equally well across all skin tones.
- **Explainability**: Making the model's decision-making process transparent.

---

## Approach
### 1. **Data Augmentation**
We used data augmentation techniques (e.g., flipping, rotation, color adjustments) to improve model robustness and address class imbalance.

### 2. **Transfer Learning**
We fine-tuned pre-trained models (e.g., ResNet, EfficientNet) on the competition dataset to improve accuracy and reduce computational requirements.

---

## Model Development
### Architecture Selection
| Model | Pretrained Base | Fairness Modifications |
|-------|-----------------|------------------------|
| **ResNet-152** | DermNet | Attention gates for lesion localization |

### Key Techniques
1. **Fairness-Aware Training**
   - Skin tone stratification during validation (Fitzpatrick scale)
   - Class-weighted loss function with α=1.2 for rare conditions

2. **Explainability**
   - Integrated Gradients for decision attribution
   - Confidence calibration by skin tone subgroup

---

## Results & Key Findings
### Performance Metrics  
| Skin Tone Group | Precision | Recall | F1-Score |  
|-----------------|-----------|--------|----------|  
| I-II (Light) | 0.18 | 0.12 | 0.14 |  
| III-IV (Medium) | 0.15 | 0.11 | 0.13 |  
| V-VI (Dark) | 0.13 | 0.09 | 0.11 |  

**Overall Weighted F1**: 14% (±3% across tones)  

### Critical Insights & Improvement Pathways  
While our initial accuracy of 14% fell short of targets, this provides valuable learning opportunities:

**Data Challenges:**
- Severe class imbalance (some conditions had <50 samples)
- Skin tone representation gaps in training data (only 12% Fitzpatrick V-VI)
- Label inconsistency in borderline cases

**Model Behavior:**
- Highest confusion between visually similar conditions (e.g., eczema vs. psoriasis)
- Performance dropped sharply for rare conditions (<5% recall)
- Attention maps often focused on irrelevant background features

---

## Impact Narrative  
Our work directly supports **SDG 3.8** for equitable healthcare access. By open-sourcing this model, we:  

Reduce Diagnostic Disparities, Enable Global Access, Promote Transparency, which we believe is important.

---

## Next Steps & Future Improvements    
- [ ] Improve our accuracy through hyperparameters 
- [ ] Utilize data augmentation to futrther train and optimize our model
