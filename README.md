To merge the two README sections into a single cohesive `README.md`, the goal is to organize them under a unified project description with clear subsections for the **dataset** and the **model training** code. Here's how you can structure it:

---

## 🚦 HazardQA & HazardNet: Traffic Scene Understanding Toolkit

This repository contains tools and code for building and fine-tuning models to understand and reason about real-world traffic scenes using images. It includes:

- **HazardQA**: A dataset of visual question-answer pairs derived from annotated traffic images.
- **HazardNet**: A small, vision-language model fine-tuned for traffic safety reasoning, using the Unsloth framework.

---

## 🛑 HazardQA: Visual Traffic Scene Reasoning Dataset

### 📁 Dataset Overview

- **Source**: Raw annotations are located in `data/drama_annotation.json`.
- **Output**: A dataset of 5 QA pairs per image, categorized into reasoning types.

### 🧠 QA Generation Logic

Each QA pair falls under categories such as:
- Object Detection and Recognition
- Spatial Relationships
- Traffic Rules
- Hazards and Risks
- Intent & Behavior Prediction

### 📦 Dependencies

```bash
pip install transformers trl datasets bitsandbytes peft qwen-vl-utils wandb accelerate torch torchvision torchaudio litellm python-dotenv
```

### 🧾 How to Use

1. Place raw data in `data/drama_annotation.json`
2. Run `HazardQA_Reasoning_Dataset.ipynb`
3. Output: structured, labeled VQA dataset

---

## 🔧 Qwen2 Vision Finetuning with Unsloth (HazardNet)

### 🚀 Key Features

- Finetunes vision-language models like Qwen2-VL using [Unsloth](https://github.com/unslothai/unsloth)
- 4-bit model loading for efficiency
- Supports Colab and local GPU setups

### ⚙️ Dependencies

```bash
pip install unsloth bitsandbytes accelerate xformers==0.0.29.post3 \
            peft trl triton cut_cross_entropy unsloth_zoo \
            sentencepiece protobuf datasets huggingface_hub hf_transfer \
            python-dotenv
```

### 🧪 Training Setup

1. Load model (e.g. `unsloth/Llama-3.2-11B-Vision-Instruct-bnb-4bit`)
2. Preprocess data
3. Apply LoRA finetuning
4. Track experiments with W&B (optional)

---

## 📂 Repository Structure

```
HazardQA-HazardNet/
├── data/
│   └── drama_annotation.json
├── HazardQA_Reasoning_Dataset.ipynb
├── qwen2-vision-finetuning-unsloth.ipynb
├── README.md
```

---

## 📚 Citations

If you use this repo, dataset, or model, please cite the following:

**HazardQA Dataset**
```bibtex
@dataset{hazardqa2024,
  title       = {HazardQA: Visual Traffic Scene Reasoning Dataset},
  author      = {Tami3},
  year        = {2024},
  publisher   = {Hugging Face},
  url         = {https://huggingface.co/datasets/Tami3/HazardQA}
}
```

**HazardNet Model**
```bibtex
@misc{abu_tami2025hazardnet,
  title         = {HazardNet: A Small-Scale Vision Language Model for Real-Time Traffic Safety Detection at Edge Devices},
  author        = {Mohammad Abu Tami and Mohammed Elhenawy and Huthaifa I. Ashqar},
  year          = {2025},
  eprint        = {2502.20572},
  archivePrefix = {arXiv},
  primaryClass  = {cs.CV},
  url           = {https://arxiv.org/abs/2502.20572},
  howpublished  = {\url{https://huggingface.co/Tami3/HazardNet}}
}
```