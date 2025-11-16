# Cross-Lingual Sign Language Transfer Learning  
### ISL → Bengali → Assamese | Landmark-Based Gesture Classification

This project explores whether a model trained on a large Indian Sign Language (ISL) landmark dataset can effectively transfer knowledge to low-resource regional sign languages like Bengali and Assamese.  
Using numerical hand-landmark features (~50K ISL, ~10K Bengali, ~2.5K Assamese), the project evaluates both:

- **Baseline classifiers** for each language
- **Cross-lingual transfer learning** using a two-phase strategy  
  - **Phase 1:** Freeze encoder → train classifier  
  - **Phase 2:** Full fine-tuning

---

## Key Results

| Transfer Direction | Baseline Acc | Transfer Acc | Improvement |
|-------------------|--------------|--------------|-------------|
| **ISL → Bengali** | ~77%         | **~82%**     | +5%         |
| **ISL → Assamese** | ~99%        | ~99%         | ≈ same (dataset very easy) |
| **Bengali → Assamese** | ~99%    | **~99.5%**   | small but consistent gain |

These results show that *even lightweight MLP models learn reusable gesture representations across languages*.

---

## Dataset Summary

- **ISL Dataset:** ~50,000 samples  
- **Bengali Dataset:** ~10,000 samples  
- **Assamese Dataset:** ~2,500 samples  

Each sample contains **126 numerical features** representing hand landmark coordinates extracted from videos.

---

## 🔧 Methodology

### **1. Baseline Models**
- Trained separate MLP classifiers for ISL, Bengali, and Assamese.
- Tracked accuracy curves and confusion matrices.

### **2. Transfer Learning Pipeline**
1. Load encoder weights from source language  
2. Train only classifier head (frozen encoder)  
3. Full-model fine-tuning  
4. Compare against baselines

### **3. Evaluation**
- Train/Val/Test splits  
- Accuracy curves  
- Confusion matrices  
- End-to-end timing and reproducible seeds  
- All results exported in `/results/` (plots, logs, CSVs)

---

## Visuals

### Accuracy Curves
> *Baseline vs Transfer*

![Example Accuracy Curve](<img width="1383" height="939" alt="isl_to_bengali_20251104_071830" src="https://github.com/user-attachments/assets/bfad33b9-42aa-49d3-92c5-5f4a305e059c" />
)

### Confusion Matrices

![Example Confusion Matrix](<img width="1281" height="1093" alt="isl_to_bengali_cm_20251104_071830" src="https://github.com/user-attachments/assets/1add56ab-945b-41f0-896e-60d1b8f0939d" />
)


---

## Tech Stack

- **Python**, NumPy, pandas  
- **PyTorch** (MLP models, training loops)  
- Matplotlib + Seaborn (for plots)

---

## 🔍 Conclusion

This work demonstrates that **cross-lingual transfer learning significantly boosts performance** for low-resource sign languages.  
It also shows that **simple MLP models can learn universal gesture embeddings**, making this approach useful even without deep video models.

---

## 🧑‍💻 Author

**Shashwat Laloriya**  

