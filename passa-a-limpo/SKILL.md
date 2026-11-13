---
name: passa-a-limpo
description: Quando a pessoa escrever "passa a limpo" (ou "resumo para novo chat", "vou abrir um chat novo"), resume a conversa num bloco curto e colável com o objetivo, as decisões, as regras e o próximo passo, para continuar num chat novo sem perder contexto e sem gastar o limite.
---

# Passa a limpo

Conversas longas gastam mais limite, porque cada resposta obriga o Claude a reler tudo. Esta skill condensa a conversa num bloco pequeno que a pessoa cola num chat novo.

## Quando usar

- A pessoa escreve "passa a limpo".
- A pessoa diz que vai abrir um chat novo, ou que a conversa já está muito longa.

## O que fazer

1. Relê a conversa e extrai só o que é preciso para continuar. Não inventes nada: se algo não foi dito, não entra.
2. Responde apenas com o bloco abaixo, dentro de um bloco de código para ser fácil de copiar. Sem introdução e sem comentários antes.
3. Depois do bloco, escreve uma única linha: "Copia o bloco, abre um chat novo e cola lá para continuares."

## Formato do bloco

```
CONTEXTO PARA CONTINUAR (colado de um chat anterior)

OBJETIVO
- [o que se está a tentar conseguir, numa ou duas frases]

DECISÕES JÁ TOMADAS
- [decisão] (porquê, se for relevante)

REGRAS E PREFERÊNCIAS
- [tom, formato, idioma, limites, coisas a evitar que a pessoa pediu]

ESTADO ATUAL
- [o que já está feito e o que está a meio; ficheiros, nomes ou números importantes]

PRÓXIMO PASSO
- [a primeira ação concreta a fazer no chat novo]

Continua a partir daqui, sem repetir o que já está decidido.
```

## Regras

- Mantém o bloco curto: idealmente menos de 250 palavras. Corta o que não muda o próximo passo.
- Escreve na língua em que a pessoa tem falado.
- Se uma secção não tiver conteúdo, apaga-a em vez de a preencher com enchimento.
- Guarda os textos finais que a pessoa quer manter (um guião, um e-mail aprovado) por inteiro, dentro de ESTADO ATUAL, em vez de os resumir.
- Não incluas palavras-passe, chaves ou dados sensíveis.
- Se a conversa for curta (poucas mensagens), diz numa linha que ainda não vale a pena trocar de chat e dá o bloco na mesma, se a pessoa quiser.
