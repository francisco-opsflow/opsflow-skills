# Marcadores de deteção e regras de inferência

Tabelas de consulta para identificar decisões, tarefas e compromissos implícitos, mais as regras para inferir prioridade e prazos. Os exemplos estão em português; se a reunião decorrer noutra língua, aplica os equivalentes nessa língua.

## Marcadores de decisão

Marcadores explícitos:
- "Decidimos que..."
- "Vamos com..."
- "A decisão é..."
- "Vamos avançar com..."
- "Ficámos de acordo que..."
- "Fica decidido..."
- "A resposta final é..."
- "Aprovado."
- "Então avançamos com..."
- "Esse é o plano."

Marcadores implícitos:
- Consenso depois de debate: várias pessoas concordam numa direção após a discussão
- Declaração de quem lidera: uma pessoa sénior indica a direção sem objeções
- Aprovação por silêncio: é feita uma proposta e ninguém levanta objeções
- Decisão condicional: "Se X, então fazemos Y"

## Marcadores de tarefa

Marcadores explícitos:
- "Eu vou..."
- "Podes [fazer X]?"
- "Vamos [fazer X] até [data]"
- "O [Nome] vai..."
- "Tarefa: ..."
- "A fazer: ..."
- "O próximo passo é..."
- "Temos de..."
- "Garante que..."
- "Fazer seguimento de..."
- "Marcar uma..."
- "Enviar [algo] ao [alguém]"
- "Atualizar [algo]"
- "Rever [algo]"
- "Preparar [algo]"
- "Configurar [algo]"

Marcadores de compromisso implícito (essenciais -- muitas vezes as pessoas não percebem que se comprometeram):
- "Vou ver isso" = TAREFA: pesquisar e dar retorno
- "Deixa-me confirmar" = TAREFA: investigar e partilhar o que encontrar
- "Se calhar consigo..." = TAREFA: tentar e confirmar
- "Devíamos..." (dito por quem tem autoridade) = TAREFA: fazer
- "Boa ideia, vou pensar nisso" = TAREFA: ponderar e responder
- "Depois volto a isso" = TAREFA: fazer seguimento
- "Vou falar com o [pessoa]" = TAREFA: ter a conversa e dar retorno
- "Acho que precisamos de..." (com concordância do grupo) = TAREFA: dar início
- "Sim, eu faço isso" = TAREFA: aceitação explícita
- "Fico eu com isso" / "Trato disso" = TAREFA: responsabilidade assumida
- "Depois logo se vê" = TAREFA: precisa de ser decomposta em tarefas concretas
- "Depois dou-te um toque" = TAREFA: enviar comunicação de seguimento
- "Já te envio isso" = TAREFA: entregar o material

## Regras de inferência de prioridade

- ALTA: referida como urgente, bloqueia outro trabalho, tem prazo apertado ou foi pedida por um responsável sénior
- MÉDIA: tarefa normal com prazo, parte do fluxo habitual de trabalho
- BAIXA: desejável, exploratória, sem prazo mencionado

## Regras de inferência de prazos

- Explícito: "até sexta", "antes da próxima reunião", "até ao fim da semana"
- Inferido do contexto: "antes do lançamento" (se a data do lançamento for conhecida), "antes do próximo sprint"
- Cadência das reuniões: numa reunião semanal, o prazo por defeito é "antes da próxima reunião" (1 semana)
- Se não houver qualquer sinal de prazo: marca como "A DEFINIR" e pede ao responsável que o defina

## Pontuação de confiança

- ALTA: afirmação clara e explícita. Pessoa identificada. Significado inequívoco.
- MÉDIA: inferência razoável a partir do contexto. Pessoa identificável. O significado provavelmente está certo, mas podia ser interpretado de outra forma.
- BAIXA: compromisso implícito ou afirmação ambígua. A pessoa pode não estar clara. Assinala para revisão humana.

Para os itens de confiança BAIXA, assinala sempre para revisão:

```
[CONFIANÇA BAIXA] Os itens seguintes foram extraídos mas podem não estar corretos.
Por favor revê e confirma ou remove:

- A-XXX: [Tarefa] - Atribuída a [Nome]
  Motivo da confiança baixa: [Explicação]
  Citação original: "[Citação]"
```
