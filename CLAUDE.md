# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a GPT (Generative Pre-trained Transformer) implementation following Andrej Karpathy's [Zero To Hero](https://karpathy.ai/zero-to-hero.html) video tutorial. The implementation is a character-level language model trained on the tiny Shakespeare dataset.

## Working with the Notebook

This is a Jupyter notebook (`gpt_dev.ipynb`). To work with it:

```bash
# Install dependencies (if needed)
pip install torch jupyter

# Start Jupyter
jupyter notebook gpt_dev.ipynb

# Or use Jupyter Lab
jupyter lab gpt_dev.ipynb
```

The notebook can also be executed using VSCode's Jupyter extension or other notebook environments.

## Architecture

The implementation progresses through several stages:

1. **Simple Bigram Model** (cells 13-16): Basic token embedding lookup table
2. **Self-Attention Mechanism** (cells 18-24): Demonstrates the mathematical foundation of attention
3. **Full Transformer Model** (cell 37): Complete implementation with:
   - Token and positional embeddings
   - Multi-head self-attention
   - Feed-forward networks
   - Layer normalization
   - Residual connections

### Key Components

- **BigramLanguageModel**: The main model class containing the full transformer architecture
- **Head**: Single attention head implementation
- **MultiHeadAttention**: Parallel attention heads
- **FeedForward**: MLP layer after attention
- **Block**: Complete transformer block (attention + feedforward with residual connections)

## Training Configuration

Default hyperparameters (cell 37):
- `batch_size = 16`
- `block_size = 32` (context length)
- `max_iters = 5000`
- `learning_rate = 1e-3`
- `n_embd = 64` (embedding dimension)
- `n_head = 4` (number of attention heads)
- `n_layer = 4` (number of transformer blocks)
- `dropout = 0.0`

The model trains on 90% of the data, with 10% held out for validation.

## Data

The notebook downloads `input.txt` (tiny Shakespeare dataset) automatically from the karpathy/char-rnn repository. The model uses character-level tokenization with a vocabulary of 65 characters.

## Text Generation

To generate text from a trained model, the `generate()` method samples autoregressively:

```python
context = torch.zeros((1, 1), dtype=torch.long, device=device)
generated = model.generate(context, max_new_tokens=500)
print(decode(generated[0].tolist()))
```

## Notes

- The model uses decoder-only transformer architecture (causal/autoregressive attention)
- Attention is masked with a lower triangular matrix to prevent looking ahead
- The scaling factor `head_size**-0.5` in attention prevents softmax saturation
- Device automatically switches to CUDA if available, otherwise uses CPU
