
# 📊 Local LLM Test Results Repository  

This repository is a **collection of reproducible benchmark results for a wide range of locally‑run large language models (LLMs)**. It was created to give developers, researchers, and hobbyists a clear picture of how different models behave on the same hardware and prompts, without relying on cloud services.

## What you’ll find here  

| Section | Contents | Highlights |
|---|---|---|
| **Model performance tables** | Detailed timing, token‑rate, and prompt‑/eval statistics for each model (e.g., DeepSeek‑Coder‑V2, Granite 3.2, LLaVA, Qwen 3‑VL, Gemma 3, Llama 3.2‑vision). | Shows GPU vs CPU split, model size, and raw benchmark numbers |
| **Coding benchmark suite** | “Write a JavaScript function to remove a specific JSON element” test run on models from ~8 GB up to ~120 GB. | Includes success/failure flags and sample code snippets for each model |
| **Vision‑LLM OCR tests** | OCR output from image‑aware models on a map of Ilam Park. | Demonstrates the text‑extraction capabilities of Gemma 3, LLaVA, Qwen 3‑VL, and Llama 3.2‑vision |
| **System‑level comparisons** | Example of running the same prompt on Windows 11 vs. WSL (Ubuntu 24.04) with DeepSeek‑R1. | Provides raw timing data to illustrate environment impact |
| **Setup & reproducibility** | Exact command‑line invocations (e.g., `ollama run deepseek-r1:32b --verbose`), hardware specs, and a note that every test was performed on a **fresh model load with no prior context**. | Guarantees that numbers are comparable across runs |

## Why this matters  

- **Transparency** – All raw numbers, prompts, and model versions are stored in plain markdown tables, so you can verify or extend the data yourself.  
- **Local‑first** – No API keys or remote inference; everything runs on your own machine (or VM).  
- **Model‑agnostic** – The suite works with any Ollama‑compatible model, from 8 GB quantised builds up to 120 GB instruction‑tuned giants.  

## Discussions  

[Local LLM tests](https://github.com/donatas-xyz/AI/discussions/1)

All tests were performed on a clean model load with the default Ollama settings, ensuring a fair baseline for comparison.

---

*Happy benchmarking!*
