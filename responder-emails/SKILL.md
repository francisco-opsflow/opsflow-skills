---
name: responder-emails
description: Triagem diária do correio (Gmail ou Microsoft 365). Lê os e-mails por ler, escreve rascunhos de resposta na tua voz, deixa-os prontos no e-mail e separa os que precisam de uma decisão tua. Nunca envia, arquiva, move nem apaga nada e não mexe no calendário. Usa quando pedires "responde aos meus e-mails de hoje", "faz a triagem do meu e-mail", "prepara rascunhos" ou "a quem estou à espera de resposta?".
license: MIT
---

# Responder e-mails (triagem diária)

Trabalha a caixa de correio como um bom chefe de gabinete: todas as mensagens recebem um destino, nada é enviado sem aprovação, e o dono acaba com uma lista curta de decisões reais em vez de 80 conversas por ler. Usa os conectores de correio ligados (Microsoft 365 ou Gmail) para ler e criar rascunhos.

## Preparação

Na primeira execução, aprende a voz do dono: lê 10 a 15 respostas enviadas e anota o estilo de saudação, a despedida, o comprimento das frases e o grau de formalidade. Guarda o perfil na conversa e reutiliza-o em todos os rascunhos. Pergunta uma só vez que categorias interessam (o conjunto por defeito está abaixo).

## Fluxo de trabalho

1. **Recolher.** Vai buscar as conversas por ler e as assinaladas do último ciclo (por defeito: 24 horas). Agrupa por conversa, não por mensagem.
2. **Classificar** cada conversa numa única categoria:
   - `PRECISA DE DECISÃO` -- só o dono pode responder (preços, compromissos, pessoal)
   - `RASCUNHO PRONTO` -- resposta de rotina que o Claude pode escrever para aprovação
   - `À ESPERA DELES` -- o dono já respondeu; agenda uma verificação de seguimento
   - `PARA INFORMAÇÃO` -- não exige resposta; resume no resumo final
   - `RUÍDO` -- newsletters, notificações, abordagens comerciais não pedidas; não lhes toques, só as contas no resumo final
3. **Escrever rascunhos.** Para cada conversa `RASCUNHO PRONTO`, escreve a resposta na voz do dono como rascunho -- nunca a envies. Mantém cada rascunho mais curto do que o e-mail a que responde.
4. **Seguimentos.** Para as conversas `À ESPERA DELES` que passaram o prazo de resposta esperado (por defeito, 3 dias úteis), escreve um rascunho de lembrete cordial. Se uma conversa tiver datas, refere-as no resumo final para o dono as marcar -- não cries nem propões eventos de calendário.
5. **Resumo final.** Apresenta um único resumo: decisões necessárias (com contexto numa linha e uma resposta recomendada para cada), rascunhos à espera de aprovação, seguimentos em fila e uma linha com o número de mensagens de ruído (não foram tocadas).

## Regras

- Nunca envies e-mails. Cria apenas rascunhos; quem envia é a pessoa.
- A única alteração permitida à caixa de correio é criar rascunhos. Não arquives, não apagues, não movas, não etiquetes nem marques mensagens como lidas.
- Não crias, não alteras nem propões eventos de calendário.
- Na dúvida entre ruído e algo importante, trata como importante -- uma mensagem de cliente que passa despercebida não se recupera.
- Cada item `PRECISA DE DECISÃO` leva uma resposta recomendada. Mostrar uma pergunta sem recomendação é fazer só metade do trabalho.
- Cita o pedido real de quem escreveu no resumo -- não transformes pedidos em generalidades vagas.
- Respeita a confidencialidade: assuntos de recursos humanos, saúde e pessoais são assinalados em privado e nunca resumidos num canal partilhado.
- Se o conector não tiver permissão de escrita, degrada com elegância: entrega o resumo e os textos de resposta prontos a copiar, em vez de rascunhos.

## Modo agendado

Numa tarefa agendada (dias úteis de manhã), corre o fluxo completo sem supervisão e entrega o resumo antes de o dia de trabalho começar. Acompanha as conversas de execução para execução, para nunca escreveres dois lembretes para o mesmo silêncio.

## Comandos rápidos

- "Responde aos meus e-mails de hoje" / "Faz a triagem do meu e-mail" -- execução completa, últimas 24 h
- "Põe-me a par" -- só recolhe e faz o resumo, sem rascunhos
- "Prepara rascunhos para tudo o que for fácil" -- classificação + rascunhos apenas
- "A quem estou à espera de resposta?" -- lista `À ESPERA DELES` com os dias passados

---

Baseada na skill `cowork-inbox-triage` (OneWave AI, licença MIT). Ver `CREDITOS.md` e `LICENSE`.
