# Base de Conhecimento

> [!TIP]
> **Prompt usado para esta etapa:**
> 
> Organize a base de conhecimento do agente "DevEnglish" usando os 4 arquivos da pasta data/ (em anexo). Explique pra que serve cada arquivo e monte um exemplo de contexto formatado que será enviado pro LLM. Preencha o template abaixo.
>
> [cole ou anexe o template `02-base-conhecimento.md` pra contexto]

## Dados Utilizados


| Arquivo | Formato | Para que serve no Edu? |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV |Contextualizar interações anteriores do aluno, acompanhando evolução no inglês e dificuldades recorrentes. |
| `perfil_investidor.json` | JSON | Personalizar o ensino com base no nível de inglês, área de atuação em TI e objetivos do usuário.|
| `produtos_financeiros.json` | JSON | Fornecer exemplos reais de inglês aplicado ao dia a dia de TI (reuniões, commits, entrevistas, etc.). |
| `transacoes.csv` | CSV | Identificar erros frequentes e ajudar o agente a corrigir de forma didática e contextualizada. |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Os dados foram adaptados para o contexto de ensino de inglês para tecnologia. Em vez de dados financeiros, foram incluídos exemplos práticos de comunicação em inglês no ambiente de TI, como frases usadas em reuniões, entrevistas e código. Também foram adicionados erros comuns cometidos por brasileiros para melhorar a capacidade de correção do agente.


---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Existem duas possibilidades, injetar os dados diretamente no prompt (Ctrl + C, Ctrl + V) ou carregar os arquivos via código, como no exemplo abaixo:

```python
import pandas as pd
import json

perfil = json.load(open('./data/perfil_investidor.json'))
transacoes = pd.read_csv('./data/transacoes.csv')
historico = pd.read_csv('./data/historico_atendimento.csv')
produtos = json.load(open('./data/produtos_financeiros.json'))
```

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Para simplificar, podemos simplesmente "injetar" os dados em nosso prompt, agarntindo que o Agente tenha o melhor contexto possível. Lembrando que, em soluções mais robustas, o ideal é que essas informaçoes sejam carregadas dinamicamente para que possamos ganhar flexibilidade.

```text
DADOS DO CLIENTE E PERFIL (data/perfil_investidor.json):
{
  "nome": "Maria",
  "nivel_ingles": "basico",
  "area_ti": "analise de dados",
  "objetivo": "melhorar comunicação em reuniões e entrevistas",
  "dificuldades": ["speaking", "listening", "formação de frases"],
  "preferencia_aprendizado": "exemplos práticos e correções leves"
}

ERROS COMUNS (data/erros_comuns.csv):
erro,correcao,explicacao
"I did a travel","I took a trip","'Travel' não é usado como substantivo contável"
"Make a code","Write code","'Make' não é usado nesse contexto"
"I have 20 years","I am 20 years old","Estrutura correta para idade em inglês"
"I did a meeting","I had a meeting","'Have' é o verbo correto para reuniões"

HISTORICO DE INTERAÇÕES (data/historico_interacoes.csv):
data,tema,frase_usuario,correcao_aplicada,evolucao
2025-10-01,reuniao,"I did a meeting with the team","I had a meeting with the team",sim
2025-10-03,entrevista,"I am working here since 2 years","I have been working here for 2 years",sim
2025-10-05,codigo,"I make a function","I write a function",sim
2025-10-10,apresentacao,"I explain the dashboard yesterday","I explained the dashboard yesterday",sim

FRASES TECNICAS (data/frases_tecnicas.json):
[
  {
    "contexto": "reuniao",
    "frase": "Let's align on the next steps",
    "explicacao": "Usado para alinhar próximos passos em reuniões"
  },
  {
    "contexto": "codigo",
    "frase": "I'll push the changes to the repository",
    "explicacao": "Usado ao enviar alterações para o repositório"
  },
  {
    "contexto": "entrevista",
    "frase": "I have experience working with data pipelines",
    "explicacao": "Forma comum de descrever experiência técnica"
  },
  {
    "contexto": "debug",
    "frase": "I'm investigating the root cause of the issue",
    "explicacao": "Usado ao analisar problemas técnicos"
  }
]
```

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

O exemplo de contexto montado abaixo, se baiseia nos dados originais da base de conhecimento, mas os sintetiza deixando apenas as informações mais relevantes, otimizando assim o consumo de tokens. Entretanto, vale lembrar que mais importante do que economizar tokens, é ter todas as informações relevantes disponíveis em seu contexto.

```
DADOS DO USUÁRIO:
- Nome: Maria
- Nível: Intermediário
- Área: Análise de Dados
- Objetivo: Melhorar comunicação em reuniões e entrevistas

PRINCIPAIS DIFICULDADES:
- Speaking
- Listening
- Formação de frases

ERROS FREQUENTES:
- "I did a meeting" → "I had a meeting"
- "Make a code" → "Write code"
- "I have 20 years" → "I am 20 years old"

FRASES ÚTEIS (TI):
- "Let's align on the next steps"
- "I'll push the changes to the repository"
- "I'm investigating the root cause of the issue"
- "I have experience working with data pipelines"
```
