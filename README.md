# Skills do Claude em português

Skills prontas a usar, em português de Portugal, para partilhar.

| Skill | O que faz | Palavra-chave |
|---|---|---|
| [`responder-emails`](responder-emails) | Lê os e-mails do dia, deixa os rascunhos prontos na tua caixa de correio e separa os que precisam de uma decisão tua. **Nunca envia, arquiva nem mexe no calendário.** | EMAIL |
| [`notas-para-tarefas`](notas-para-tarefas) | Cola as notas soltas de uma reunião e recebe o e-mail de seguimento, as tarefas com datas e o que ainda está por resolver. | NOTAS |
| [`voz-dna`](voz-dna) | Dá-lhe 3 textos teus e ele cria uma skill que escreve como tu. | VOZ |
| [`passa-a-limpo`](passa-a-limpo) | Diz "passa a limpo" a meio de uma conversa e a decisão em cima da mesa vai a um conselho de 5 conselheiros de IA, que a analisam, se avaliam entre si e dão um veredicto no chat. | PASSA A LIMPO |

## Como instalar

- **Claude (web e aplicação):** descarrega a pasta da skill em `.zip` e carrega-a na secção de skills das definições do Claude.
- **Claude Code:** copia a pasta da skill para `~/.claude/skills/`.

A `responder-emails` precisa de um conector de Gmail ou Microsoft 365 ligado ao Claude, com permissão para criar rascunhos.

## Licenças e créditos

Estas skills são traduções e adaptações de skills de outros autores. **Cada pasta traz um `CREDITOS.md` com o autor original e a lista de alterações e, quando o original tem licença MIT, o respetivo `LICENSE`. Se partilhares uma skill, leva a pasta inteira.**

| Skill | Baseada em | Autor original | Licença |
|---|---|---|---|
| `responder-emails` | [cowork-inbox-triage](https://github.com/onewave-ai/claude-skills/tree/HEAD/cowork-inbox-triage) | OneWave AI | MIT |
| `notas-para-tarefas` | [meeting-to-tasks](https://github.com/onewave-ai/claude-skills/tree/HEAD/meeting-to-tasks) | OneWave AI | MIT |
| `voz-dna` | [voice-dna](https://github.com/nahiddotai/operator-powers/tree/HEAD/plugins/operator-powers/skills/voice-dna) | nahiddotai | MIT |
| `passa-a-limpo` | [llm-council](https://github.com/aiwithremy/claude-skills-llm-council) | Ole Lehmann | Não indicada no original |

Os autores originais não revêem nem apoiam estas versões.
