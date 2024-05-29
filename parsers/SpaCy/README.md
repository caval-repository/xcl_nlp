# Classical Armenian SpaCy Models

This repository contains SpaCy models for Classical Armenian, including parser, lemmatizer, and morphologizer/tagger. The models have been trained on the UD_Classical_Armenian-CAVaL treebank (UD v2.14): https://universaldependencies.org/treebanks/xcl_caval/index.html.

## Created by: Lilit Kharatyan, Petr Kocharov

## License: CC BY-NC-ND 4.0

## Directory Structure

- **Parsers**
  - **SpaCy**
    - **morphologizer_tagger**: Morphologizer/Tagger model
    - **lemmatizer**: Lemmatizer model
    - **parser**: Dependency parser model

Each model directory contains the following files:
- `config.cfg`: Configuration file
- `meta.json`: Metadata file
- `model_folder`: Directory containing model-specific files (e.g., `parser`, `trainable_lemmatizer`, `morphologizer`, `tagger`)
- `tok2vec`: Directory containing tok2vec model files
- `tokenizer`: Tokenizer model file
- `vocab`: Directory containing vocabulary files

## Usage

To use these models, you need to have SpaCy installed. You can install SpaCy using pip:

```bash
pip install spacy
from spacy.language import Language as DefaultLanguage
from spacy.util import set_lang_class

class XclLanguage(DefaultLanguage):
    lang = "xcl"

    @classmethod
    def create(cls, vocab):
        nlp = super(XclLanguage, cls).create(vocab)
        return nlp

# Add the custom language class to SpaCy
set_lang_class("xcl", XclLanguage)

import spacy

# Load the morphologizer/tagger model
nlp_morph = spacy.load("parsers/SpaCy/morphologizer_tagger")

# Load the lemmatizer model
nlp_lemma = spacy.load("parsers/SpaCy/lemmatizer")

# Load the dependency parser model
nlp_parser = spacy.load("parsers/SpaCy/parser")

# Example text
text = "Ասաց եւ առակ մի նոցա՝ առ այն թե պարտ է յամենայն ժամ կալ նոցա յաղաւթս. եւ մի ձանձրանալ."

# Process the text with the morphologizer/tagger model
doc_morph = nlp_morph(text)
print("Morphologizer/Tagger Model Results:")
for token in doc_morph:
    print(f"Token: {token.text}, POS: {token.pos_}, Morph: {token.morph}")

# Process the text with the lemmatizer model
doc_lemma = nlp_lemma(text)
print("\nLemmatizer Model Results:")
for token in doc_lemma:
    print(f"Token: {token.text}, Lemma: {token.lemma_}")

# Process the text with the dependency parser model
doc_parser = nlp_parser(text)
print("\nDependency Parser Model Results:")
for token in doc_parser:
    print(f"Token: {token.text}, Dep: {token.dep_}, Head: {token.head.text}")
```
## Acknowledgements
The models have been developed as part of the "CAVaL: Classical Armenian Valency Lexicon" project funded by the Deutsche Forschungsgemeinschaft (DFG), project number 518003859.
We acknowledge the permission of the Arak29 Charitable Foundation (https://arak29.org/) for a non-commercial use of their digital editions of Classical Armenian texts to train word2vec vectors. Thanks to Adriane Boyd from Explosion AI for her prompt and invaluable assistance with issues regarding the dataset and training process
