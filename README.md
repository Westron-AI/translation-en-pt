# Modelo de Tradução Especializado em Documentações Técnicas (en-pt)

## ⚠️ Aviso

**Este modelo é uma prova de conceito de um modelo de tradução especializado em documentações técnicas desenvolvido como parte de um Trabalho de Conclusão de Curso. O uso deste modelo é voltado para fins acadêmicos. O autor não se responsabiliza por qualquer uso indevido.**

## Sobre 

Este é um modelo de tradução automática para tradução de inglês (en) para português (pt),   **fine-tuned** com dados da **Revista FAPESP** e **documentações técnicas de diversas fontes**. Os dados da FAPESP foram obtidos de [FAPESP Corpora](http://www.nilc.icmc.usp.br/nilc/tools/Fapesp%20Corpora.htm). Os dados de documentações técnicas, abrangendo mais de 10 mil páginas, foram coletados pelo autor em conformidade com as diretrizes específicas de cada fonte.

## Modelo Original

[Helsinki-NLP/opus-mt-tc-big-en-pt](https://huggingface.co/Helsinki-NLP/opus-mt-tc-big-en-pt)

## Modelo Fine-tuned Especializado em Documentações Técnicas
[westronai/translation-en-pt](https://huggingface.co/westronai/translation-en-pt)

## Características do Modelo

- **Arquitetura:** Transformer-Big
- **Linguagem de origem:** Inglês (en)
- **Linguagem alvo:** Português (pt)
- **Tokenização:** SentencePiece
- **Dados de fine-tuning:** Dados da Revista FAPESP e Documentações Técnicas

## Como Usar

Aqui está um exemplo de como usar o modelo em Python com Hugging Face:

```python
from transformers import MarianMTModel, MarianTokenizer

src_text = [
    "A bus is a communication system that transfers data between components.",
    "The database host is experiencing issues.",
    "The table is under a lock during the operation."
]

model_name = "westronai/translation-en-pt"
tokenizer = MarianTokenizer.from_pretrained(model_name)
model = MarianMTModel.from_pretrained(model_name)
translated = model.generate(**tokenizer(src_text, return_tensors="pt", padding=True))

for t in translated:
    print(tokenizer.decode(t, skip_special_tokens=True))

```
## Resultados
Essa tabela mostra as diferenças entre o modelo original e o modelo com fine-tuning, evidenciando as melhorias em termos de adequação técnica nas traduções.

| Sentença                                                    | Tradução Modelo Original                                                    | Tradução Modelo com Fine-Tuning                                             |
|---------------------------------------------------------------------|--------------------------------------------------------------------|-------------------------------------------------------------------|
| A bus is a communication system that transfers data between components | Um ônibus é um sistema de comunicação que transfere dados entre componentes | Um barramento é um sistema de comunicação que transfere dados entre componentes |
| The database host is experiencing issues                            | O anfitrião do banco de dados está enfrentando problemas             | O host do banco de dados está enfrentando problemas                |
| The table is under a lock during the operation                      | A mesa está sob um bloqueio durante a operação                      | A tabela está sob bloqueio durante a operação                      |

## Referência

```bibtex
@INPROCEEDINGS{aziz:2011:newfapesp,
AUTHOR={Wilker Aziz and Lucia Specia},
TITLE={Fully Automatic Compilation of a {Portuguese-English} Parallel Corpus for Statistical Machine Translation},
BOOKTITLE={STIL 2011},
ADDRESS={Cuiab\'a, MT},
DAYS={24-26},
MONTH={October},
YEAR={2011},
}

@inproceedings{tiedemann-thottingal-2020-opus,
    title = "{OPUS}-{MT} {--} Building open translation services for the World",
    author = {Tiedemann, J{\"o}rg  and Thottingal, Santhosh},
    booktitle = "Proceedings of the 22nd Annual Conference of the European Association for Machine Translation",
    month = nov,
    year = "2020",
    address = "Lisboa, Portugal",
    publisher = "European Association for Machine Translation",
    url = "https://aclanthology.org/2020.eamt-1.61",
    pages = "479--480",
}

@inproceedings{tiedemann-2020-tatoeba,
    title = "The Tatoeba Translation Challenge {--} Realistic Data Sets for Low Resource and Multilingual {MT}",
    author = {Tiedemann, J{\"o}rg},
    booktitle = "Proceedings of the Fifth Conference on Machine Translation",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2020.wmt-1.139",
    pages = "1174--1182",
}

=======
