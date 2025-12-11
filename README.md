## Part A: Full Finetuning with a small model
I have fine-tune a variety of open-weight LLMs using Unsloth AI for different specialized tasks:

- **Llama 3.1 (8B)** – Code generation & debugging assistant  
  📄 [Colab Notebook](https://drive.google.com/file/d/1dY0nmvW5cqDh9iT8q_y8zG_0VT10KaqO/view?usp=sharing)  
- **Mistral NeMo (12B)** – Customer-support chat agent  
  📄 [Colab Notebook](https://drive.google.com/file/d/1I-Axx7zxIjbhxY4_btgTXZt9NpnnLfCe/view?usp=sharing)  
- **Gemma 2 (9B)** – Human-like conversational AI  
  📄 [Colab Notebook](https://drive.google.com/file/d/1DBtPX4Jvc2sI_76sn3z1J4ZoURhyCdPG/view?usp=sharing)  
- **Phi-3 (medium)** – Math-based reasoning & problem solving  
  📄 [Colab Notebook](https://drive.google.com/file/d/13GHh5p_3D-o_M2EJ4SYgh28_la16ownR/view?usp=sharing)  

## Part B: Continued Pretraining on LORA parameter(smollm-135m)
- **Purpose:** Adapt to handle Hindi text by unsupervised continuation of its language model pretraining.  
- 📄 [Open in Colab](https://colab.research.google.com/drive/10eHHGvOuqaWK_RHngdQEYyPS4Bjg41OJ?usp=sharing)

---
## Part C: Reinforcement Learning with Preference Data (DPO)
- **Model:** SmolLM2‑135M  
- 📄 [Open in Colab](https://colab.research.google.com/drive/1EVHl7NZfvc0Hv2kl1bZ7ZDnbEY2F2LI6?usp=sharing)

Fine-tune **SmolLM2‑135M** with **Direct Preference Optimization (DPO)** on a small math preference dataset containing `prompt`, `chosen`, and `rejected` answers. LoRA adapters (rank 16) are attached to attention and MLP layers, and `trl.DPOTrainer` is used with a tiny preference set so it runs comfortably on a single T4 GPU. The resulting LoRA checkpoint (e.g., `smollm2-135m-dpo-math`) teaches the model to prefer correct, well‑structured math solutions over incorrect ones.

---

## Part D: Reinforcement Learning with GRPO
- **Model:** SmolLM2‑135M  
- 📄 [Open in Colab](https://colab.research.google.com/drive/1_EcYElIFDKWLX_fh7tntUTRzadF2K1Ly?usp=sharing)

- Train **SmolLM2‑135M** on **GSM8K** using **GRPO (Group Relative Policy Optimization)** with a simple reward function: +1 if the final numeric answer matches the gold answer, 0 otherwise, plus a small penalty for overly long completions. The model is loaded in 4‑bit, patched for GRPO, and fine‑tuned with multiple generations per prompt. The trained GRPO LoRA adapter (`SmolLM2-135M-GRPO-GSM8K`) improves step‑by‑step math reasoning accuracy.

---

## Part E: Continued Pretraining from Checkpoint
- **Model:** SmolLM2‑135M  
- 📄 [Open in Colab](https://colab.research.google.com/drive/14FOvUsyf25rq5MloOuJqjSkaJFcWumPm?usp=sharing)

- Continue pretraining `unsloth/smollm2-135m` on a small monolingual corpus any language using a simple `text` column dataset. The model is trained with full‑parameter updates (not just LoRA) using an LM objective with packing and `max_seq_length ≈ 512`. The new checkpoint (e.g., `SmolLM2-135M-ContinuedPretraining-<Language>`) shows improved fluency and style control in the target language.

---

## Part F: Mental-Health Support Chatbot  
**Model:** Phi-3 Mini  
- **Scope:** Fine-tune for empathetic, safe mental-health conversations, including dataset sourcing and safety filtering.  
- 📄 [Open in Colab](https://drive.google.com/file/d/1q1-I7Gg5JXCtd7-9PAbGfBmNdBZZ9xWu/view?usp=sharing)

---

## Part G: Export & Inference with Ollama  
**Model:** Llama 3  
- **Goal:** Convert your LoRA adapter into a GGUF format and run live inference via Ollama.  
- 📄 [Open in Colab](https://drive.google.com/file/d/1OHtx8wDypC_pJb5RoWIsjruUq5acv0Tb/view?usp=sharing)

---

YouTube Demo explaning Youtube : 
