# Radiology Segmentation Prompt Generator

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)

## Project Overview

This project generates segmentation prompts for radiology tasks based on clinical notes. Given a clinical note, the system produces structured prompts to assist segmentation in medical imaging.

---

## Dataset

- Synthetic clinical notes with paired segmentation prompts generated via ChatGPT.  
- Columns: `id`, `note`, `organ`, `diagnosis`, `stage`, `prompt`.  
- For demo purposes only; not for clinical use.

---

## Techniques Explored

### 1. Fine-tuning FLAN-T5

- Fine-tuned a text-to-text model to generate prompts directly from notes.  
- Limited success due to small dataset; outputs often generic or incomplete.

### 2. Retrieval-Augmented Generation (RAG)

- Encoded notes using `all-MiniLM-L6-v2` sentence embeddings.  
- Used cosine similarity to retrieve closest prompts from dataset.  
- Delivered reliable results without extensive training.

---

## Comparison of Approaches

| Technique                | Dataset Size Requirement | Training Time | Performance on Small Data | Complexity | Suitability for This Project       |
|--------------------------|--------------------------|---------------|---------------------------|------------|-----------------------------------|
| Fine-tuning FLAN-T5      | Large                    | High          | Poor                      | High       | Not ideal due to limited data      |
| Retrieval-Augmented Gen. | Small to Medium          | Low           | Good                      | Medium     | Practical, effective for this use  |

---

## What I Learned

- Fine-tuning large language models demands substantial, diverse datasets to achieve quality output.  
- Retrieval-based methods using embeddings and similarity search provide a strong baseline for small datasets without complex training.  
- Working with biomedical text requires careful dataset preparation and clear prompt design to guide models effectively.  
- Practical implementation challenges include managing tensor vs numpy data types and Hugging Face’s tokenization intricacies.  
- Experimentation and flexibility are crucial—switching methods when one doesn’t fit is part of research and engineering.

---

## Requirements

- Python 3.8+  
- transformers  
- sentence-transformers  
- datasets  
- scikit-learn  
- huggingface_hub

Install dependencies with:

```bash
pip install -r requirements.txt
