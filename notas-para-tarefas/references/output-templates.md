# Modelos de resultados

Modelos para cada resultado gerado e a estrutura de pastas que os guarda. Por defeito, apresenta o resumo, as tarefas, o que está por resolver e o e-mail de seguimento diretamente na conversa. Cria ficheiros e pastas só quando a pessoa o pedir.

## Estrutura da pasta de resultados

```
meeting-outputs/
  {data}-{nome-da-reuniao}/
    meeting-summary.md           # Resumo completo da reunião
    follow-up-email.md           # Seguimento pronto a enviar
    action-items.yaml            # Todas as tarefas em formato estruturado
    tasks/
      linear/                    # Ficheiros de tarefas compatíveis com o Linear
        A-001.md
        A-002.md
      github/                    # Ficheiros compatíveis com GitHub Issues
        A-001.md
        A-002.md
      generic/                   # Ficheiros YAML genéricos de tarefas
        A-001.yaml
        A-002.yaml
    raw/
      transcript.md              # Transcrição original (preservada)
      extraction-log.md          # Registo das decisões de extração e pontuações de confiança
```

## Resultado 1: Resumo da reunião (meeting-summary.md)

```markdown
# Resumo da reunião: [Título]
**Data**: [Data]
**Duração**: [Duração]
**Participantes**: [Lista]
**Tipo**: [Tipo de reunião]

---

## Resumo

[Resumo narrativo em 2 a 3 parágrafos. O que foi discutido, o que foi decidido
e o que tem de acontecer a seguir. Escrito para quem não esteve na reunião.]

---

## Decisões tomadas

| # | Decisão | Tomada por | Confiança |
|---|---------|------------|-----------|
| D-001 | [Frase da decisão] | [Nome] | [Alta/Média/Baixa] |

---

## Tarefas

| # | Tarefa | Responsável | Prazo | Prioridade | Tipo |
|---|--------|-------------|-------|------------|------|
| A-001 | [Frase da tarefa] | [Nome] | [Data] | [A/M/B] | [Tipo] |

### Compromissos implícitos detetados

Estes itens não foram apresentados como tarefas, mas representam compromissos assumidos durante a reunião:

| # | Compromisso | Quem o disse | Citação original |
|---|-------------|--------------|------------------|
| A-XXX | [Tarefa interpretada] | [Nome] | "[citação exata]" |

---

## Questões em aberto

| # | Questão | Levantada por | Atribuída a | Prazo |
|---|---------|---------------|-------------|-------|
| Q-001 | [Questão] | [Nome] | [Nome] | [Data] |

---

## Parque de estacionamento

| Assunto | Levantado por | Seguimento |
|---------|---------------|------------|
| [Assunto] | [Nome] | [Quando/Onde] |

---

## Notas da discussão

### [Assunto 1]
[Resumo da discussão]

### [Assunto 2]
[Resumo da discussão]
```

## Resultado 2: Ficheiros de tarefas individuais

Gera um ficheiro por tarefa, num formato compatível com a ferramenta de gestão de projetos da pessoa. Só quando a pessoa o pedir. Os nomes dos campos (por exemplo `title`, `assignee`) ficam em inglês, para continuarem compatíveis com as ferramentas.

### Formato compatível com o Linear (tasks/linear/)

```markdown
---
title: "[Título da tarefa]"
assignee: "[Nome do responsável]"
priority: "[urgent|high|medium|low]"
status: "Todo"
labels: ["meeting-action", "[projeto]"]
due_date: "[AAAA-MM-DD]"
---

## Descrição

[Descrição detalhada da tarefa]

## Contexto

Esta tarefa surgiu na reunião [Título da reunião] de [Data].

**Citação original**: "[Citação da transcrição]"

**Decisões relacionadas**: [Lista das decisões relacionadas]

## Critérios de aceitação

- [ ] [Critério específico 1]
- [ ] [Critério específico 2]

## Dependências

- [Lista de dependências]
```

### Formato GitHub Issues (tasks/github/)

```markdown
---
title: "[Título da tarefa]"
assignees: ["[nome-de-utilizador-github]"]
labels: ["meeting-action", "[prioridade]"]
milestone: "[se aplicável]"
---

## Descrição

[Descrição detalhada]

## Contexto

De: [Título da reunião] ([Data])
Responsável: [Nome]
Prazo: [Data]
Prioridade: [Prioridade]

## Tarefas

- [ ] [Subtarefa 1]
- [ ] [Subtarefa 2]

## Relacionado

- Decisão: [Decisão relacionada]
- Reunião: [Ligação ao resumo da reunião]
```

### Formato genérico de tarefa (tasks/generic/)

```yaml
task:
  id: "A-001"
  title: ""
  description: ""
  owner: ""
  deadline: ""
  priority: ""
  status: "open"
  tags: []
  subtasks: []
  notes: ""
  source: "Reunião: [Título] em [Data]"
```

## Resultado 3: Rascunho do e-mail de seguimento (follow-up-email.md)

```markdown
Assunto: [Título da reunião] - Resumo e tarefas ([Data])

Olá a todos,

Obrigado pela reunião de hoje. Fica o resumo do que abordámos,
das decisões que tomámos e das tarefas, com responsáveis e prazos.

## Decisões principais
[Lista numerada das decisões]

## Tarefas
[Tabela de tarefas com responsáveis e prazos]

## Questões em aberto
[Lista das questões que ainda precisam de resposta]

## Próxima reunião
[Data/hora da próxima reunião, se conhecida]

Peço que revejam as tarefas que vos foram atribuídas e me digam se algum
prazo precisa de ser ajustado.

Cumprimentos,
[Nome]
```
