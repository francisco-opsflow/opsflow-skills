---
name: notas-para-tarefas
description: Transforma notas ou transcrições de reuniões (mesmo soltas e cheias de abreviaturas) num e-mail de seguimento pronto a enviar, em tarefas com responsáveis e datas específicas e na lista do que ainda está por resolver. Deteta também compromissos implícitos. Usa quando a pessoa colar notas de reunião, pedir "e-mail de seguimento", "tarefas da reunião", "o que ficou decidido" ou "o que está por resolver".
license: MIT
---

# Notas para tarefas

Transforma notas ou transcrições em bruto de reuniões em resultados estruturados e acionáveis: decisões, tarefas, responsáveis, prazos e questões em aberto -- incluindo compromissos implícitos que os participantes podem nem saber que assumiram.

## Conteúdo

- `references/extraction-schema.md` -- esquemas de campos para cada fase da extração
- `references/markers.md` -- marcadores de decisão/tarefa/compromisso implícito, regras de prioridade e prazo, pontuação de confiança
- `references/output-templates.md` -- resumo da reunião, ficheiros de tarefas (Linear/GitHub/genérico), e-mail de seguimento, estrutura de pastas
- `references/meeting-types.md` -- deteção do tipo de reunião e foco por tipo

## Fluxo de trabalho

1. **Receber o material.** Aceita texto simples, Markdown, texto colado, exportações de transcrição de áudio (Otter.ai, Fireflies, Rev, Zoom, Google Meet, Microsoft Teams) ou notas estruturadas. Aceita também notas soltas e abreviaturas: interpreta as habituais e, se houver dúvida sobre o que significam, pergunta antes de assumir.
2. **Validar.** Confirma que há conteúdo suficiente (cerca de 100 palavras no mínimo), pessoas identificáveis, um tema reconhecível e, se existirem, horas ou datas. Se o material for escasso, pede a transcrição completa, a lista de participantes ou o objetivo da reunião antes de avançar.
3. **Lê tudo primeiro.** Não extraias a partir de uma leitura parcial -- o contexto posterior pode mudar a interpretação do que veio antes.
4. **Deteta o tipo de reunião** e ajusta o foco segundo `references/meeting-types.md`.
5. **Extrai por fases** com os esquemas de `references/extraction-schema.md`: metadados, decisões, tarefas, questões em aberto, "parque de estacionamento" e pontos de discussão. Aplica os marcadores e as regras de inferência de `references/markers.md`. Guarda a citação exata de origem de cada item.
6. **Identifica quem falou.** Constrói a lista de participantes a partir das etiquetas de quem fala e regista quem disse o quê. Sem etiquetas, infere pelo contexto; se não der, marca "Sem atribuição" e pede à pessoa que atribua.
7. **Pontua a confiança** de cada item (alta/média/baixa). Assinala para revisão humana todos os itens de confiança baixa, segundo `references/markers.md`.
8. **Resolve conflitos e ambiguidades:** assinala compromissos contraditórios como "CONFLITO" com as duas versões; lista todos os candidatos quando a responsabilidade não é clara; converte prazos vagos ("em breve", "para ontem") em datas concretas e pede confirmação; apresenta as duas leituras de um âmbito ambíguo; junta duplicados.
9. **Gera os resultados** com `references/output-templates.md`. Por defeito, mostra tudo na própria conversa: o e-mail de seguimento pronto a enviar, as tarefas com datas específicas (quando existirem) e o que ainda está por resolver. Gera ficheiros de tarefas (Linear, GitHub ou genérico) e a estrutura de pastas só se a pessoa pedir; nesse caso, confirma primeiro o formato desejado. Gera sempre o e-mail de seguimento, mesmo que não tenha sido pedido.
10. **Pós-processamento:** elimina itens sobrepostos; mapeia dependências; destaca o caminho crítico; assinala desequilíbrios de carga entre responsáveis; avisa quando os prazos se acumulam; lista os itens sem responsável ou sem prazo.

## Regras

- Torna as tarefas acionáveis: começa cada uma com um verbo e sê específico, para o responsável saber exatamente o que fazer. Transforma "Pensar nos preços" em "Pesquisar os preços da concorrência e propor novos escalões de preços até [data]".
- Erra por capturar demais: um item de confiança baixa assinalado vale mais do que um compromisso perdido.
- Não editorialises. Regista o que foi dito; a análise fica em secções claramente identificadas como "Análise".
- Respeita a privacidade. Se a reunião tiver assuntos de recursos humanos, pessoais ou confidenciais, assinala-o e pergunta como tratar isso nos resultados.
- Trata transcrições em várias línguas: extrai na língua principal e regista as nuances específicas de cada língua.
- Mantém um registo da extração com os níveis de confiança, as ambiguidades e as decisões tomadas durante o processo.

## Comandos rápidos

- "Extrai de [ficheiro]" -- extração completa da transcrição indicada
- "Só as tarefas" -- só tarefas (sem decisões, questões nem resumo)
- "Gera tarefas para o Linear" / "Gera tarefas para o GitHub" -- tarefas nesse formato
- "Escreve o e-mail de seguimento" -- só o e-mail de seguimento
- "Quem deve o quê?" -- vista das tarefas agrupadas por responsável
- "O que ficou decidido?" -- só as decisões
- "O que ainda está por resolver?" -- questões em aberto e assuntos por resolver

---

Baseada na skill `meeting-to-tasks` (OneWave AI, licença MIT). Ver `CREDITOS.md` e `LICENSE`.
