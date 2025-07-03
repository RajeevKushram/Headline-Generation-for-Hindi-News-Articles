# 📰 Headline Generation for Hindi News Articles using IndicBART and LoRA

This project implements an automatic Hindi headline generation system using transformer-based architectures — primarily **IndicBART-XLSum**. Two fine-tuning approaches are explored:
- **Standard Fine-Tuning** of the full model
- **Parameter-Efficient Fine-Tuning** using **LoRA (Low-Rank Adaptation)**

The project shows that LoRA achieves comparable performance while significantly reducing memory usage and training time — a practical solution for low-resource NLP environments.

---

## 📌 Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Model Architectures](#model-architectures)
- [Training & Evaluation](#training--evaluation)
- [Results](#results)
- [How to Run](#how-to-run)
- [Dependencies](#dependencies)
- [Project Report](#project-report)
- [Future Work](#future-work)

---

## 📘 Project Overview

In low-resource NLP environments like Hindi, full fine-tuning of large transformer models can be impractical. This project demonstrates the effectiveness of **LoRA** for headline generation using:
- **IndicBART-XLSum (Standard)**: Full fine-tuning.
- **IndicBART-XLSum with LoRA**: Only trainable low-rank matrices are updated.

Both models were evaluated using ROUGE, BLEU, METEOR, and BERTScore.

---

## 📚 Dataset

- **Source**: Mukhyansh dataset
- Each record contains:
  - `text` – The full Hindi news article
  - `title` – The corresponding headline

📥 [**👉 Click here to download the language-wise datasets**](https://drive.google.com/drive/folders/1PYUgWMqELhVbQ_nJ7EtpYo_R1xm7XM6y)


| Split       | Samples | Avg. Article Length | Avg. Headline Length |
|-------------|---------|----------------------|------------------------|
| Training    | 24,000  | 450 tokens           | 19 tokens              |
| Validation  | 4,500   | 440 tokens           | 15 tokens              |
| Testing     | 1,500   | 460 tokens           | 16 tokens              |

---

## 🧠 Model Architectures

### 1. Standard IndicBART Fine-Tuning
- All weights updated
- More compute-intensive

### 2. IndicBART + LoRA
- Frozen base model
- LoRA injected into attention layers
- Lightweight and modular

---

## 🏋️ Training & Evaluation

- **Framework**: Hugging Face Transformers + PEFT (LoRA support)
- **Loss**: CrossEntropy
- **Tokenizer**: IndicBART SentencePiece
- **Max Input Length**: 512
- **Max Output Length**: 32

### Evaluation Metrics:
- ROUGE-1, ROUGE-2, ROUGE-L
- BLEU
- METEOR
- BERTScore
- Human Evaluation (Relevance, Fluency, Conciseness)

---

## 📊 Results

| Metric      | IndicBART (Standard) | IndicBART (LoRA) |
|-------------|----------------------|------------------|
| ROUGE-1     | 0.493                | 0.423            |
| ROUGE-2     | 0.324                | 0.124            |
| ROUGE-L     | 0.519                | 0.429            |
| BLEU        | 0.158                | 0.118            |
| METEOR      | 0.288                | 0.242            |
| BERTScore   | 0.756                | 0.676            |

🟢 **LoRA saves ~50% GPU memory and halves training time** while achieving competitive results.

---

## ▶️ How to Run

1. Clone the repository:
   ```bash
   https://github.com/RajeevKushram/Headline-Generation-for-Hindi-News-Articles.git
   cd Headline-Generation-for-Hindi-News-Articles.git

2. Open and run:
- IndicBART Standard.ipynb
- IndicBART with LORA.ipynb

3. (Optional) Evaluate using your own dataset in JSONL format.

