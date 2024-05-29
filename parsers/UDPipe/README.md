# Classical Armenian UDPipe 2 Model

This repository contains a UDPipe 2 model for Classical Armenian, including a POS tagger, lemmatizer and dependency parser. The model have been trained on the UD_Classical_Armenian-CAVaL treebank (UD v2.14): https://universaldependencies.org/treebanks/xcl_caval/index.html The deployment and use of this model require some computational knowledge and resources and are intended as a research tool rather than a user-friendly, intuitive application.

## Created by: Lilit Kharatyan, Petr Kocharov

## License: CC BY-SA 4.0

## Directory Structure

- **Parsers**
  - **UDPipe**
    - `checkpoint`
    - `events.out.tfevents.1714655826.WVGL039.v2`
    - `log`
    - `mappings.pickle`
    - `options.json`
    - `weights.data-00000-of-00001`
    - `weights.index`
    - `XCL.tokenizer`
    - **C**
      - `events.out.tfevents.1708955920.WVGL039.v2`
      - `events.out.tfevents.1714655826.WVGL039.v2`

## Deployment

To deploy this model, follow the guidelines provided in the [UDPipe 2 GitHub repository](https://github.com/ufal/udpipe/tree/udpipe-2).

## Important Configuration

Ensure that the `udpipe2_server.py` file contains the following lines to correctly compute the word embeddings:

```python
# Compute the WEmbeddings
with self._server_args.optional_semaphore:
    time_we = time.time()
    if self._network.args.wembedding_model:
        wembeddings = self._server_args.wembedding_server.compute_embeddings(self._network.args.wembedding_model, wembedding_input)
    else:
        wembeddings = []
```
## Acknowledgments

The models have been developed as part of the "CAVaL: Classical Armenian Valency Lexicon" project funded by the Deutsche Forschungsgemeinschaft (DFG), project number 518003859.

We are grateful to Milan Straka for his assistance with the code and for modifying scripts to accommodate the specific requirements of our model.

## Contact
For any questions or assistance regarding the deployment and use of the model, please contact [Lilit Kharatyan](https://www.phil.uni-wuerzburg.de/en/vgsp/team/lilit-kharatyan/).
