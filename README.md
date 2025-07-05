# Emotional Expression & Speech Recognizer

## Overview

This project aims to build a multimodal system that classifies human emotions by analyzing both **facial expressions** and **speech**. This work addresses the limitations of traditional human-computer interaction systems, especially for individuals with **alexithymia** — a condition involving difficulty in identifying and expressing emotions.

## Team Members

- Isaac Yeoh
- Tushar Agashe  
- Shiyang Xin  
- Xiao Guo

## Motivation

Current AI systems struggle to fully interpret human emotions. People with alexithymia, in particular, cannot easily communicate how they feel, and no conversational agents currently address this. Our goal is to build a dual-input emotion recognition system that combines visual and auditory cues to better classify human emotions in real-time.

## System Architecture

The proposed system consists of:
- **Facial Emotion Classifier (Image CNN)**
- **Speech Emotion Classifier (Audio CNN)**

These models operate independently and their outputs are compared to determine the final predicted emotion from a video source. Our workflow is shown below:

<img width="1027" alt="Screenshot 2025-07-04 at 6 26 39 PM" src="https://github.com/user-attachments/assets/fd553fa5-ca20-400e-ae19-e31c6947d24f" />

---

## 1. Facial Expression Model

### Data
- **Dataset**: FER-2013 (48x48 grayscale images)
- **Classes**: 7 emotions
- **Split**: 64% Train / 16% Validate / 20% Test

### Methods
- Built CNN models using both TensorFlow and PyTorch
- Hyperparameter tuning across:
  - Convolution filters
  - Dense layer sizes
  - Dropout rates
  - Learning rates

### Best Model
- Achieved **64% accuracy**
- Best performing on: **Happy**, **Surprise**, **Neutral**
- Harder to classify: **Fear**, **Disgust**, **Angry** due to subtle expressions

---

## 2. Emotional Speech Model

### Data
- **Dataset**: RAVDESS (1440 WAV files)
- **Phrases**: “Kids are talking by the door”, “Dogs are sitting by the door”
- **Emotions**: 7 classes

### Methods
- Feature extraction using **Librosa** (156 features)
- Data augmentation: noise addition, pitch shift, and time stretch
- Model: 1D CNN with ReLU activations

### Performance
- Achieved **61% accuracy**
- Best classification: **Happy**
- Poor classification: **Fear** due to overlap and possible overfitting

---

## Alternatives & Experiments

- Tried different CNN architectures and a pre-trained ResNet-18
- Additional datasets (≈11,970 samples) explored for speech model
- Advanced regularization and architecture complexity did not improve results significantly

### Benchmark Comparisons
- **FER model (Huang et al., 2023)**: 77.4% (limited external validity)
- **Speech model (Asmaa Samir, 2023)**: 97.3% (possible data leakage)
- **Marco Giuseppe de Pinto (2020)**: 80% accuracy

---

## Future Directions

- Improve dataset quality and diversity (especially for **Disgust**)
- More extensive hyperparameter searches
- Better augmentation strategies
- Combine both models for joint prediction and real-time inference
- Deploy as a full video-based AI emotion recognition agent

---

## Contact

Feel free to reach out with questions or suggestions!
