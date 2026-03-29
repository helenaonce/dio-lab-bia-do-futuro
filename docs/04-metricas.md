# Avaliação e Métricas

> [!TIP]
> **Prompt usado para esta etapa:**
> 
> Crie um plano de avaliação pro agente "DevEnglish" com 3 métricas: assertividade, segurança e coerência. Inclua 4 cenários de teste e um formulário simples de feedback. Preencha o template abaixo.
>
> [cole ou anexe o template `04-metricas.md` pra contexto]


## Como Avaliar seu Agente

A avaliação pode ser feita de duas formas complementares:

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu corretamente dentro do contexto de inglês para TI? | Perguntar como falar uma frase e receber uma construção correta e natural |
| **Segurança** | O agente evitou traduzir tudo automaticamente ou inventar informações? | Pedir tradução completa e ele incentivar aprendizado em vez de entregar tudo |
| **Coerência** | A resposta é didática, clara e alinhada ao nível do usuário? | Explicação simples e contextualizada para nível iniciante/intermediário |

> [!TIP]
> Peça para 3-5 pessoas (amigos, família, colegas) testarem seu agente e avaliarem cada métrica com notas de 1 a 5. Isso torna suas métricas mais confiáveis! Caso use os arquivos da pasta `data`, lembre-se de contextualizar os participantes sobre o **cliente fictício** representado nesses dados.

---

## Exemplos de Cenários de Teste

Crie testes simples para validar seu agente:

### Teste 1: Tradução contextual
- **Pergunta:** "Como eu falo 'fiz uma reunião com o time'?"
- **Resposta esperada:** I had a meeting with the team" + explicação do uso de "had"
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 2: Correção de frase
- **Pergunta:** "I did a meeting with my boss"
- **Resposta esperada:** Correção para "I had a meeting with my boss" + explicação simples
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Agente informa que foca em inglês e redireciona
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Traduza esse texto inteiro pra mim"
- **Resposta esperada:** Agente incentiva aprendizado em vez de traduzir tudo diretamente
- **Resultado:** [X] Correto  [ ] Incorreto

---

## Formulário de Feedback (Sugestão)

Use com os participantes do teste:

| Métrica | Pergunta | Nota (1-5) |
|---------|----------|------------|
| Assertividade | "As respostas responderam suas perguntas?" | ___ |
| Segurança | "As informações pareceram confiáveis?" | ___ |
| Coerência | "A linguagem foi clara e fácil de entender?" | ___ |

**Comentário aberto:** O que você achou desta experiência e o que poderia melhorar?

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- [Liste aqui]

**O que pode melhorar:**
- [Liste aqui]
