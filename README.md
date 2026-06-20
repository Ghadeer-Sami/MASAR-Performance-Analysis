# MASAR – AI-Powered Drone Localization System  
AI Systems Design – Course Project

MASAR is an AI-driven drone localization prototype designed to match drone-view images with satellite imagery using a Vision Transformer (TransGeo), FAISS retrieval, and XAI visualization. The project demonstrates the full AI pipeline, evaluation, and a deployment prototype.

---

## Project Overview
MASAR aims to identify the geographic location of a drone image by retrieving the closest matching satellite image. The system uses:
- **TransGeo (Vision Transformer backbone)** for feature extraction  
- **FAISS** for fast similarity search  
- **Recall@K** for evaluation  
- **XAI visualizations** to explain predictions  

The full pipeline was implemented and tested in **Google Colab**, with a UI prototype and a partial Streamlit deployment attempt.

---

## Model Architecture
- **Backbone:** Vision Transformer (ViT) inside TransGeo  
- **Loss Function:** Symmetric cross‑entropy between normalized embeddings  
- **Retrieval:** FAISS index search  
- **Evaluation Metrics:** Recall@1, Recall@5, Recall@10  
- **Explainability:** XAI heatmaps for matched satellite images  

---

## Deployment Strategy
Due to GPU and dependency limitations, full deployment was not possible. Instead, the team delivered:

### What Was Deployed
- A **UI prototype** showing:
  - Login screen  
  - Operational dashboard  
  - Prediction + XAI explanation screen  
- A **local Streamlit prototype** demonstrating:
  - Uploading a drone image  
  - Displaying predicted satellite match  
  - Showing XAI output  

### What Could Not Be Deployed
- Full backend pipeline (TransGeo + FAISS + XAI)  
- GPU‑dependent model hosting  
- Real‑time drone integration  

### Prototype Interface  
UI Prototype:  
https://stitch.withgoogle.com/preview/10823588653852611758?node-id=1c8e539f7c3b4e02810b5493f4499345

---

## Model Collapse Analysis

### 1. Did the model collapse during training?  
**No.**

### 1.1 Indicators used to avoid collapse
- Monitoring **contrastive loss** for abnormal flattening  
- Ensuring **normalized embeddings** maintain stable distribution  
- Tracking **Recall@K** to detect representation collapse  
- Gradual dataset scaling to ensure stable learning  

### 2. Possible collapse after deployment  
**Operational / Production Drift Collapse**  
Caused by:
- Weather changes  
- Seasonal lighting  
- Urban development  
- Environmental mismatch between drone and satellite images  

### 3. Proposed Fix: Drift Warning System  
A safety layer that checks the similarity score between live drone embeddings and FAISS matches.  
If similarity < threshold → trigger warning.


