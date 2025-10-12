# 🖼️ CycleGAN — Unpaired Style Transfer (Monet ↔ Photo)

This assignment guides you through implementing and analyzing a **CycleGAN** (Cycle-Consistent Adversarial Network) to perform **unpaired image-to-image translation** between **Monet paintings** and **real photos**.  
You will focus on designing and implementing key **loss functions** (LSGAN, identity, and cycle consistency) and interpreting training dynamics.

---

## 🎯 Learning Objectives
By the end of this assignment, you should be able to:

- Explain how **cycle consistency** enables unpaired translation.
- Implement **LSGAN adversarial**, **identity**, and **cycle consistency** losses.
- Understand the role of each loss in stabilizing unpaired training.
- Diagnose training artifacts such as mode collapse or color shifts.

---

## 📁 Dataset
Use the **Monet2Photo** dataset structured as follows:

```
monet2photo/
│
├── trainA/   # Monet paintings
├── trainB/   # Real photos
├── testA/
└── testB/
```

Each image will be resized to **286×286**, then randomly cropped to **256×256**, flipped horizontally, and normalized to `[-1, 1]`.

You can download the dataset from Kaggle or other CycleGAN sources:
- [Monet2Photo Dataset on Kaggle](https://www.kaggle.com/datasets/andrewmvd/monet2photo)

---

## ⚙️ Environment Setup
### Requirements
```bash
pip install torch torchvision matplotlib pillow tqdm
```

If running on Google Colab, ensure GPU is enabled:
```
Runtime → Change runtime type → Hardware accelerator → GPU
```

---

## 🧩 Implementation Tasks (Student TODOs)

You will complete the following five functions inside the notebook:

| Function | Description |
|-----------|--------------|
| `get_disc_loss(real_X, fake_X, disc_X, adv_criterion)` | LSGAN loss for discriminator |
| `get_gen_adversarial_loss(real_X, disc_Y, gen_XY, adv_criterion)` | Generator adversarial loss |
| `get_identity_loss(real_X, gen_YX, identity_criterion)` | Identity mapping loss |
| `get_cycle_consistency_loss(real_X, fake_Y, gen_YX, cycle_criterion)` | Cycle consistency loss |
| `get_gen_loss(...)` | Total generator loss combining all above terms |

Each function includes clear TODO tags and docstrings for guidance.

---

## 🧠 Key Hyperparameters
| Parameter | Description | Default |
|------------|-------------|----------|
| `λ_cyc` | Cycle-consistency loss weight | 10 |
| `λ_id` | Identity loss weight | 0.1 |
| `batch_size` | Training batch size | 1 |
| `lr` | Learning rate | 2e-4 |
| `n_epochs` | Number of epochs | 20 |
| `optimizer` | Adam (β₁=0.5, β₂=0.999) | — |

---

## 🧪 Experiments (Ablations)
Perform two small ablation studies:

1. **Cycle weight sweep:** `λ_cyc ∈ {5, 10, 20}`  
   - Observe effects on content preservation and stylization.
2. **Identity loss on/off:** `λ_id ∈ {0.0, 0.1}`  
   - Observe color and tone preservation differences.

*(Optional)*  
Try adding one stabilization technique, such as:
- Fake image replay buffer  
- One-sided label smoothing  
- Learning rate decay  

---

## 📊 Report Expectations (2–4 Pages)
Include the following sections in your report:

1. **Method** – Explain the CycleGAN architecture and loss equations.  
2. **Experimental Setup** – Dataset, augmentations, and hyperparameters.  
3. **Results** –  
   - Monet→Photo and Photo→Monet generated samples  
   - Cycle reconstructions (A→B→A, B→A→B)  
   - Generator/discriminator loss curves  
   - Ablation comparison tables  
4. **Discussion** – Analyze how λ_cyc and λ_id impact translation quality.  
5. **Conclusion** – Key takeaways and comparison with paired models (Pix2Pix).

---

## 📦 Deliverables
Submit a single ZIP file containing:

```
<LastName>_CycleGAN_Assignment.zip
│
├── CycleGAN_MonetPhoto_Assignment.ipynb   # Completed notebook
├── CycleGAN_MonetPhoto_Report.pdf         # 2–4 page report
└── samples/                               # Optional: Generated outputs
```

---

## 💯 Grading Rubric

| Area | Criteria | Points |
|------|-----------|--------|
| **Loss Implementations** | All five loss functions correct & tested | 35 |
| **Training & Results** | Functional model; plausible translations | 25 |
| **Ablation Studies** | Two experiments completed with analysis | 15 |
| **Report Quality** | Clear, concise, and well-structured | 20 |
| **Code Quality** | Readable and reproducible | 5 |

---

## 🧰 References
- Zhu et al., *Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks*, ICCV 2017  
- [Original CycleGAN GitHub Repository](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix)  
- [LSGAN Paper](https://arxiv.org/abs/1611.04076)

