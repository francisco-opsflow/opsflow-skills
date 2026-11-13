---
name: passa-a-limpo
description: "Passa a limpo a conversa que está a decorrer: quando a pessoa diz 'passa a limpo', usa o tema e o contexto do chat atual e põe-no à prova com um conselho de 5 conselheiros de IA que analisam em separado, avaliam-se uns aos outros de forma anónima e terminam num veredicto final. Baseado no LLM Council de Karpathy. GATILHO OBRIGATÓRIO: 'passa a limpo' (também 'passa isto a limpo', 'passa a limpo isto'). GATILHOS SECUNDÁRIOS (só quando há uma decisão real com custos e alternativas): 'põe isto à prova', 'testa isto ao limite', 'debate isto', 'estou dividido entre', 'não consigo decidir', 'qual das opções', 'o que farias', 'é este o caminho certo', 'valida isto', 'quero várias perspetivas'. NÃO ativar em perguntas simples de sim/não, consultas de factos, nem num 'devo' casual sem um compromisso real (por exemplo, 'devo usar markdown' não é uma questão para o conselho)."
---

# Passa a limpo (Conselho de IA)

Se fizeres uma pergunta a uma IA, recebes uma resposta. Pode ser ótima. Pode ser medíocre. Não tens forma de saber, porque só viste uma perspetiva.

O conselho resolve isto. Leva a questão a 5 conselheiros independentes, cada um a pensar a partir de um ângulo radicalmente diferente. Depois, avaliam o trabalho uns dos outros. No fim, um presidente sintetiza tudo numa recomendação que diz onde os conselheiros concordam, onde divergem e o que deves mesmo fazer.

A ideia vem do LLM Council de Andrej Karpathy: ele envia a mesma pergunta a vários modelos, pede-lhes que se avaliem de forma anónima e um presidente produz a resposta final. Aqui fazemos o mesmo dentro do Claude, com subagentes que usam lentes de pensamento diferentes em vez de modelos diferentes.

---

## Como é ativada

Esta skill corre **no chat onde estás a conversar**. Quando a pessoa escreve "passa a limpo" a meio de uma conversa, a pergunta a levar ao conselho é **o assunto que estava a ser discutido** nesse chat: as opções em cima da mesa, os números, as restrições e o que a pessoa já disse. Não pedes que repita a pergunta, e não recomeças do zero.

- Se "passa a limpo" vem acompanhado de texto ("passa a limpo: devo lançar o curso a 297 €?"), esse texto é a pergunta, completada com o contexto do chat.
- Se vem sozinho, a pergunta é a decisão ou ideia que a conversa em curso estava a tratar. Resume-a numa linha no início ("Vou levar ao conselho: ...") para a pessoa poder corrigir, e segue em frente sem esperar.
- Se o chat ainda não tem nenhuma decisão ou ideia clara, faz **uma única** pergunta ("O que queres que eu passe a limpo?") e prossegue com a resposta.

---

## Quando correr o conselho

O conselho serve para perguntas em que errar sai caro.

Boas perguntas para o conselho:

- "Devo lançar um workshop a 97 € ou um curso a 497 €?"
- "Qual destes 3 posicionamentos é o mais forte?"
- "Estou a pensar mudar de X para Y. Estou maluco?"
- "Este é o texto da minha página de destino. O que está fraco?"
- "Devo contratar uma assistente virtual ou construir primeiro uma automatização?"

Más perguntas para o conselho:

- "Qual é a capital de França?" (uma só resposta certa, não precisa de perspetivas)
- "Escreve-me uma publicação" (tarefa de criação, não uma decisão)
- "Resume este artigo" (tarefa de processamento, não de julgamento)

O conselho brilha quando há incerteza genuína e o custo de uma má decisão é alto. Se já sabes a resposta e só queres validação, o conselho provavelmente vai dizer-te o que não queres ouvir. É essa a ideia.

---

## Os cinco conselheiros

Cada conselheiro pensa a partir de um ângulo diferente. Não são cargos nem personagens: são estilos de pensamento que criam tensão entre si de forma natural.

### 1. O Contrariador

Procura ativamente o que está errado, o que falta e o que vai falhar. Parte do princípio de que a ideia tem uma falha fatal e tenta encontrá-la. Se tudo parecer sólido, escava mais fundo. O Contrariador não é um pessimista: é o amigo que te livra de um mau negócio ao fazer as perguntas que estás a evitar.

### 2. O Pensador de Primeiros Princípios

Ignora a pergunta à superfície e pergunta "o que estamos mesmo a tentar resolver aqui?". Tira os pressupostos e reconstrói o problema de raiz. Por vezes, o resultado mais valioso do conselho é este conselheiro dizer "estás a fazer a pergunta errada".

### 3. O Expansionista

Procura o potencial que os outros não vêem. O que podia ser maior? Que oportunidade vizinha está escondida? O que está a ser subvalorizado? O Expansionista não se preocupa com o risco (isso é trabalho do Contrariador). Preocupa-se com o que acontece se isto correr ainda melhor do que o esperado.

### 4. O Forasteiro

Não tem qualquer contexto sobre ti, a tua área ou o teu historial. Reage apenas ao que tem à frente. É o conselheiro mais subestimado. Os especialistas criam pontos cegos, e o Forasteiro apanha a maldição do conhecimento: o que é óbvio para ti e confuso para toda a gente.

### 5. O Executor

Só quer saber de uma coisa: isto pode mesmo ser feito e qual é o caminho mais rápido? Ignora a teoria, a estratégia e a visão de conjunto. O Executor olha para cada ideia com a pergunta "ótimo, mas o que fazes na segunda-feira de manhã?". Se uma ideia parece brilhante mas não tem um primeiro passo claro, o Executor di-lo.

**Porquê estes cinco:** criam três tensões naturais. O Contrariador contra o Expansionista (risco contra potencial). Os Primeiros Princípios contra o Executor (repensar tudo contra simplesmente fazer). O Forasteiro fica no meio, a manter todos honestos com o olhar de quem chega de fora.

---

## Como decorre uma sessão do conselho

### Passo 1: enquadrar a questão (com enriquecimento de contexto)

Quando a pessoa diz "passa a limpo" (ou outro gatilho), faz duas coisas antes de enquadrar:

**A. Reúne o contexto.** A pergunta é muitas vezes só a ponta do icebergue. Antes de enquadrar, junta o que melhora a qualidade do conselho:

- **A conversa em curso.** É a fonte principal. Recolhe o que já foi dito: opções, números, restrições, objetivos, o que já foi tentado e o que a pessoa já descartou.
- Os ficheiros que a pessoa tenha anexado ou referido.
- Se estiveres num ambiente com ficheiros (por exemplo, Claude Code), um `CLAUDE.md` ou `claude.md` na raiz do projeto, uma pasta `memory/` ou outros ficheiros que ajudem a questão em causa (por exemplo, dados de receitas se a pergunta for sobre preços). Não gastes mais de 30 segundos nisto.
- A memória do Claude, se estiver ligada e for relevante.

Procura os 2 ou 3 elementos que dão aos conselheiros o contexto necessário para conselhos específicos e fundamentados, em vez de opiniões genéricas.

**B. Enquadrar a questão.** Pega na pergunta e no contexto e reformula-os num pedido claro e neutro, que os cinco conselheiros vão receber. A questão enquadrada deve incluir:

1. A decisão ou pergunta central
2. O contexto relevante dito pela pessoa, incluindo o que veio da conversa
3. O contexto relevante dos ficheiros ou da memória (fase do negócio, público, restrições, resultados anteriores, números)
4. O que está em jogo (porque é que esta decisão importa)

Não acrescentes a tua opinião. Não influencies. Mas garante que cada conselheiro tem contexto suficiente para dar uma resposta específica e fundamentada.

Se a pergunta for vaga demais ("passa a limpo: o meu negócio"), faz uma pergunta de esclarecimento. Só uma. Depois avança.

Guarda a questão enquadrada para a transcrição.

### Passo 2: convocar o conselho (5 subagentes em paralelo)

Lança os 5 conselheiros em simultâneo como subagentes. Cada um recebe:

1. A sua identidade de conselheiro e estilo de pensamento (das descrições acima)
2. A questão enquadrada
3. Uma instrução clara: responde de forma independente. Não faças ressalvas. Não tentes ser equilibrado. Assume por inteiro a tua perspetiva. Se vires uma falha fatal, di-lo. Se vires um potencial enorme, di-lo. O teu trabalho é representar o teu ângulo com a maior força possível. A síntese vem depois.

Cada conselheiro deve produzir uma resposta de 150 a 300 palavras. Suficiente para ser substancial, curta o suficiente para ser lida num relance.

**Se não tiveres subagentes disponíveis** (por exemplo, num chat sem a ferramenta de agentes): simula o conselho tu próprio, em duas passagens. Escreve primeiro as 5 respostas, cada uma isolada das outras e sem as consultar. Depois faz as avaliações cruzadas com as respostas anonimizadas. Diz à pessoa, numa linha, que o conselho correu sem subagentes.

**Modelo do pedido ao subagente:**

```
És [Nome do Conselheiro] num Conselho de IA.

O teu estilo de pensamento: [descrição do conselheiro acima]

Uma pessoa trouxe esta questão ao conselho:

---
[questão enquadrada]
---

Responde a partir da tua perspetiva. Sê direto e específico. Não faças ressalvas nem tentes ser equilibrado. Assume por inteiro o teu ângulo. Os outros conselheiros cobrem os ângulos que tu não cobres.

Responde em português de Portugal, com 150 a 300 palavras. Sem preâmbulo. Entra logo na análise.
```

### Passo 3: avaliação cruzada (5 subagentes em paralelo)

Este é o passo que faz do conselho mais do que "perguntar 5 vezes". É o essencial da ideia de Karpathy.

Recolhe as 5 respostas dos conselheiros. Anonimiza-as como Resposta A a E (sorteia que conselheiro corresponde a cada letra, para não haver enviesamento de posição).

Lança 5 subagentes novos, um por cada conselheiro. Cada avaliador vê as 5 respostas anonimizadas e responde a três perguntas:

1. Qual é a resposta mais forte e porquê? (escolhe uma)
2. Qual é a resposta com o maior ponto cego e qual é esse ponto cego?
3. O que é que TODAS as respostas deixaram escapar e o conselho devia considerar?

**Modelo do pedido ao avaliador:**

```
Estás a avaliar os resultados de um Conselho de IA. Cinco conselheiros responderam, de forma independente, a esta questão:

---
[questão enquadrada]
---

Aqui estão as respostas anonimizadas:

**Resposta A:**
[resposta]

**Resposta B:**
[resposta]

**Resposta C:**
[resposta]

**Resposta D:**
[resposta]

**Resposta E:**
[resposta]

Responde a estas três perguntas. Sê específico. Refere as respostas pela letra.

1. Qual é a resposta mais forte? Porquê?
2. Qual é a resposta com o maior ponto cego? O que lhe falta?
3. O que é que TODAS as cinco respostas deixaram escapar e o conselho devia considerar?

Mantém a avaliação abaixo das 200 palavras, em português de Portugal. Sê direto.
```

### Passo 4: síntese do presidente

Este é o passo final. Um só agente recebe tudo: a questão original, as 5 respostas dos conselheiros (agora desanonimizadas, para se ver quem disse o quê) e as 5 avaliações cruzadas.

O trabalho do presidente é produzir o resultado final do conselho, com esta estrutura:

**VEREDICTO DO CONSELHO**

1. **Onde o conselho concorda**: os pontos em que vários conselheiros convergiram de forma independente. São sinais de alta confiança.
2. **Onde o conselho diverge**: os desacordos genuínos. Não os suavizes. Apresenta os dois lados e explica porque é que conselheiros razoáveis discordam.
3. **Pontos cegos que o conselho apanhou**: o que só surgiu na avaliação cruzada. O que conselheiros individuais deixaram escapar e outros assinalaram.
4. **A recomendação**: uma recomendação clara e acionável. Não "depende". Não "considera os dois lados". Uma resposta a sério. O presidente pode discordar da maioria se o raciocínio o justificar.
5. **A primeira coisa a fazer**: um único próximo passo concreto. Não uma lista de 10 coisas. Uma só.

**Modelo do pedido ao presidente:**

```
És o Presidente de um Conselho de IA. O teu trabalho é sintetizar o trabalho de 5 conselheiros e das suas avaliações cruzadas num veredicto final.

A questão levada ao conselho:

---
[questão enquadrada]
---

RESPOSTAS DOS CONSELHEIROS:

**O Contrariador:**
[resposta]

**O Pensador de Primeiros Princípios:**
[resposta]

**O Expansionista:**
[resposta]

**O Forasteiro:**
[resposta]

**O Executor:**
[resposta]

AVALIAÇÕES CRUZADAS:

[as 5 avaliações]

Produz o veredicto do conselho com esta estrutura exata, em português de Portugal:

## Onde o conselho concorda
[Pontos em que vários conselheiros convergiram de forma independente. São sinais de alta confiança.]

## Onde o conselho diverge
[Desacordos genuínos. Apresenta os dois lados. Explica porque é que conselheiros razoáveis discordam.]

## Pontos cegos que o conselho apanhou
[O que só surgiu na avaliação cruzada. O que conselheiros individuais deixaram escapar e outros assinalaram.]

## A recomendação
[Uma recomendação clara e direta. Não "depende". Uma resposta a sério, com o raciocínio.]

## A primeira coisa a fazer
[Um único próximo passo concreto. Não uma lista. Uma só coisa.]

Sê direto. Não faças ressalvas. O objetivo do conselho é dar à pessoa uma clareza que não conseguiria com uma única perspetiva.
```

### Passo 5: apresentar o veredicto no chat

Quando a síntese do presidente estiver pronta, apresenta o veredicto completo diretamente no chat, em markdown. **Não** geres relatórios em HTML nem ficheiros. A pessoa lê-o na conversa, que é onde o pediu.

Formato:

```
## Veredicto do conselho: {tema curto}

### Onde o conselho concorda
{conteúdo}

### Onde o conselho diverge
{conteúdo}

### Pontos cegos que o conselho apanhou
{conteúdo}

### A recomendação
{conteúdo}

### A primeira coisa a fazer
{conteúdo}
```

Mantém-no fácil de percorrer. Usa listas. Inclui exemplos de antes e depois quando fizerem sentido.

### Passo 6: guardar a transcrição (opcional)

Só guarda uma transcrição se a pessoa o pedir ou se a questão for importante o bastante para ser consultada mais tarde. Se guardares, escreve em `transcricao-conselho-[data-hora].md` na pasta `active/` do projeto, se existir, ou na pasta de trabalho. Em ambientes sem ficheiros, oferece-te para colar a transcrição no chat.

---

## Exemplo: passar a limpo uma decisão de produto

**Pessoa:** "Passa a limpo: estou a pensar criar um curso de 297 € sobre Claude Code para iniciantes. O meu público é sobretudo empreendedores a solo sem formação técnica. É a decisão certa?"

**O Contrariador:** "O mercado está inundado de cursos de Claude neste momento. A 297 €, estás a competir com conteúdo gratuito no YouTube. O teu público não é técnico, o que significa muito apoio ao cliente e risco de reembolsos. Quem pagaria 297 € provavelmente já passou da fase de iniciante..."

**O Pensador de Primeiros Princípios:** "O que estás realmente a tentar alcançar? Se é receita, um curso é um dos caminhos mais lentos. Se é autoridade, um recurso gratuito pode render mais. Se é construir uma base de clientes para ofertas mais caras, o preço e o público podem não encaixar..."

**O Expansionista:** "Claude para iniciantes empreendedores é um mercado enorme e mal servido. Toda a gente ensina o avançado. Se acertares no ângulo do iniciante, és dono do ponto de entrada de todo este espaço. 297 € pode ser pouco. E se isto se tornasse um programa de 997 € com acesso a uma comunidade..."

**O Forasteiro:** "Não sei o que é o Claude Code. Se visse 'curso de 297 € sobre Claude Code para iniciantes', não saberia se é para mim. O nome não diz nada a quem está fora do teu mundo. A tua página de venda tem de vender o resultado, não a ferramenta..."

**O Executor:** "Um curso completo demora 4 a 8 semanas a produzir como deve ser. Antes de construíres seja o que for, faz um workshop ao vivo a 97 € para 50 pessoas. Validas a procura, geras testemunhos e crias a matéria-prima do curso. Se 50 pessoas não compram o workshop, 500 não vão comprar o curso..."

**Veredicto do presidente:**

*Onde o conselho concorda:* O ângulo do empreendedor iniciante tem procura real, mas o enquadramento atual (um curso de Claude Code) é demasiado centrado na ferramenta e não vai ressoar com compradores não técnicos.

*Onde o conselho diverge:* O preço. O Contrariador diz que 297 € é caro face à concorrência. O Expansionista diz que é barato face ao valor. A resolução depende provavelmente de quanto apoio e acesso à comunidade vão incluídos.

*Pontos cegos apanhados:* O argumento do Forasteiro, de que "Claude Code" não diz nada ao comprador-alvo, é o contributo mais importante. Todos os conselheiros, exceto o Forasteiro, assumiram que o público já sabe o que isto é.

*Recomendação:* Não construas já o curso. Valida primeiro com uma oferta de menor compromisso. Mas muda o enquadramento por inteiro: vende o resultado (automatiza o teu negócio, ganha 10 horas por semana), não a ferramenta.

*A primeira coisa a fazer:* Fazer um workshop ao vivo a 97 €, chamado "Como automatizar a tua primeira tarefa de negócio com IA", para 50 pessoas. Não menciones o Claude Code no título.

---

## Notas importantes

- **Lança sempre os 5 conselheiros em paralelo.** Lançá-los em sequência desperdiça tempo e deixa as primeiras respostas contaminar as seguintes.
- **Anonimiza sempre para a avaliação cruzada.** Se os avaliadores souberem quem disse o quê, vão deferir a certos estilos de pensamento em vez de avaliar pelo mérito.
- **O presidente pode discordar da maioria.** Se 4 em 5 conselheiros disserem "faz" mas o raciocínio do dissidente for o mais forte, o presidente deve ficar do lado do dissidente e explicar porquê.
- **Não passes a limpo questões triviais.** Se a pessoa perguntar algo com uma só resposta certa, responde. O conselho é para a incerteza genuína em que várias perspetivas acrescentam valor.
- **O veredicto vive no chat.** A maioria das pessoas vai percorrer o veredicto, não ler a transcrição inteira. Mantém-no limpo e fácil de percorrer.
