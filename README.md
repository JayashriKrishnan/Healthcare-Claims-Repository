Extraction Approaches



During development, multiple document understanding strategies were explored before converging on an LLM-based solution.



1\. Rule / Template-Based Extraction (Classical Computer Vision)



Early implementations relied on fixed form layouts. Fields were extracted using predefined spatial locations and anchor keywords.



Example mapping:



* Box 2 → Patient Name
* Box 21 → Diagnosis Code
* Box 24D → CPT Code



While effective for standardized HCFA-1500 forms, this approach proved highly template-specific and failed when layouts changed across providers.



Limitations:



* Requires per-template configuration
* Breaks under layout variation
* Sensitive to OCR inaccuracies



---



2\. Layout-Aware Machine Learning (Non-LLM)



Layout-aware models learn relationships between text content and spatial positioning using labeled datasets.



Examples:



* LayoutLM
* DiT
* DocFormer



Advantages:



* Better generalization across layouts
* Reduced rule engineering



Limitations:



* Requires annotated training data
* Expensive dataset preparation
* Retraining needed for new formats



---



3\. Traditional OCR + NLP (Pre-LLM Pipeline)



This method combined OCR output with classical NLP techniques such as regex parsing and keyword matching.



Characteristics:



\* Pattern-based extraction

\* Deterministic logic



Limitations:



* OCR errors propagate downstream
* Regex cannot understand semantic meaning
* Text ordering variations cause failures



---



4\. Commercial Document AI APIs



Pretrained enterprise solutions were evaluated conceptually, including:



* LayoutLM family models
* Amazon Textract
* Google Document AI



These systems integrate visual layout understanding with language modeling but introduce vendor dependency and cost considerations.



---



&nbsp;Final Approach: LLM-Based Document Understanding



The final implementation adopts a prompt-driven LLM extraction pipeline capable of handling heterogeneous claim formats.



Key advantages:



* Layout-independent extraction
* Robustness to noisy OCR text
* Reduced template engineering
* Adaptability to unseen claim structures



The repository therefore contains the LLM-based pipeline as the primary executable implementation, while earlier approaches are documented here for completeness and architectural comparison.



