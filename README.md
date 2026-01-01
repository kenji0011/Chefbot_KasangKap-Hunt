# 🧑‍🍳 KaSangkap-Hunt: The Filipino Chefbot

**KaSangkap-Hunt** is a specialized conversational AI fine-tuned to be an expert in Filipino cuisine. Built on the **Mistral-7B** architecture using **Unsloth**, this chatbot can generate authentic recipes, suggest ingredient substitutions, and guide users through cooking techniques with a cultural context.

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Model](https://img.shields.io/badge/Model-Mistral--7B-yellow)
![Fine-Tuning](https://img.shields.io/badge/Library-Unsloth-green)

---

## 📖 Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Dataset](#dataset)
- [How to Run](#how-to-run)
- [Repository Structure](#repository-structure)
- [Training Details](#training-details)
- [Future Improvements](#future-improvements)

---

## 🥘 Overview

Finding authentic, well-structured Filipino recipes can be challenging. Standard LLMs often hallucinate ingredients or provide generic instructions. **KaSangkap-Hunt** solves this by being fine-tuned on a curated dataset of over 10,000 Filipino recipes. It is designed to understand the nuances of Filipino cooking, from *Sinigang* to *Adobo*, and can handle complex queries like ingredient substitutions based on flavor profiles.

---

## ✨ Key Features

*   **Recipe Generation:** Generates detailed ingredients and step-by-step instructions for classic Filipino dishes.
*   **Intelligent Substitutions:** Understands context to suggest valid alternatives (e.g., suggesting *oxtail* or *beef* as a substitute for *pork* in Kare-Kare).
*   **Persona Adaptation:** Can modify its tone to explain recipes simply for beginners or provide technical details for advanced cooks.
*   **Contextual Awareness:** Can answer questions about cooking times, preparation methods, and ingredient characteristics.
*   **User-Friendly Interface:** Integrated with a chat-style UI (Gradio) for easy interaction.

---

## 🛠️ Tech Stack

*   **Core Framework:** PyTorch
*   **Base Model:** `unsloth/mistral-7b-instruct-v0.3-bnb-4bit` (Quantized for efficiency)
*   **Fine-Tuning:** PEFT (Parameter-Efficient Fine-Tuning) with LoRA (Low-Rank Adaptation) via the **Unsloth** library.
*   **Interface:** Gradio
*   **Data Processing:** Pandas, Datasets (Hugging Face)
*   **Environment:** Google Colab (T4 GPU)

---

## 📊 Dataset

The model was trained on the `filipino_recipes.csv` dataset, which contains:
*   **Recipe Names**
*   **Ingredients Lists** (Parsed and cleaned)
*   **Step-by-Step Instructions**
*   **Cooking Times**

*Data Augmentation:* The dataset was enhanced by generating synthetic Q&A pairs to train the model on specific tasks, such as handling ingredient substitutions and answering specific cooking queries.

---

## 🚀 How to Run

Since the model requires a GPU to run efficiently, it is best executed within Google Colab.

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/Chefbot_KasangKap-Hunt.git
    ```

2.  **Open the Notebook:**
    Upload `Chefbot_V3.ipynb` to Google Colab.

3.  **Setup Environment:**
    *   Upload the `data/filipino_recipes.csv` to your Google Drive.
    *   Ensure the notebook path points to your Drive directory.

4.  **Run the Cells:**
    *   Execute the setup cells to install dependencies (`unsloth`, `trl`, `peft`).
    *   Run the **Inference** section to load the fine-tuned adapter.
    *   Run the **Gradio** cell to launch the web interface.

---

## 📂 Repository Structure

```text
Chefbot_KasangKap-Hunt/
├── data/
│   └── filipino_recipes.csv      # The raw dataset used for training
├── documentation/
│   └── Project_Documentation.docx # Full documentation and reports
├── Chefbot_V3.ipynb              # The main Jupyter notebook (Training + Inference)
└── README.md                     # Project overview (this file)
```


**Training Details**
The model underwent iterative training to improve performance:
Initial Training (1200 Steps): Established basic recipe knowledge.
Evaluation: Identified weaknesses in substitution logic (e.g., hallucinating placeholders).
Data Refinement: The data generation script was updated to provide explicit, high-quality substitution examples.
Final Training (3400 Steps): Retrained on the improved dataset, resulting in a highly capable model with low evaluation loss.

**Future Improvements**
Expand Dataset: Incorporate more regional dishes (e.g., Ilocano, Bicolano specific recipes).
Web Search Integration: Connect the bot to the internet to fetch real-time pricing or availability of ingredients.
Image Recognition: Allow users to upload a picture of ingredients, and the bot suggests a recipe.
