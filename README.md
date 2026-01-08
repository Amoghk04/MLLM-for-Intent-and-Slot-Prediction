# Breaking Language Barriers in NLU
## Joint Intent and Slot Recognition with Enhanced XLM-RoBERTa

This repository provides the inference pipeline and interactive web interface for the research work:

**Breaking Language Barriers in NLU: Joint Intent and Slot Recognition with Enhanced XLM-RoBERTa**  
Accepted at the **16th IEEE International Conference on Computing, Communication and Networking Technologies (ICCCNT 2025)**, IIT Indore  
(To appear in IEEE Xplore)

The system demonstrates cross-lingual intent classification and slot filling using a joint XLM-RoBERTa model, evaluated on unseen languages without fine-tuning.

---

## 🔍 Overview

Modern NLU systems struggle to scale across languages due to syntactic variation, lexical divergence, and limited annotated data. This work addresses these challenges by:

- Leveraging **XLM-RoBERTa** for language-agnostic representations
- Training a **joint intent classification + slot filling model**
- Supporting **open-text, enumerated, and implicit slots**
- Generalizing to **unseen languages** in a zero-shot setting
- Providing a **real-time web interface** for practical evaluation

The model is trained on **English, Hindi, and Korean** and evaluated on **German, Spanish, Afrikaans, and French**.

---

## ✨ Key Contributions

- **Joint Modeling**: Unified architecture for intent recognition and slot extraction improves contextual alignment.
- **Zero-Shot Cross-Lingual Inference**: Strong generalization to unseen languages without retraining.
- **Diverse Slot Handling**:
  - Open-text slots (e.g., names, messages)
  - Enumerated slots (e.g., device types, modes)
  - Implicit slots inferred from user intent
- **Robust to Paraphrasing**: Handles explicit, implicit, and paraphrased commands.
- **Production-oriented Demo**: Web interface for real-time inference.

---

## 🧠 Model Architecture

- **Base Model**: XLM-RoBERTa
- **Variant**: `xlm-roberta-base`
- **Tokenizer**: SentencePiece (shared multilingual subword vocabulary)
- **Architecture**:
  - Shared transformer encoder
  - Intent classification head (utterance-level)
  - Slot tagging head (token-level sequence labeling)

### Joint Objective

The model is trained using a combined loss:

```
L_total = L_intent + L_slot
```

This encourages shared representations while preserving task-specific learning.

---

## 📊 Dataset

This work uses the **MASSIVE dataset**:

> **MASSIVE: A Large-Scale Multilingual Dataset for Slot Filling and Intent Classification**

- **Languages**: 52 total
  - **Training languages**: English, Hindi, Korean
  - **Evaluation (unseen) languages**: German, Spanish, Afrikaans, French
- **Per-language size**:
  - ~11.5k training samples
  - ~2.5k validation samples
  - ~2k test samples
- **Domains**:
  - Smart Home Control
  - Clock
  - Messaging

📌 **Note:**  
This repository does not include the dataset. The MASSIVE dataset can be obtained directly from Hugging Face.

---

## ✅ Experimental Results

| Task                    | Metric   | Score  |
|-------------------------|----------|--------|
| Intent Classification   | Accuracy | 92.85% |
| Slot Filling            | F1-Score | 92.88% |

- Results are reproducible using the provided model checkpoint.
- Performance remains consistent across structurally diverse unseen languages.

---

## 🌐 Web Interface

The repository includes a web-based interface that allows users to:

- Enter multilingual utterances
- View predicted intent
- Inspect extracted slots
- Test zero-shot behavior interactively

This interface is designed for rapid qualitative evaluation by NLU engineers and researchers.

---

## 🛠 Repository Scope

This repository contains:

✅ Inference code  
✅ Pretrained model checkpoint  
✅ Web application for live testing

It does **not** include:

❌ Training scripts  
❌ Dataset files  
❌ Hyperparameter search code

The focus is **deployment, inference, and evaluation**, not retraining.

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/<your-org>/<repo-name>.git
cd <repo-name>
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the web app
```bash
python app.py
```

Access the interface at:
```
http://localhost:5000
```

---

## 📌 Use Cases

- Multilingual voice assistants
- Cross-lingual NLU systems
- Zero-shot intent recognition
- Smart home and messaging automation
- Rapid prototyping for global NLU products

---

## 📄 Citation

If you use this work, please cite:

```bibtex
@inproceedings{kalasapura2025breaking,
  title={Breaking Language Barriers in NLU: Joint Intent and Slot Recognition with Enhanced XLM-RoBERTa},
  author={Rajarajeswari, S. and Naidu, R. China Appala and Kaveramma, O. K. and Kalasapura, Amogh and Singh, Abhinav and Padmapriya, R. and Bhojwani, Priyanshu and Tiwari, Sourabh and Sharma, Jalaj},
  booktitle={Proceedings of the 16th IEEE International Conference on Computing, Communication and Networking Technologies (ICCCNT)},
  year={2025}
}
```