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

## See Also

- [ASCII Encoding - Category Documentation](ascii-encoding.md)
- [Base64 / URL / Obfuscation - Category Documentation](base64-url-obfuscation.md)
- [Unicode / Bidi / Zero-Width - Category Documentation](unicode-bidi-zero-width.md)
- [JSON / Markdown / Code-Blocks - Category Documentation](json-markdown-code-blocks.md)
- [Length / Prefix-Suffix Wrappers - Category Documentation](length-prefix-suffix-wrappers.md)

For an overview of all families, see [Taxonomy Overview](../taxonomy-overview.md).
