# Browser Transformer: GGUF + Text Generation

**A complete vanilla JavaScript implementation of a GPT-2 transformer, running entirely in your browser. No server, no Python, no frameworks, no WebGPU—just HTML + JS.**

---

## What is This?

This project is a full end-to-end transformer model (**GPT-2**) executed in your browser, using real pre-trained weights directly from `*.gguf` files with real tokenizers. It requires **no external dependencies or special hardware**. Everything—tensor parsing, attention, feed-forward, autoregressive text generation—is performed in pure JS.

- **Loads and parses GGUF files (all tensors, including all layers, attention, FFN, etc.)**
- **Loads a compatible tokenizer (`tokenizer.json` from HuggingFace/LLM)** 
- **Full tokenization, generation, and decoding pipeline**
- **Outputs true GPT-2 completions, in the browser, at interactive speed**

---

## Live Demo

Just open `index.html` in your browser. No server is required.

---

## What Files Do I Need?

You need **2 files**:

1. **A GPT-2 model in GGUF format (f32 recommended for simplicity)**  
   - Example: `gpt2-f32.gguf` or any transformer model `*.gguf` with similar or smaller size.
   - Must be unquantized/f32 if you want compatibility (quantized formats may not be fully supported out of the box).
   - [Get GPT-2 f32 GGUF weights](https://huggingface.co/ddh0/GPT-2-GGUF/resolve/main/GPT-2-f32.gguf) 

2. **Accompanying tokenizer.json**  
   - Download the `tokenizer.json` file that matches your model, usually from the HuggingFace repo.
   - For GPT-2, get [`tokenizer.json`](https://huggingface.co/openai-community/gpt2/blob/main/tokenizer.json).

**You must have both the GGUF model file and a compatible tokenizer.**

---

## How To Use

1. **Clone or download this repo.**
2. Open `index.html` in your desktop browser (Chrome or Firefox recommended).
3. **Step 1: Upload your GGUF model file** (e.g., `gpt2-f32.gguf`).  
   - You will see all model tensors/weights listed if loading is successful.
4. **Step 2: Upload the tokenizer JSON file** (`tokenizer.json` from the same model family).
   - You'll see a message confirming the tokenizer loaded.
5. **Step 3: Enter a prompt and generate text!**
   - Enter your prompt (e.g., _Once upon a time_) and click "Generate Text".
   - Watch your browser run real transformer inference!

---

## What Models Work?

- **Any GPT-2 (124M, 355M, etc) exported to GGUF format (F32) and using standard vocabulary.**
- Some other models of similar architecture and size, as long as tensor names/shapes match (PRs welcome for more).
- For large models: browser RAM and patience limit size; stick to smaller models for now.

**Note:** Only unquantized/f32 weights are (fully) supported out of the box. Some quantizations (Q4, Q8, etc) may need extension.

---

## Features

- **Full GGUF parser and tensor extractor (read any GGUF tensor!)**
- **All model weights: attention, FFN, layernorm, embeddings, output head**
- **Load and use tokenizer in browser**
- **Full transformer math (multi-head attention, feed-forward, etc)**
- **No WASM, no WebGPU, no server—just browser JS**
- **Interactive playground for custom vector input**

---

## Limitations

- May be **slow** (~20 seconds for 5 new tokens on large models), but runs deterministically and in real-time with real GPT-2 weights.
- Large GGUF models may cause browser tabs to crash due to RAM limits.
- Only tested on Chromium and Firefox.
- Only F32 is natively supported (quantized support possible but not default).

---

## Credits

- [GGUF format](https://github.com/ggerganov/llama.cpp/blob/master/docs/gguf.md)
- [GPT-2 weights](https://huggingface.co/openai-community/gpt2)
- Tokenizer and model concept based on OpenAI/HuggingFace

---

## Why Is This Cool?

- **First demonstration** (as of 2025) of *full GPT-2 inference* in the browser with *real weights* using *no dependencies*.
- Completely transparent transformer math. Hack, modify, and learn!
- Shows what’s possible with just HTML + JavaScript and some clever engineering.

---

## License

MIT

---

## Questions or Want to Help?

Open an Issue or PR!  
For more info or to collaborate, contact [Matthew James Abbott](https://github.com/matthewJamesAbbott).

## Vercel Link
(https://javascript-transformer.vercel.app/)
