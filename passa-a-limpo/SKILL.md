---
name: passa-a-limpo
description: Quando a pessoa escrever "passa a limpo" (ou "resumo para novo chat", "vou abrir um chat novo"), condensa a conversa num ficheiro ESTADO.md pronto a anexar a um chat novo, com o objetivo, as decisões, as regras e o próximo passo, para continuar sem perder contexto e sem gastar o limite.
---

# Passa a limpo

Conversas longas gastam mais limite, porque cada resposta obriga o Claude a reler tudo. Esta skill condensa a conversa num ficheiro `ESTADO.md` que a pessoa anexa a um chat novo e pronto: o chat novo arranca já a trabalhar.

## Quando usar

- A pessoa escreve "passa a limpo".
- A pessoa diz que vai abrir um chat novo, ou que a conversa já está muito longa.

## O que fazer

1. Relê a conversa e extrai só o que é preciso para continuar. Não inventes nada: se algo não foi dito, não entra.
2. Cria o ficheiro `ESTADO.md` com o formato abaixo e entrega-o à pessoa (envia o ficheiro, para ela o poder descarregar). O nome é sempre `ESTADO.md`, sem datas nem variações.
3. Se não conseguires criar ficheiros nesta conversa, dá o mesmo conteúdo dentro de um bloco de código, para a pessoa o copiar e colar num ficheiro ou diretamente no chat novo.
4. Não escrevas o conteúdo no chat nem faças introdução. Depois de entregar o ficheiro, escreve uma única linha: "Descarrega o ESTADO.md, abre um chat novo e anexa-o na primeira mensagem para continuares."

## Formato do ficheiro ESTADO.md

```
# ESTADO: [nome curto do tema]

> Instrução para o Claude: isto é o resumo de um chat anterior. Lê tudo, responde numa linha a dizer o que percebeste e avança logo pelo PRÓXIMO PASSO, sem repetir o que já está decidido nem fazer perguntas que já têm resposta aqui.

## Objetivo
- [o que se está a tentar conseguir, numa ou duas frases]

## Decisões já tomadas
- [decisão] (porquê, se for relevante)

## Regras e preferências
- [tom, formato, idioma, limites, coisas a evitar que a pessoa pediu]

## Estado atual
- [o que já está feito e o que está a meio; ficheiros, nomes ou números importantes]

## Próximo passo
- [a primeira ação concreta a fazer no chat novo]
```

## Regras

- Mantém o ficheiro curto: idealmente menos de 250 palavras, sem contar os textos finais guardados por inteiro. Corta o que não muda o próximo passo.
- Escreve na língua em que a pessoa tem falado.
- Se uma secção não tiver conteúdo, apaga-a em vez de a preencher com enchimento.
- Guarda os textos finais que a pessoa quer manter (um guião, um e-mail aprovado) por inteiro, dentro de "Estado atual", em vez de os resumir.
- Não incluas palavras-passe, chaves ou dados sensíveis.
- Se a conversa for curta (poucas mensagens), diz numa linha que ainda não vale a pena trocar de chat e entrega o ficheiro na mesma, se a pessoa quiser.
