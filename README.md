# Modelo de Tradução Adaptado ao Domínio de Documentações Técnicas de Tecnologia (en-pt)

## ⚠️ Aviso

**Este modelo é uma prova de conceito de um modelo de tradução especializado em documentações técnicas desenvolvido como parte de um Trabalho de Conclusão de Curso. O uso deste modelo é voltado para fins acadêmicos. O autor não se responsabiliza por qualquer uso indevido.**

## Sobre 

A técnica de _mixed fine-tuning_ foi aplicada, conforme descrito no artigo [An Empirical Comparison of Domain Adaptation Methods for Neural Machine Translation](https://aclanthology.org/P17-2061) (Chu et al., ACL 2017)

O _mixed fine-tuning_ foi realizado com dados da **Revista FAPESP** e **documentações técnicas de diversas fontes**. Os dados da FAPESP foram obtidos da seguinte fonte: [FAPESP Corpora](http://www.nilc.icmc.usp.br/nilc/tools/Fapesp%20Corpora.htm) (Aziz & Specia, 2011). Os dados de documentações técnicas, foram coletados e compilados pelo autor em conformidade com as diretrizes específicas de cada fonte.



## Modelo Original

[Helsinki-NLP/opus-mt-tc-big-en-pt](https://huggingface.co/Helsinki-NLP/opus-mt-tc-big-en-pt)

## Modelo Adaptado ao Domínio de Documentações Técnicas
[westronai/translation-en-pt](https://huggingface.co/westronai/translation-en-pt)

## Características do Modelo

- **Arquitetura:** Transformer-Big
- **Linguagem de origem:** Inglês (en)
- **Linguagem alvo:** Português (pt)
- **Tokenização:** SentencePiece
- **Dados de _fine-tuning_:** Dados da Revista FAPESP e Documentações Técnicas

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

| Sentença                                                    | Tradução Modelo Original                                                    | Tradução Modelo Adaptado                                          |
|---------------------------------------------------------------------|--------------------------------------------------------------------|-------------------------------------------------------------------|
| A bus is a communication system that transfers data between components | Um ônibus é um sistema de comunicação que transfere dados entre componentes | Um barramento é um sistema de comunicação que transfere dados entre componentes |
| The database host is experiencing issues                            | O anfitrião do banco de dados está enfrentando problemas             | O host do banco de dados está enfrentando problemas                |
| In Git, a branch is a new/separate version of the main repository. | No Git, um ramo é uma versão nova/separada do repositório principal.                     | No Git, um branch é uma versão nova/separada do repositório principal.|
| Asynchronous programming models, such as Promises and async/await, improve the efficiency of I/O operations | Modelos de programação assíncronos, como Promessas e assíncronas/despertar, melhoram a eficiência das operações de E/S | Modelos de programação assíncrona, como Promises e async/await, melhoram a eficiência das operações de E/S





## Métricas

A análise métrica foi realizada utilizando um conjunto de 10.000 sentenças, composto igualmente por documentações técnicas e textos da revista FAPESP, extraídas do conjunto de testes.


| Ferramenta | BLEU  | METEOR | chrF   |
|------------|-------|--------|--------|
| Modelo Original | 0.571 | 0.771  | 76.816 |
| Modelo Adaptado | 0.651 | 0.812  | 81.644 |





