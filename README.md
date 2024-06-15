# Transformers Pipelines Example

This repository demonstrates the usage of different pipelines available in the Hugging Face Transformers library for natural language processing and computer vision tasks.

## Installation

To use the code in this repository, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/your/repository.git
   cd repository
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Zero-Shot Classification

Perform zero-shot text classification using pretrained models.

```python
from transformers import pipeline

classifier = pipeline("zero-shot-classification")
text = '''
<Your input text>
'''

labels = ['political', 'racial', 'gender']

scores = classifier(text, labels)

for i in range(len(scores)):
    print(f"{labels[i]} = {scores['scores'][i] * 100:.2f}%")
```

### Named Entity Recognition (NER)

Identify named entities in text using pretrained models.

```python
ner = pipeline("ner", grouped_entities=True)
entities = ner(text)

for entity in entities:
    print(f"{entity['word']} - {entity['entity_group']}")
```

### Image-to-Text Conversion

Convert images to text using a pretrained image-to-text model.

```python
mm_pipeline = pipeline("image-to-text", model="llava-hf/llava-1.5-7b-hf")
result = mm_pipeline("https://example.com/image.jpg", "Optional caption or question")

print(result)
```
## Acknowledgments

- Hugging Face Transformers Library: https://huggingface.co/transformers/
