# BPE Tokenization for LLMs

This notebook demonstrates building a **Byte Pair Encoding (BPE)** tokenizer from scratch, training it on a large-scale Hindi Wikipedia corpus, and testing its functionality for efficient tokenization and reconstruction tasks. It is suitable for learning and experimentation with custom tokenizer logic, especially for low-resource languages.

## Table of Contents

- [Dataset Download](#dataset-download)
- [BPE Algorithm Description](#bpe-algorithm-description)
- [BPE Algorithm Implementation](#bpe-algorithm-implementation)
- [Tokenizer Training](#tokenizer-training)
- [Encoding & Decoding Functions](#encoding-decoding-functions)
- [Training & Testing](#training-testing)
- [Saving the Tokenizer](#saving-the-tokenizer)
- [Results & Observations](#results-observations)
- [Demo: Test the Tokenizer Online](#demo-test-the-tokenizer-online)

## Dataset Download

The notebook utilizes Hugging Face's `datasets` library to download the **Wikipedia Hindi dataset** (`wikimedia/wikipedia`, version `20231101.hi`). This provides a modern Hindi text corpus, useful for building subword vocabularies.

## BPE Algorithm Description

**Byte Pair Encoding (BPE)** is a subword tokenization technique commonly used in NLP tasks for efficient vocabulary creation and handling of out-of-vocabulary words.

**How BPE Works:**
- The algorithm starts with text split into individual characters (or bytes).
- It then repeatedly finds the most frequent adjacent pair of symbols (bytes, characters, or tokens) in the data.
- This pair is merged into a single new symbol and replaced throughout the corpus.
- The process is repeated until a target vocabulary size or specified number of merges is achieved.
- The result: frequent multi-character patterns are merged together, helping capture common word stems, suffixes, and even full words, which improves compression and handles rare words gracefully.

## BPE Algorithm Implementation

Implements a **simplified Byte Pair Encoding (BPE)** method for tokenizer training.

## Tokenizer Training

Text is preprocessed and BPE merges are performed until the specified vocabulary size is reached.

## Encoding & Decoding Functions

- **encode(text):** Converts input text into a sequence of token IDs.
- **decode(ids):** Reconstructs the original text from token IDs via the vocab mapping.

## Training & Testing

- Trains the tokenizer on the first 100,000 characters for computational efficiency.
- Reports key stats, validates encode-decode, and demonstrates compression.

## Saving the Tokenizer

- Serializes `vocab` and `merges` for external usage.
- Saves to `vocab.json` and `merges.json`.

## Results & Observations

- Typical compression ratios >6x (bytes/tokens)
- Final vocab size is configurable
- Fully reversible encode/decode

***

## Demo: Test the Tokenizer Online

**You can interactively test the trained tokenizer at this Hugging Face Spaces app:**  
👉 [https://huggingface.co/spaces/saneshashank/hindi_bpe_tokenizer](https://huggingface.co/spaces/saneshashank/hindi_bpe_tokenizer)

- Paste Hindi sentences and observe encoding/decoding and token segmentation live.

***

## How to Use

1. **Run cells sequentially** for dataset download, tokenizer definition, BPE training, and testing.
2. **Modify settings** (like dataset or vocab size) as needed.
3. **Export tokenizer artifacts** to use in custom projects or the provided online demo.

***

## Dependencies

- Python 3
- `datasets` (Hugging Face)
- `tqdm`

***

## References

- [Hugging Face Datasets Documentation](https://huggingface.co/docs/datasets)
- [Byte Pair Encoding for NLP](https://www.aclweb.org/anthology/P16-1162/)
- [Subword Tokenization Algorithms](https://arxiv.org/abs/1508.07909)

***

**Author:**  
Shashank Sane

**Date:**  
November 2025

---

[1](https://colab.research.google.com/drive/14AiyfhDvTeUyvpi-5GJ6NBSRym6Yug99#scrollTo=wn-9hsgzbmw5)
