# Esquema de extração

Campos estruturados a capturar em cada fase da extração. Guarda sempre a citação exata de origem que deu lugar a cada item. Os nomes dos campos mantêm-se em inglês (são nomes técnicos); os comentários e os valores de exemplo estão em português.

## Fase 1: Metadados da reunião

```yaml
meeting:
  title: ""                # Inferido do conteúdo ou perguntado
  date: ""                 # Extraída ou a data de hoje
  duration: ""             # Se disponível
  type: ""                 # diária, planeamento, revisão, brainstorming, 1:1, plenário, cliente, etc.
  participants:
    - name: ""
      role: ""             # Inferido do contexto (moderador, apresentador, decisor, etc.)
  agenda_items: []         # Se foi referida uma agenda
  context: ""              # Breve descrição do assunto da reunião
```

## Fase 2: Decisões

```yaml
decisions:
  - id: "D-001"
    decision: ""           # Frase clara do que foi decidido
    context: ""            # O que levou a esta decisão
    made_by: ""            # Quem tomou ou confirmou a decisão
    participants: []       # Quem estava presente na decisão
    confidence: ""         # alta, média, baixa (quão claramente foi uma decisão?)
    conditions: ""         # Condições ou ressalvas
    reversibility: ""      # fácil, moderada, difícil (pode ser desfeita?)
    source_quote: ""       # Citação exata da transcrição
```

## Fase 3: Tarefas

```yaml
action_items:
  - id: "A-001"
    title: ""              # Frase clara e concisa da tarefa (modo imperativo)
    description: ""        # Descrição detalhada com contexto
    owner: ""              # Pessoa responsável
    collaborators: []      # Outras pessoas envolvidas
    deadline: ""           # Prazo explícito, prazo inferido ou "A DEFINIR"
    priority: ""           # alta, média, baixa (inferida dos sinais de urgência)
    status: "open"         # open, in-progress, blocked, done
    type: ""               # tarefa, pesquisa, decisão necessária, seguimento, comunicação
    dependencies: []       # Outras tarefas de que esta depende
    related_decisions: []  # IDs das decisões a que esta tarefa se liga
    commitment_type: ""    # explícito, implícito, inferido
    source_quote: ""       # Citação exata da transcrição
    confidence: ""         # alta, média, baixa (quão certo é que isto é uma tarefa?)
    project: ""            # Projeto ou frente de trabalho a que pertence
    tags: []               # Etiquetas de categorização
```

## Fase 4: Questões em aberto

```yaml
open_questions:
  - id: "Q-001"
    question: ""           # A pergunta tal como foi feita
    raised_by: ""          # Quem perguntou
    context: ""            # Porque importa
    assigned_to: ""        # Quem deve responder (se identificado)
    deadline: ""           # Quando é preciso uma resposta
    related_items: []      # Decisões ou tarefas relacionadas
    source_quote: ""
```

## Fase 5: Parque de estacionamento (assuntos adiados)

```yaml
parking_lot:
  - id: "P-001"
    topic: ""
    raised_by: ""
    reason_deferred: ""    # Porque não foi tratado
    follow_up_meeting: ""  # Quando deve ser retomado
```

## Fase 6: Pontos principais da discussão

```yaml
discussion_points:
  - topic: ""
    summary: ""            # Resumo em 2 a 3 frases
    participants: []       # Quem contribuiu
    outcome: ""            # decisão, tarefa, adiado, informativo
    time_spent: ""         # estimado, se houver marcas de tempo
```
