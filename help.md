# Language Model Evaluation Notebook

This repository contains a Jupyter notebook for evaluating and comparing different language models using LoRA fine-tuning and human evaluation.

## Prerequisites

Before running the notebook, ensure you have the following installed:
- Python 3.x
- PyTorch
- CUDA-compatible GPU (recommended)
- Required Python packages (install using pip):
  ```bash
  pip install transformers
  pip install -U bitsandbytes
  pip install safetensors
  pip install peft
  ```

## Available Models

The notebook supports the following models:
- deepseek-ai/deepseek-llm-7b-base
- mistralai/Mistral-7B-Instruct-v0.3
- meta-llama/Llama-3.1-8B-Instruct
- microsoft/phi-2

## Usage Instructions

1. **Model Selection and Import**
   - Open the notebook and select your desired model from the `models` list
   - The notebook will automatically download and set up the model with 8-bit quantization

2. **LoRA Configuration**
   - The notebook uses LoRA (Low-Rank Adaptation) for efficient fine-tuning
   - Default configuration:
     - Rank (r): 8
     - LoRA alpha: 42
     - Target modules: q_proj, v_proj
     - Dropout: 0.05
   - You can modify these parameters in the `lora_training` function

3. **Loading Custom Adapters**
   - If you have a pre-trained adapter, specify its path in the `load_adapter` function
   - Example: `model.load_adapter("path/to/your/adapter", adapter_name="custom")`

4. **Generating Responses**
   - Use the `gen` function to generate responses from the model
   - Parameters:
     - max_length: 500 (maximum response length)
     - temperature: 0.7 (controls randomness)
     - top_p: 0.95 (nucleus sampling)
   - Example usage:
     ```python
     response = gen("Your question here", model, tokenizer)
     ```

## Evaluation Process

1. **Prepare Evaluation Questions**
   - Create a list of diverse questions to test the model's capabilities
   - Include questions that test different aspects (reasoning, knowledge, creativity)

2. **Generate Responses**
   - Use the `gen` function to get responses for each question
   - Save the responses for comparison

3. **Human Evaluation**
   - Compare responses from different models
   - Evaluate based on:
     - Accuracy
     - Relevance
     - Coherence
     - Completeness
     - Response length

## Tips for Better Evaluation

1. **Consistent Prompting**
   - Use the same prompt format for all models
   - Keep questions clear and specific

2. **Response Analysis**
   - Compare responses side by side
   - Note any patterns or consistent differences between models

3. **Resource Management**
   - The notebook uses 8-bit quantization to reduce memory usage
   - Monitor GPU memory usage during evaluation

## Troubleshooting

- If you encounter memory issues, try reducing the model size or batch size
- For tokenizer errors, ensure the pad_token is properly set
- If the model fails to load, check your internet connection and available disk space
