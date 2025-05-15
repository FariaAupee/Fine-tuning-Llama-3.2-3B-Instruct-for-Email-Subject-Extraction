# 🦙 Fine-Tuning LLaMA 3 for Email Subject Extraction

This project fine-tunes the **LLaMA 3.2B Instruct** model on the [`Enron Email Dataset`](https://www.kaggle.com/datasets/thedevastator/uncovering-enron-employees-secrets-exploring-the) dataset to extract email subjects directly from the body content. It demonstrates a practical use of LLMs for structured information extraction from unstructured text.

## 🔍 Problem Statement

In many enterprise and user-level applications, email subjects are either missing, poorly written, or non-informative. Extracting or generating a relevant subject line from the email body can:
- Improve email searchability and categorization
- Enhance summarization for threads
- Enable better NLP-driven email automation

## 💡 Key Features

- Supervised fine-tuning of LLaMA 3 Instruct (3B) using Hugging Face `transformers`
- Utilization of LoRA (Low-Rank Adaptation) for efficient training
- Evaluation and generation of subject lines using test samples

## 📂 Dataset

The dataset used is the [Enron Email Dataset](https://www.kaggle.com/datasets/thedevastator/uncovering-enron-employees-secrets-exploring-the), a public collection of internal emails from Enron Corporation.

For this project:
- Only the `body` and `subject` fields were extracted.
- The dataset was cleaned and formatted into input-output pairs.

## 🧠 Model & Approach

- **Base Model:** [Meta-Llama-3-8B-Instruct](https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct)
- **Task:** Generate the subject of an email based on its body.
- **Methodology:** Supervised fine-tuning using Hugging Face’s `transformers` and `accelerate` libraries.

Training was done on a Colab environment using a sequence-to-sequence setup.

## 🛠️ Environment & Dependencies
- Python 3.10+

- PyTorch 2.x

- transformers >= 4.38

- accelerate

- peft (for LoRA support)

- datasets

- trl (for training utilities)

- bitsandbytes (for 4-bit quantization)

## 🚀 Training
The training pipeline uses the trl, Hugging Face transformers and peft libraries. The notebook:

- Loads and preprocesses the dataset

- Tokenizes inputs and labels

- Applies LoRA to the LLaMA 3 model

- Fine-tunes the model using SFTTrainer

- Evaluates the model and generates subject lines

- Key parameters used:

- Model: meta-llama/Meta-Llama-3-8B-Instruct or smaller 3B variant

- Sequence Length: 512 tokens

- Training Epochs: 3

- Batch Size: 2 (adjust based on GPU memory)

## ✨ Results
The fine-tuned model successfully generates concise and relevant subject lines for unseen email bodies. It can be integrated into email automation pipelines, CRM tools, or chatbots.

- Example:

  Input Body:

  As required by the Houston Fire Department, a fire drill has been scheduled for the Enron Center Campus.

  Generated Subject: 

  Enron Center Campus Fire Drill - Thursday, December 20th, 2001  	3:15 PM and 3:45 PM

  Actual Subject:

  Fire Drill Scheduled

## 🙌 Acknowledgements
[Meta](https://ai.meta.com/) for releasing LLaMA 3

[Hugging Face](https://huggingface.co/) for datasets, model hub, and fine-tuning tools

[Enron Email Dataset](https://www.kaggle.com/datasets/thedevastator/uncovering-enron-employees-secrets-exploring-the) for the dataset
