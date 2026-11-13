# Skills do Claude em português

Skills prontas a usar, em português de Portugal, para partilhar.

| Skill | O que faz | Palavra-chave |
|---|---|---|
| [`responder-emails`](responder-emails) | Lê os e-mails do dia, deixa os rascunhos prontos na tua caixa de correio e separa os que precisam de uma decisão tua. **Nunca envia, arquiva nem mexe no calendário.** | EMAIL |
| [`notas-para-tarefas`](notas-para-tarefas) | Cola as notas soltas de uma reunião e recebe o e-mail de seguimento, as tarefas com datas e o que ainda está por resolver. | NOTAS |
| [`voz-dna`](voz-dna) | Dá-lhe 3 textos teus e ele cria uma skill que escreve como tu. | VOZ |

## Como instalar

- **Claude (web e aplicação):** descarrega a pasta da skill em `.zip` e carrega-a na secção de skills das definições do Claude.
- **Claude Code:** copia a pasta da skill para `~/.claude/skills/`.

A `responder-emails` precisa de um conector de Gmail ou Microsoft 365 ligado ao Claude, com permissão para criar rascunhos.

## Licenças e créditos

Estas skills são traduções e adaptações de skills de código aberto com licença MIT. **Cada pasta traz o seu `LICENSE` e um `CREDITOS.md` com o autor original e a lista de alterações. Se partilhares uma skill, leva a pasta inteira.**

| Skill | Baseada em | Autor original | Licença |
|---|---|---|---|
| `responder-emails` | [cowork-inbox-triage](https://github.com/onewave-ai/claude-skills/tree/HEAD/cowork-inbox-triage) | OneWave AI | MIT |
| `notas-para-tarefas` | [meeting-to-tasks](https://github.com/onewave-ai/claude-skills/tree/HEAD/meeting-to-tasks) | OneWave AI | MIT |
| `voz-dna` | [voice-dna](https://github.com/nahiddotai/operator-powers/tree/HEAD/plugins/operator-powers/skills/voice-dna) | nahiddotai | MIT |

Os autores originais não revêem nem apoiam estas versões.
