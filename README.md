

# Assigment 1: NanoGPT 

## Assignment 1 (10%): NanoGPT Experimentation

**Introduce:** Week 3 (1/26)

**Deadline:** Week 5 (2/9 11:59 PM)

**Format:** Submit a short report (PDF or Markdown). Code submission is optional; **outputs + analysis are required**.

This assignment uses a minimal GPT implementation (based on Andrej Karpathy’s TinyGPT) to understand how training steps, dataset choice, and tokenization affect generated text.

**Before you start:** Watch Karpathy’s video: https://youtu.be/kCc8FmEb1nY

---

### Required Environment (Important)

You must run experiments on **Google Colab with GPU**.

- Colab menu: **Runtime → Change runtime type → T4 GPU (or other GPUs)**
- If you run on CPU, training will be extremely slow.

---

## What to Submit (for *every* section)

For each section (1–4), your report must include:

1. **Output** (generated text) pasted in a **code block** (monospace font), like:

```
PASTE YOUR GENERATED TEXT HERE
```

1. **Short analysis** (3–6 sentences):
    - What changed?
    - What patterns improved/worsened?
    - Why do you think that happened?

---

## 1. Baseline: Run TinyGPT (1 Point)

**Task**

- Run the **unmodified** TinyGPT code in Colab (default dataset + default tokenizer).
- Generate text once training finishes (or at the end of the notebook).

**Report**

- Paste **one sample output** in a code block.
- Write a brief analysis (3–6 sentences).

---

## 2. Change Training Iterations (2 Points)

**Goal:** Understand how training duration affects output quality.

**Task**

- Keep everything the same as baseline (same dataset, same tokenizer, same model).
- Change **`max_iters`** to the following values and run training each time:
    - `max_iters = 100`
    - `max_iters = 300`
    - `max_iters = 1000`

**Report**

- Paste **three outputs** (one per `max_iters`) as separate code blocks.
- Write a short analysis comparing:
    - “100 vs 300 vs 1000”: what improved, what still fails, and why.

---

## 3. Change the Dataset (3 Points)

**Goal:** See how training data changes style and vocabulary.

**Task**

- Replace the training text with a different dataset.
- You may use the class dataset:
    - Harry Potter text:
        
        https://ryosuzuki.github.io/lecture-demo/sample-data/harry-potter.txt
        
    
    (Or you may use another dataset, but include the link/source.)
    
- Train with:
    - `max_iters = 1000`

**Report**

- Paste **one output** sample in a code block.
- Write a short analysis explaining:
    - How the style differs from Shakespeare baseline
    - Why the dataset causes that change

---

## 4. Switch Tokenizer to Tiktoken  (4 Points)

**Goal:** Compare character-level tokenization vs BPE tokenization.

**Task**

- Modify the code to use **tiktoken (BPE tokenizer)** .
- Using the original dataset (Tiny Shakespeare) or your own dataset from the question 3, run training with:
    - `max_iters = 100`
    - `max_iters = 300`
    - `max_iters = 1000`

**Report**

- Paste **three outputs** (100 / 300 / 1000) as separate code blocks.
- Write a short analysis comparing:
    - BPE vs char-level at the same iteration counts
    - Why BPE might produce more readable outputs earlier
    - Any failure modes (e.g., repetition like “the the the…”)

**Hint**

Use tiktoken python library https://github.com/openai/tiktoken/tree/main

```jsx
import tiktoken
```

This code block (`encode` and `decode` functions) is the part that does the character tokenization in the original code, so you should modify this with tiktoken. 

```python
# here are all the unique characters that occur in this text
chars = sorted(list(set(text)))
vocab_size = len(chars)
# create a mapping from characters to integers
stoi = { ch:i for i,ch in enumerate(chars) }
itos = { i:ch for i,ch in enumerate(chars) }
encode = lambda s: [stoi[c] for c in s] # encoder: take a string, output a list of integers
decode = lambda l: ''.join([itos[i] for i in l]) # decoder: take a list of integers, output a string
```

to something like this, for example. 

```python
def encode(s: str):
		return # insert tiktoken encode
		
def decode(ids):
```