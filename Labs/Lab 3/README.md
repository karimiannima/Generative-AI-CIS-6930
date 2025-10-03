# 🫀 Fine-Tuning Pre-Trained Models for ECG Analysis with PEFT

## 📊 Dataset Overview

- **Dataset Name:** `df_segment2.csv`  
- **Shape:** `65,425 × 601`  
- **Description:**  
  - Each **row** corresponds to one ECG segment.  
  - Each segment contains **600 signal samples**, followed by a **binary label** (`0` or `1`) in the **last column**.  
  - Segments originate from multiple users (user IDs are **not provided**).

### 📥 Download  
The dataset can be downloaded from the following link (requires USF Learn authentication):

👉 [USF Learn – df_segment2.csv](https://usflearn.instructure.com/courses/2047050/files?preview=199873452)

### 🧪 Preprocessing (Required)

Before training, each ECG segment must be **normalized**:

- ✅ **Per-segment z-score (Recommended)**  
  For each row \( x \):  
  \[
  x' = \frac{x - \mu_{\text{row}}}{\sigma_{\text{row}}}
  \]

- 🧪 **Global z-score (For Ablation)**  
  Compute the global mean and standard deviation across the entire dataset and normalize all samples accordingly.

---

## 🧠 Assignment Overview

The objective of this assignment is to **fine-tune pre-trained audio and foundation models** for ECG signal analysis using **Parameter-Efficient Fine-Tuning (PEFT)** methods such as **Adapters** and **LoRA**.

### 🎯 Goal  
> Fine-tune **Wav2Vec2**, **HuBERT**, and the **ECG-FM foundation model** for **binary classification** on ECG segments.

**Models to use:**  
- [Wav2Vec2](https://huggingface.co/facebook/wav2vec2-base)  
- [HuBERT](https://huggingface.co/facebook/hubert-base-ls960)  
- [ECG-FM](https://github.com/bowang-lab/ECG-FM)

---

## 📝 Tasks

### 1. Model Selection & Preparation
- Select **two pre-trained models** (Wav2Vec2 and HuBERT) and include **ECG-FM**.  
- Understand each model’s **architecture**, **input format**, and **capabilities**.  
- Preprocess the ECG dataset appropriately for each model.

### 2. Fine-Tuning with PEFT
Implement and compare two PEFT techniques for each model:
- 🧩 **Adapters**  
- 🪄 **LoRA (Low-Rank Adaptation)**

### 3. Implementation & Training
- Use **PyTorch** or **TensorFlow** for implementation.  
- Fine-tune each model with adapters and LoRA.  
- Perform hyperparameter tuning (e.g., learning rate, batch size, epochs).  
- Log training and validation curves for analysis.

### 4. Evaluation & Comparison
Evaluate and compare models using:
- **Accuracy**  
- **Precision**  
- **Recall**  
- **F1-score**

Analyze trade-offs between adapters and LoRA for each model.

---

## 📦 Deliverables

1. **Report (PDF or Markdown)**  
   - Description of the models and their architectures  
   - PEFT techniques implemented  
   - ECG preprocessing pipeline  
   - Training process and hyperparameters  
   - Evaluation metrics and performance comparison

2. **Code**  
   - Scripts or notebooks for each model × PEFT technique  
   - Clean, well-documented code

---

## 🧮 Grading Criteria

| **Category**                          | **Points** | **Description** |
|---------------------------------------|------------|-----------------|
| Model Understanding & Selection       | 40 pts     | Understanding architectures, justifying model & PEFT choices |
| Implementation & Training             | 60 pts     | Correct implementation, training, tuning |
| Evaluation & Comparison               | 60 pts     | Proper metric computation and analysis |
| Report Quality & Clarity              | 40 pts     | Clear, structured, insightful report |

---

## 📚 References

- [Hugging Face Transformers](https://huggingface.co/docs/transformers/index)  
- [LoRA: Low-Rank Adaptation of Large Language Models](https://arxiv.org/abs/2106.09685)  
- [ECG-FM Foundation Model](https://github.com/bowang-lab/ECG-FM)  

---

## 📂 Suggested Project Structure

