# Stanza Models for Classical Armenian

This directory contains Stanza models for Classical Armenian, including tokenizer, POS tagger, lemmatizer, and dependency parser. 
The models have been trained on the UD_Classical_Armenian-CAVaL treebank (UD v2.14): https://universaldependencies.org/treebanks/xcl_caval/index.html.

## Created by: Lilit Kharatyan, Petr Kocharov

## License: CC BY-NC-ND 4.0

## Models

- **Tokenizer**: `xcl_classicalarmenian_tokenizer.pt`
- **POS Tagger**: `xcl_classicalarmenian_nocharlm_tagger.pt`
- **Lemmatizer**: `xcl_classicalarmenian_nocharlm_lemmatizer.pt`
- **Dependency Parser**: `xcl_classicalarmenian_nocharlm_parser.pt`
- **Pretrained Vectors**: `xcl_w2v_vectors.pt`

## Usage

Load the models in Stanza and use them for processing text as shown in the example below:

```python
import stanza

# Define the paths to the models
tokenizer_model_path = 'parsers/stanza/xcl_classicalarmenian_tokenizer.pt'
pos_model_path = 'parsers/stanza/xcl_classicalarmenian_nocharlm_tagger.pt'
lemma_model_path = 'parsers/stanza/xcl_classicalarmenian_nocharlm_lemmatizer.pt'
depparse_model_path = 'parsers/stanza/xcl_classicalarmenian_nocharlm_parser.pt'
pretrain_path = 'parsers/stanza/new_vectors.pt'

# Initialize the pipeline
nlp = stanza.Pipeline(lang='hy', 
                      tokenize_model_path=tokenizer_model_path,
                      pos_model_path=pos_model_path,
                      lemma_model_path=lemma_model_path,
                      depparse_model_path=depparse_model_path,
                      pos_pretrain_path=pretrain_path,
                      depparse_pretrain_path=pretrain_path)

# Example text
text = "Եւ ելեալ գնաց ըստ սովորութեանն ի լեառն Ձիթենեաց. գնացին զհետ նորա եւ աշակերտքն:"
doc = nlp(text)

# Process and print the results in conll-u format
for sentence in doc.sentences:
    print(f"# text = {sentence.text}")
    for word in sentence.words:
        feats = word.feats if word.feats else '_'
        conllu_line = f"{word.id}\t{word.text}\t{word.lemma}\t{word.upos}\t_\t{feats}\t{word.head}\t{word.deprel}\t_"
        print(conllu_line)
    print()

## Acknowledgements
The models have been developed as part of the "CAVaL: Classical Armenian Valency Lexicon" project funded by the Deutsche Forschungsgemeinschaft (DFG), project number 518003859.
We acknowledge the permission of the Arak29 Charitable Foundation (https://arak29.org/) to use the digital editions of Classical Armenian texts for training of the xcl_w2v_vectors.pt model.
