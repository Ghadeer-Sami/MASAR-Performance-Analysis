# MASAR – Vision-Based Drone Localization System  

---

## Overview
MASAR is an AI-powered navigation system designed to enable drones to localize themselves visually in GPS-denied environments.  
Instead of relying on GPS signals, MASAR uses computer vision and deep learning to match live drone images with reference satellite imagery, determining the drone’s coordinates with high accuracy.  
The system integrates **Explainable AI (XAI)** to visualize and justify predictions, enhancing transparency and operator trust.

---

## Project Objectives
- Develop a **vision-based localization system** using the TransGeo model (Vision Transformer backbone).  
- Achieve reliable navigation in GPS-degraded or GPS-denied environments.  
- Provide **XAI visual explanations** for every prediction to improve interpretability.  
- Support emergency response, search and rescue, and autonomous operations in critical environments.

---

## Model Architecture
- **Model:** TransGeo (Zhu et al., CVPR 2022)  
- **Backbone:** Vision Transformer (ViT)  
- **Feature Extraction:** 512-dimensional embeddings for drone and satellite images  
- **Retrieval Engine:** FAISS for fast nearest-neighbor search  
- **Evaluation Metrics:** Recall@1, Recall@5, Recall@10  
- **Explainability:** Saliency maps and attention visualizations for prediction transparency  

---

## Dataset
- **Source:** University-1652 Benchmark Dataset  
- **Content:** Multi-view images (drone, satellite, ground) from 72 universities  
- **Scale:** 1,652 buildings, 28,000+ images  
- **Purpose:** Cross-view geo-localization and visual matching  
- **Preprocessing:**  
  - Resizing to 256×256  
  - Normalization using ImageNet statistics  
  - Augmentation (rotation, flipping, color jitter)  
  - DataLoader batching and shuffling for efficient training  

---

## Implementation
- **Frameworks:** Python, PyTorch, OpenCV, FAISS  
- **Environment:** Google Colab  
- **Data Handling:** Automated ingestion and pairing of drone–satellite images  
- **Version Control:** GitHub repository with modular code and checkpoints  
- **Model Checkpoints:** `MASAR_TransGeo_subset.pth`  

---

## AI Lifecycle Summary
### 1. Scoping
- Defined problem: GPS signal loss and unreliability in urban or obstructed areas.  
- Target users: Drone operators, emergency teams, defense sectors, and autonomous vehicle developers.  
- KPIs: Localization accuracy (ATE), drift error (RPE), inference latency, and robustness.

### 2. Data
- Data sourced from University-1652.  
- Preprocessing pipeline implemented in Colab.  
- Data governance ensured through validation checks and version control.

### 3. Modeling
- TransGeo model adopted as the main architecture.  
- Hyperparameter tuning and iterative training performed.  
- FAISS retrieval integrated for fast similarity search.

### 4. Deployment
- Logical architecture designed for cloud-based processing.  
- UI prototypes created for:
  - Secure login  
  - Operational dashboard  
  - Prediction + XAI explanation screen  
- Streamlit prototype tested locally.

### 5. Monitoring
- Logging hooks and error handling integrated.  
- Model drift detection and update strategy proposed.  
- Disaster recovery and reliability considerations documented.

---

## Evaluation & Results
- **Recall@K Performance:** High retrieval accuracy across multiple scales.  
- **Latency Tests:** Optimized inference time using FAISS.  
- **Stress Testing:** Robustness verified under lighting and environmental variations.  
- **XAI Verification:** Saliency maps confirmed model transparency and interpretability.

---

## Risk Assessment
| Risk | Impact | Mitigation |
|------|---------|-------------|
| Limited time | High | Focused proof-of-concept on localized dataset |
| Lack of features | High | Use TransGeo’s self-attention for global context |
| Hardware constraints | Medium | Simulated environment for testing |
| Poor lighting | Medium | Data augmentation for robustness |
| Computational lag | Medium | FAISS integration for fast retrieval |

---

## Ethical & Legal Considerations
- **Privacy:** Transition planned from cloud-based to onboard processing to avoid data exposure.  
- **Bias Mitigation:** Diverse training data and augmentation to prevent geo-localization bias.  
- **Compliance:** Adheres to SDAIA AI Ethics Principles and national data governance laws.  
- **Societal Impact:** Supports humanitarian and safety missions while maintaining transparency.

---

## Future Work
- Full deployment on GPU-enabled server or drone hardware (e.g., NVIDIA Jetson).  
- Real-time localization and communication pipeline.  
- Integration of drift warning system for operational safety.  
- Expansion to multi-drone collaborative localization.

---

## Date
June 24, 2026
