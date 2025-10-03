🫀 Fine-Tuning Pre-Trained Models for ECG Analysis with PEFT
📊 Dataset Overview

Dataset Name: df_segment2.csv

Shape: 65,425 × 601

Description:

Each row represents one ECG segment.

Each segment contains 600 signal samples followed by a binary label (0 or 1) in the last column.

Segments originate from multiple users (user IDs are not provided to students).

📥 Download

You can download the dataset from:
👉 USF Learn – df_segment2.csv

Note: You must be logged into your USF Learn account to access the file.

🧪 Preprocessing (Required)

Before feeding the data into models, you must normalize each segment:

✅ Per-segment z-score (Recommended)
For each row 
𝑥
x:

𝑥
′
=
𝑥
−
𝜇
row
𝜎
row
x
′
=
σ
row
	​

x−μ
row
	​

	​


🧪 Global z-score (For Ablation)
Compute the global mean and standard deviation over the entire dataset and normalize all samples accordingly.

🧠 Assignment Overview

The goal of this assignment is to fine-tune pre-trained audio and foundation models for ECG signal analysis using Parameter-Efficient Fine-Tuning (PEFT) methods such as Adapters and LoRA.

🎯 Objective

Fine-tune Wav2Vec2, HuBERT, and the ECG-FM foundation model for binary classification of ECG signals.

📚 Models to use:

Wav2Vec2

HuBERT

ECG-FM

📝 Tasks
1. Model Selection & Preparation

Choose two pre-trained models (Wav2Vec2 and HuBERT) and include ECG-FM.

Study their architectures, expected input format, and capabilities.

Preprocess the ECG data to match each model's input requirements (e.g., reshape 1D signals as needed).

2. Fine-Tuning with PEFT

Implement and compare two PEFT techniques for each model:

🧩 Adapters

🪄 LoRA (Low-Rank Adaptation)

3. Implementation & Training

Use PyTorch (preferred) or TensorFlow.

Implement fine-tuning for each model with adapters and LoRA.

Tune hyperparameters such as learning rate, batch size, epochs, and regularization.

Log training and validation curves for analysis.

4. Evaluation & Comparison

Evaluate models using:

Accuracy

Precision

Recall

F1-score

Compare adapters vs LoRA for each model and analyze trade-offs in performance, convergence, and resource usage.

📦 Deliverables

📄 Report (PDF or Markdown)

Overview of models and their architectures.

Description of PEFT techniques used.

ECG preprocessing pipeline.

Training process and hyperparameters.

Quantitative results and performance comparison.

💻 Code

Implementation scripts or notebooks for each model × PEFT combination.

Clear documentation and comments.

🧮 Grading Criteria
Category	Points	Description
Model Understanding & Selection	40 pts	Correct model choice, architectural understanding, PEFT justification
Implementation & Training	60 pts	Proper implementation and training with adapters/LoRA
Evaluation & Comparison	60 pts	Metric computation, adapters vs LoRA comparison
Report Quality & Clarity	40 pts	Clear, organized, well-written report with insights
📚 References

Hugging Face Transformers

LoRA: Low-Rank Adaptation of Large Language Models

ECG-FM Foundation Model
