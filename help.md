# LoRA Fine-tuning and Evaluation

Tools for fine-tuning and testing language models with LoRA.

## Setup

- Python 3.x
- PyTorch
- GPU (recommended)
- MLflow (optional)


## What's Here

- `LoRA.ipynb` - Fine-tuning notebook
- `evaluate.ipynb` - Testing notebook
- `lora_trained_adapters/` - Saved models
- `csv_frames/` - Test data
- `cache/` - Cache files

## How to Use

1. Fine-tuning:
   - Open `LoRA.ipynb`
   - Pick your model
   - Set training options
   - Run and save

2. Testing:
   - Open `evaluate.ipynb`
   - Load your model
   - Run tests
   - Check results

## What LoRA Does

- Uses 8-bit quantization to save memory
- Fine-tunes only key parts of the model:
  - Query projections (q_proj)
  - Value projections (v_proj)
- Default settings:
  - Rank: 8
  - Alpha: 42
  - Dropout: 0.05

## Evaluation

- Tests model responses with:
  - Temperature: 0.7 (creativity)
  - Top-p: 0.95 (diversity)
  - Max length: 500 tokens
- Saves responses for comparison
- Supports multiple models:
   - deepseek-ai/deepseek-llm-7b-base
   - mistralai/Mistral-7B-Instruct-v0.3
   - meta-llama/Llama-3.1-8B-Instruct
   - microsoft/phi-2

## Tools
- MLflow: Track experiments and metrics
- FAISS: Fast similarity search (TBD)

## Issues
- Out of memory? Try smaller batch size
- Training stuck? Check learning rate
- Slow? Enable 8-bit mode
- Errors? Check data format
