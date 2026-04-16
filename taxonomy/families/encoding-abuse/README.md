# Encoding Abuse Family

## Definition

The Encoding Abuse family encompasses mechanisms that manipulate how instructions are represented or structured rather than altering wording. These attacks exploit ambiguities and vulnerabilities in decoding, tokenization, normalization, and structural parsing: the layers that transform raw input text into the semantic representations that safety mechanisms operate on. By obscuring harmful instructions through encoding schemes or structural wrapping, these attacks make it difficult for safety classifiers to detect the intent while remaining interpretable to the underlying language model.

**Family Prevalence: 20.35%**

## Splitting Rule

The Encoding Abuse family is subdivided based on the layer of abstraction at which obfuscation is applied. **Encoding & Unicode Tricks** apply obfuscation at the character and encoding layer, using techniques like Base64 encoding, URL encoding, ASCII manipulation, and Unicode exploits to obscure text at the lowest representational level. **Wrappers & Schemas**, by contrast, apply obfuscation through higher-level structural containers (JSON objects, Markdown blocks, code snippets, and prefix-suffix wrapping) that change how the instruction is parsed without modifying the underlying character representation.

## Categories and Leaves

| Category | Leaf | Prevalence | Description |
|----------|------|-----------|-------------|
| Encoding & Unicode Tricks | ASCII Encoding | 2.65% | Conversion of harmful text to ASCII-encoded formats (e.g., decimal or hexadecimal representations) that require decoding before interpretation. |
| Encoding & Unicode Tricks | Base64 / URL / Obfuscation | 8.85% | Encoding harmful instructions using Base64, URL encoding, or other standard obfuscation schemes to evade text-based safety detection. |
| Encoding & Unicode Tricks | Unicode / Bidi / Zero-Width | 1.77% | Exploitation of Unicode properties, bidirectional text rendering, or zero-width characters to hide or misrepresent the semantic meaning of instructions. |
| Wrappers & Schemas | JSON / Markdown / Code-Blocks | 4.42% | Embedding harmful instructions within structured formats (JSON objects, Markdown code blocks, XML) that may bypass safety mechanisms through structural parsing ambiguities. |
| Wrappers & Schemas | Length / Prefix-Suffix Wrappers | 2.65% | Wrapping harmful text with benign prefixes, suffixes, or length-based padding to alter how safety classifiers tokenize or segment the input. |

## Detailed Category Descriptions

### Encoding & Unicode Tricks (13.27%)

Encoding and Unicode tricks manipulate the character-level representation of harmful instructions, exploiting the gap between how text is encoded and how it is interpreted. These techniques operate at the boundary between raw bytes and semantic meaning.

**ASCII Encoding (2.65%):** This technique converts harmful text into ASCII-encoded representations using decimal codes (e.g., "72 101 108 108 111" for "Hello"), hexadecimal codes, or other ASCII-based encoding schemes. The model is then asked to decode or interpret these sequences. While many modern models can decode ASCII representations directly, this technique can evade safety classifiers that flag text at the character level before decoding occurs.

**Base64 / URL / Obfuscation (8.85%):** The most prevalent encoding technique, this leaf encompasses encoding harmful instructions in Base64, URL encoding, or other standard obfuscation schemes. An attacker might encode a harmful request in Base64 and provide instructions to decode it, or URL-encode text to obscure it from pattern matching. These techniques exploit the fact that safety classifiers may not examine encoded representations before the model applies its decoding logic.

**Unicode / Bidi / Zero-Width (1.77%):** This technique exploits Unicode properties and rendering ambiguities. Bidirectional text (used for right-to-left languages) can be manipulated to make text appear different when rendered than when parsed sequentially. Zero-width characters (joiners, non-joiners) can be inserted to break up harmful words or change tokenization. Unicode lookalikes (e.g., Cyrillic 'А' instead of Latin 'A') can also evade character-level filters while remaining interpretable to the model.

### Wrappers & Schemas (7.08%)

Wrappers and schema-based obfuscation operate at a higher structural level, embedding harmful instructions within normalized formats (JSON, Markdown, XML, code snippets) that may be parsed differently by safety mechanisms than by the underlying model. These techniques exploit inconsistencies in how different components of the system interpret structured text.

**JSON / Markdown / Code-Blocks (4.42%):** Harmful instructions are embedded within structured formats such as JSON objects (as field values), Markdown code blocks, XML tags, or other formal syntax. Safety mechanisms designed to detect harmful text in natural language may not apply the same scrutiny to text within structured containers, or may parse the structure differently than the model does. For example, a harmful prompt might be hidden in a JSON field that is then fed to the model for interpretation.

**Length / Prefix-Suffix Wrappers (2.65%):** This technique wraps harmful text with benign prefixes or suffixes, or pads it with extra content, to alter tokenization boundaries and confuse length-based detection. An attacker might prepend a long benign passage before the harmful request, or wrap harmful text with repeated padding characters. These wrappers can change how safety classifiers segment and analyze the input, potentially causing the harmful content to be missed or misclassified.


<!-- BEGIN GENERATED: attack-catalog -->
<!-- This section is generated by scripts/generate_tables.py. Do not edit by hand. Update taxonomy/attacks.yaml instead. -->

## Attack Catalog

*23 documented attacks across Encoding Abuse. Grouped by category; see category docs for inclusion cues, canonical examples, and models tested.*

### Encoding & Unicode Tricks ([details](encoding-unicode-tricks.md)) — 14 attacks

| Attack | Leaf | Paper | Repository | Venue | Year |
|--------|------|-------|------------|-------|------|
| ASCII Art Attack | ASCII Encoding | [Link](https://arxiv.org/abs/2402.11753) | [Repo](https://github.com/uw-nsl/ArtPrompt) | ACL 2024 | 2024 |
| Read Over the Lines: Jailbreak LLMs via Camouflaging Profanity in ASCII Art | ASCII Encoding | [Link](https://arxiv.org/html/2409.18708v3) | [Repo](https://github.com/Serbernari/ToxASCII) | WOAH 2025 | 2025 |
| Symbolic Mathematics | ASCII Encoding | [Link](https://arxiv.org/abs/2409.11445) | — | ocially Responsible Language Modelling Research (SoLaR) Workshop at NeurIPS 2024 | 2024 |
| ACE | Base64 / URL / Obfuscation | [Link](https://arxiv.org/abs/2402.10601) | — | ArXiv | 2024 |
| Base64 Encoding (Promptfoo blog) | Base64 / URL / Obfuscation | [Link](https://www.promptfoo.dev/blog/how-to-jailbreak-llms/#base-encoding) | [Repo](https://github.com/promptfoo/promptfoo) | Promptfoo Blog | 2025 |
| Endless Jailbreaks with Bijection | Base64 / URL / Obfuscation | [Link](https://arxiv.org/abs/2410.01294) | [Repo](https://github.com/haizelabs/bijection-learning) | ICLR 2025 | 2025 |
| GPT-4 is Too Smart to Be Safe: Stealthy Chat with LLMs via Cipher | Base64 / URL / Obfuscation | [Link](https://arxiv.org/abs/2308.06463) | [Repo](https://github.com/RobustNLP/CipherChat) | ICLR 2024 | 2024 |
| JAM: Jailbreaking Large Language Models via Malicious Instruction Sequences in Cipher Text | Base64 / URL / Obfuscation | [Link](https://arxiv.org/abs/2405.20413) | — | NeurIPS 2024 | 2024 |
| Low-Resource Languages Jailbreak GPT-4 | Base64 / URL / Obfuscation | [Link](https://arxiv.org/abs/2310.02446) | — | NeurIPS 2023 SoLaR Workshop | 2023 |
| MetaCipher | Base64 / URL / Obfuscation | [Link](https://arxiv.org/abs/2506.22557) | [Repo](https://github.com/xzy-101/SAFER-code) | Arxiv | 2024 |
| Multilingual Jailbreak Challenges in Large Language Models | Base64 / URL / Obfuscation | [Link](https://arxiv.org/abs/2310.06474) | [Repo](https://github.com/DAMO-NLP-SG/multilingual-safety-for-LLMs) | ArXiv | 2023 |
| Sandwich Attack: Multi-Language Mixture Enhances the Jailbreak of Large Language Models | Base64 / URL / Obfuscation | [Link](https://arxiv.org/html/2404.07242v1) | — | TrustNLP 2024 | 2024 |
| Emoji Attack: Enhancing Jailbreak Attacks Against Judge LLM Detection | Unicode / Bidi / Zero-Width | [Link](https://arxiv.org/abs/2411.01077) | [Repo](https://github.com/zhipeng-wei/EmojiAttack) | ICML 2025 | 2025 |
| TokenBreak | Unicode / Bidi / Zero-Width | [Link](https://arxiv.org/abs/2506.07948) | — | Arxiv | 2025 |

### Wrappers & Schemas ([details](wrappers-and-schemas.md)) — 9 attacks

| Attack | Leaf | Paper | Repository | Venue | Year |
|--------|------|-------|------------|-------|------|
| Effective and Evasive Fuzz Testing–Driven Jailbreaking Attacks on LLMs (PAPILLON) | JSON / Markdown / Code-Blocks | [Link](https://www.usenix.org/system/files/usenixsecurity25-gong-xueluan.pdf) | [Repo](https://github.com/aaFrostnova/Papillon) | USENIX Security ’25 | 2025 |
| FuzzLLM: A Novel Fuzzing Framework for Large Language Models in Safety Settings | JSON / Markdown / Code-Blocks | [Link](https://arxiv.org/abs/2309.05274) | [Repo](https://github.com/RainJamesY/FuzzLLM) | ICASSP 2024 | 2024 |
| GPTFuzzer | JSON / Markdown / Code-Blocks | [Link](https://arxiv.org/abs/2309.10253) | [Repo](https://github.com/sherdencooper/GPTFuzz) | USENIX Security ’24 | 2024 |
| puppetry | JSON / Markdown / Code-Blocks | [Link](https://hiddenlayer.com/innovation-hub/novel-universal-bypass-for-all-major-llms/) | — | HiddenLayer Innovation Hub | 2025 |
| StructTransform: A Scalable Attack Surface for Safety-Aligned LLMs | JSON / Markdown / Code-Blocks | [Link](https://arxiv.org/abs/2502.11853) | [Repo](https://github.com/qcri/StructTransformBench) | ESORICS 2025 | 2025 |
| AdaPPA: Adaptive Position Prefill Attack Against Aligned LLMs | Length / Prefix-Suffix Wrappers | [Link](https://arxiv.org/abs/2409.07503) | [Repo](https://github.com/Yummy416/AdaPPA) | arXiv | 2024 |
| Cats Confuse Reasoning LLM: Query-Agnostic Adversarial Triggers for Reasoning Models | Length / Prefix-Suffix Wrappers | [Link](https://arxiv.org/abs/2503.01781) | [Repo](https://github.com/collinear-ai/CatAttack) | CoLM 2025 | 2025 |
| Curiosity‑driven Red Teaming (2024) | Length / Prefix-Suffix Wrappers | [Link](https://arxiv.org/abs/2402.19464) | [Repo](https://github.com/Improbable-AI/curiosity_redteam) | ICLR 2024 | 2024 |
| HIMRD (2024) | Length / Prefix-Suffix Wrappers | [Link](https://arxiv.org/abs/2412.05934) | [Repo](https://github.com/MaTengSYSU/HIMRD-jailbreak) | ICCV 2025 | 2025 |

<!-- END GENERATED: attack-catalog -->

## See Also

- [Encoding & Unicode Tricks](encoding-unicode-tricks.md) — covers ASCII Encoding, Base64 / URL / Obfuscation, and Unicode / Bidi / Zero-Width
- [Wrappers & Schemas](wrappers-and-schemas.md) — covers JSON / Markdown / Code-Blocks and Length / Prefix-Suffix Wrappers

For an overview of all families, see [Taxonomy Overview](../../taxonomy-overview.md).
