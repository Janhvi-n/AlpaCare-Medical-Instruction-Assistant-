AlpaCare Medical Instruction Assistant

(A) Project Overview

The AlpaCare Medical Instruction Assistant is a safe, non-diagnostic medical guidance system built using NLP and large language models.
This project fine-tunes a FLAN-T5 Base model on the lavita/AlpaCare-MedInstruct-52k dataset using LoRA/PEFT in a single Google Colab notebook.
It provides educational medical instructions while ensuring ethical and safety compliance.

⚠️ Important: This assistant does not provide diagnoses, prescriptions, or dosages. Every output includes a disclaimer:
“This is educational only — please consult a qualified clinician.”

(B) Architecture & Approach

1. Base Model:

FLAN-T5 Base (250M parameters, <7B limit).

Instruction-tuned and permissive license.

2. Dataset:

lavita/AlpaCare-MedInstruct-52k (52,000 medical instruction-response pairs).

Cleaned, then split: 90% train, 5% validation, 5% test.

3. Fine-tuning Strategy:

LoRA (Low-Rank Adaptation) + PEFT for memory-efficient parameter updates.

Trained for 1 epoch using Hugging Face Trainer.

Adapter saved using PeftModel.save_pretrained().

4. Inference:

Helper function ask(prompt) generates responses with safety disclaimers.

(C) Safety & Ethics:

No diagnoses, prescriptions, or dosages.

Outputs always include a disclaimer.

Notebook and adapter are reproducible privately; no public hosting.

Notebook

All steps are implemented in a single Colab notebook:

AlpaCare_FlanT5_LoRA.ipynb

Install dependencies

Load and preprocess dataset

Load FLAN-T5 base model

Apply LoRA/PEFT

Train for 1 epoch

Save adapter

Run inference using ask(prompt)

Dependencies

Install with pip:

pip install transformers==4.56.2 datasets peft accelerate sentencepiece torch


Enable GPU runtime in Colab for faster training.

(D) Dataset

Name: lavita/AlpaCare-MedInstruct-52k

Source: Hugging Face Dataset

Content: Medical instruction-response pairs.

Processing: Cleaned, formatted, and split into train/validation/test.

How to Run

Open the notebook in Google Colab.

Enable GPU runtime: Runtime → Change runtime type → GPU.

Run cells sequentially:

Install dependencies

Load and process dataset

Load FLAN-T5 model

Apply LoRA

Train model

Save adapter

Run inference

Use ask(prompt) to test model outputs:

response = ask("Explain how to properly use an inhaler.")
print(response)

(F) Expected Outputs
Prompt	Output
What are healthy food options for someone with diabetes?	
Ans: A healthy diet includes vegetables, whole grains, lean proteins. Avoid sugary/processed foods. 
⚠️ This is educational only — consult a qualified clinician.
Explain how to properly use an inhaler.	
Ans: Shake the inhaler, exhale fully, place mouthpiece in mouth, press inhaler, inhale slowly.
⚠️ This is educational only — consult a qualified clinician.
Describe safe hand-washing steps.	
Ans: Wet hands, apply soap, scrub for 20 seconds, rinse, dry with clean towel. 
⚠️ This is educational only — consult a qualified clinician.

(G) License & Ethics

For educational purposes only.

Outputs must not be used as medical advice.

Adapter and notebook are reproducible privately; not publicly hosted.
