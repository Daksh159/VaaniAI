

# 🎙️ VaaniAI : Hindi ASR Pipeline — Whisper Fine-tuning

> Fine-tuned OpenAI Whisper-small on real-world Hindi conversational audio,  
> achieving **67.8% WER reduction** (1.25 → 0.40) across 102 speakers.

---

## 📌 Project Overview

Built as part of an AI Researcher Intern assignment at **Josh Talks**, this project covers
an end-to-end Hindi ASR pipeline — from noisy raw audio to fine-tuned model evaluation,
text cleaning, spelling correction, and lattice-based fair evaluation.

---

## 📊 Results Summary

| Task | Result |
|------|--------|
| Baseline WER (Whisper-small) | 1.2537 |
| Fine-tuned WER | 0.4028 |
| WER Improvement | ↓ **67.8%** |
| Post-processing improvement | ↓ additional **27.7%** |
| Spelling classifier accuracy | **82.5%** (low-confidence set) |

---

## 🗂️ Dataset

- **104 Hindi audio recordings** from real speakers across India
- **11.44 hours**, **102 unique speakers**
- Cleaned from 5,941 → **4,442 segments** after quality filtering
- Resampled from 44.1kHz → 16kHz for Whisper compatibility

---

## 🏗️ Pipeline Components

### Q1 — Whisper Fine-tuning
- Model: `openai/whisper-small` (241.7M parameters)
- Hardware: Kaggle T4 GPU (14.6 GB)
- Training: 3 epochs, LR 1e-5, effective batch size 32 (FP16)
- Challenges solved: OOM errors, Transformers v5 compatibility bug

### Q2 — Text Cleaning
- Hindi word-to-digit converter with idiom protection
- Devanagari English loanword tagger (80+ words)

### Q3 — Spelling Correction
- 3-layer rule-based classifier over **1,77,508 unique words**
- Layers: hard rules → morphological rules → Devanagari validity

### Q4 — Lattice-Based WER Evaluation
- Multi-alternative bin-based evaluation framework
- Fairly scores numerically/semantically equivalent transcriptions

---

## 🛠️ Tech Stack

`Python` `HuggingFace Transformers` `PyTorch` `Whisper` `librosa` `Kaggle T4 GPU`

---