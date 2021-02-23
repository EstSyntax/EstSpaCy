SpaCy pipelines for Estonian language
---
 
SpaCy pipelines for Estonian are trained on 
[Estonian UD v2.5 treebank](https://github.com/UniversalDependencies/UD_Estonian-EDT) 
using Python 3.6, spaCy 3.0, PyTorch 1.7.1 and follow Universal Dependencies tagsets for part-of-speech,
morphology and syntactic relations.

Pipelines:
 - `et_dep_ud_sm`: components tok2vec, morphologizer, parser
 - `et_dep_ud_estbert`: components transformer ([EstBERT](https://huggingface.co/tartuNLP/EstBERT)), 
 morphologizer, parser
 - `et_dep_ud_xlmroberta`: components transformer ([xlm-roberta-base](https://huggingface.co/xlm-roberta-base)), 
 morphologizer parser
 
 ---
 
SpaCy *pipeline*'id eesti keele jaoks on treenitud EstUD v2.5 puudepangal, kasutades Python 3.6 ja teeke spaCy 3.0 ja PyTorch 1.7.1.
Märgenduses kasutatakse Universal Dependencies projekti morfoloogiamärgendeid (rohkem infot [siin](https://universaldependencies.org/u/pos/index.html) ja [siin](https://universaldependencies.org/u/feat/index.html)) ja süntaksimärgendeid (rohkem infot [siin](https://universaldependencies.org/u/dep/index.html)).

Kõik *pipeline*'id võimaldavad parsida sõnaliike, morfoloogilist informatsiooni (v.a lemmad) ja süntaktilist informatsiooni.
Transformereid kasutavad spaCy mudelid on paljude suhete puhul paremad kui Stanford NLP avaldatud [Stanza mudel](https://stanfordnlp.github.io/stanza/available_models.html).
LAS-skoori järgi on edukaim XLM-RoBERTat kasutav mudel.
SpaCy on enamasti parem sagedasemate suhte puhul, kuid vähem täpne nt mõningate täiendite puhul.
Tokeniseerimine, lausestus ja sõnaliigid on seevastu paremad Stanza mudelil. Täpsemad skoorid on saadaval failis model_comparison.md.
Eamasti on mudelite skooride vahe väiksem kui 5%, suuremad erinevused tulevad esile harvaesinevamate suhete (nt _discourse_ ja _fixed_) puhul.
Kui GPU-d pole võimalik kasutada või ei soovi mahukat mudelit, on seega kindlasti mõistlik kasutada Stanza mudelit.
GPU puhul võiks mudeli valida vastavalt sellele, mis parsimisel parasjagu kõige enam huvitab.


*Pipeline*'ide kirjeldused:
 - `et_dep_ud_sm`: sisaldab komponente tok2vec, morphologizer, parser
 - `et_dep_ud_estbert`: sisaldab komponente transformer ([EstBERT](https://huggingface.co/tartuNLP/EstBERT)), 
 morphologizer, parser
 - `et_dep_ud_xlmroberta`: sisaldab komponente transformer ([xlm-roberta-base](https://huggingface.co/xlm-roberta-base)), 
 morphologizer parser
 
 
 
## Usage
For using pipelines Python 3.6+ must be used and [spaCy 3.0](https://spacy.io/usage) must be installed 
to according to whether you want to use CPU or GPU 
(strongly recommended for transformer pipelines).
Following are some instructions for installing spaCy via pip and conda,
for more detailed information refer to [spaCy installation instructions](https://spacy.io/usage). 

For using model without transformer on CPU, installing pipeline with 
`pip install ` installs all needed
requirements. Otherwise spaCy and other packages should be installed followingly

### Installing spaCy for CPU:

**Using pip**:
 
```
pip install -U pip setuptools wheel
pip install -U spacy
```
or (in case of transformer pipeline)

```
pip install -U pip setuptools wheel
pip install -U spacy[transformers]
```

**Using conda**:
```
conda install -c conda-forge spacy
```

in case of transformer pipeline spacy-transformers must be installed via pip:

```
pip install sentencepiece
pip install protobuf
pip install spacy-transformers
```

### Installing spaCy for GPU
**Using pip**:

Correct CUDA version must be specified in the CUDA extra (`cuda102` in the example). 
It is used for installing the correct version of cupy.
```
pip install -U pip setuptools wheel
pip install -U spacy[cuda102]
```

or (in case of transformer pipeline)

```
pip install sentencepiece
pip install protobuf
pip install -U spacy[cuda102,transformers]
```

**Using conda**:
```
conda install -c conda-forge spacy
conda install -c conda-forge cupy
# in case of transformer pipeline:
pip install sentencepiece
pip install protobuf
pip install spacy-transformers 
```

### Installing pipeline

Pipelines can be installed via pip: 

- et_dep_ud_xlmroberta
```
pip install 
```
- et_dep_ud_estbert
```
pip install 
```
- et_dep_ud_sm
```
pip install
```

or by saving chosen model from releases and installing by pointing to local file, e.g:

```
pip install /Users/you/et_dep_ud_sm-1.0.0.tar.gz
```

### Runtime usage
After installation pipelines can be used simply by importing and loading. 

**CPU**:
```python
import et_dep_ud_xlmroberta

nlp = et_dep_ud_xlmroberta.load()
doc = nlp('Jazz oli midagi rohkemat kui lihtsalt üks musitseerimisviis.')
```

**GPU**:
````python
import et_dep_ud_xlmroberta
import spacy

spacy.require_gpu()
# or spacy.prefer_gpu()

nlp = et_dep_ud_xlmroberta.load()  # Estonian Language object
doc = nlp('Jazz oli midagi rohkemat kui lihtsalt üks musitseerimisviis.') # Doc object
````

### Parsing
Doc object can be iterated to extract Token objects.
Following properties and attributes can be extracted from tokens:
 - `Token.i`: index of token
 - `Token.morph`: MorphAnalysis object that store a single morphological analysis
 - `Token.pos_`: attribute for par-of-speech tags
 - `Token.head`: Token object of current node's head
 - `Token.dep_`: arc label between current token and its head.

Parser allows to iterate over sentences using property `Doc.sents`.
NB! Syntax iterator for extracting noun chunks is not implemented.

For comprehensive list of properties and attributes refer to [spaCy API ](https://spacy.io/api/).



Example of outputting text in format similar to conllu by iterating through sentences
and tokens:
```python
import et_dep_ud_xlmroberta
import spacy

spacy.require_gpu()

nlp = et_dep_ud_xlmroberta.load()

doc = nlp('Jazz oli midagi rohkemat kui lihtsalt üks musitseerimisviis.' 
'Kui enne sõda sümboliseeris saksofoniga neeger paljude õpetatud meeste '
'silmis Õhtumaa allakäiku, siis sõjajärgses Euroopas hakkas ta tähistama '
'pigem vabanemist lämmatavast konventsioonide koorikust.')

for sentence in doc.sents:
    for word in sentence:
        print('\t'.join([str(word.i), str(word), '_', word.pos_, '_', 
                         str(word.morph), str(word.head.i), word.dep_, '_', '_']))
    print()
```

## Performance
Using CoNLL 208 Shared Task [evaluation script](https://github.com/ufal/conll2018/blob/master/evaluation_script/conll18_ud_eval.py).
More detailed scores for dependency lables can be found in *model_comparison.md*.

### et_dep_ud_sm
Metric     | Precision |    Recall |  F1 Score | AligndAcc
--- | --- | --- | --- | --- |
Tokens     |     97.70 |     99.14 |     98.41 |
Sentences  |     89.56 |     87.80 |     88.67 |
Words      |     97.70 |     99.14 |     98.41 |
UPOS       |     88.09 |     89.40 |     88.74 |     90.17
UFeats     |     77.88 |     79.03 |     78.45 |     79.71
UAS        |     70.79 |     71.84 |     71.31 |     72.46
LAS        |     62.71 |     63.64 |     63.17 |     64.19
CLAS       |     57.42 |     58.86 |     58.13 |     59.64
MLAS       |     45.22 |     46.35 |     45.78 |     46.96
BLEX       |      0.00 |      0.00 |      0.00 |      0.00


### et_dep_ud_estbert
Metric     | Precision |    Recall |  F1 Score | AligndAcc
--- | --- | --- | --- | --- |
Tokens     |     97.70 |     99.14 |     98.41 |
Sentences  |     92.54 |     91.44 |     91.99 |
Words      |     97.70 |     99.14 |     98.41 |
UPOS       |     94.69 |     96.09 |     95.38 |     96.92
UFeats     |     94.15 |     95.55 |     94.84 |     96.37
UAS        |     86.21 |     87.49 |     86.84 |     88.25
LAS        |     83.47 |     84.71 |     84.09 |     85.44
CLAS       |     81.39 |     82.95 |     82.16 |     84.05
MLAS       |     76.28 |     77.74 |     77.00 |     78.77


### et_dep_ud_xlmroberta
Metric     | Precision |    Recall |  F1 Score | AligndAcc
--- | --- | --- | --- | --- |
Tokens     |     97.70 |     99.14 |     98.41 |
Sentences  |     94.81 |     95.58 |     95.20 |
Words      |     97.70 |     99.14 |     98.41 |
UPOS       |     95.43 |     96.84 |     96.13 |     97.68
UFeats     |     94.50 |     95.90 |     95.20 |     96.73
UAS        |     88.08 |     89.38 |     88.73 |     90.16
LAS        |     85.49 |     86.75 |     86.11 |     87.50
CLAS       |     83.71 |     85.32 |     84.51 |     86.45
MLAS       |     79.60 |     81.14 |     80.36 |     82.21
