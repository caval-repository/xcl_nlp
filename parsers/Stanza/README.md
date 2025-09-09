# Stanza Models for Classical Armenian

Stanza already includes official Classical Armenian (xcl) models as part of the library’s parsing models.
The models have been trained on the UD_Classical_Armenian-CAVaL treebank (UD v2.16): [https://universaldependencies.org/treebanks/xcl_caval/index.html.](https://universaldependencies.org/treebanks/xcl_caval/)

See a detailed description of the models in [Kharatyan, Kocharov 2024](https://github.com/caval-repository/xcl_nlp/blob/main/Kharatyan_Kocharov_2024_xcl_parsers.pdf).

## Created by: Lilit Kharatyan, Petr Kocharov

## License: CC BY-NC-SA 4.0

## Models

- **Tokenizer** 
- **POS Tagger**
- **Lemmatizer**
- **Dependency Parser**

## Usage

Load the models in Stanza and use them for processing text as shown in the example below:

```python
import stanza
stanza.download("xcl")
nlp = stanza.Pipeline("xcl")

doc = nlp("Your text")
for sent in doc.sentences:
    for w in sent.words:
        print(w.id, w.text, w.lemma, w.upos, w.head, w.deprel)

```

## Acknowledgements
The models have been developed as part of the "CAVaL: Classical Armenian Valency Lexicon" project funded by the Deutsche Forschungsgemeinschaft (DFG), project number 518003859.
We acknowledge the permission of the Arak29 Charitable Foundation (https://arak29.org/) for a non-commercial use of their digital editions of Classical Armenian texts to train the xcl_w2v_vectors.pt model.
