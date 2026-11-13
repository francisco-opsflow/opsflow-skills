# Créditos

Esta skill é uma tradução e adaptação para português de Portugal da skill **llm-council**.

- **Autor da skill:** Ole Lehmann
- **Repositório de partilha:** https://github.com/aiwithremy/claude-skills-llm-council (publicado por Remy Gaskell)
- **Método original:** LLM Council, de Andrej Karpathy (https://github.com/karpathy/llm-council)
- **Licença:** o repositório original **não inclui ficheiro de licença**. Por isso, esta pasta não traz um `LICENSE` e não deve ser tratada como MIT. Se o autor original vier a indicar uma licença, esta nota deve ser atualizada.

Os autores originais não revêem nem apoiam esta versão.

## Alterações em relação ao original

1. Tradução e adaptação do texto para português de Portugal (tratamento por "tu", vocabulário e exemplos em euros).
2. Nome da skill alterado para `passa-a-limpo`.
3. Novo gatilho obrigatório: **"passa a limpo"**. Os gatilhos do original foram traduzidos e passaram a secundários.
4. Nova secção "Como é ativada": a skill corre no chat em curso e usa a conversa já existente como pergunta e contexto, sem pedir que a pessoa a repita.
5. Passo 1 alargado para usar a conversa e a memória do Claude como fontes de contexto, além dos ficheiros.
6. Acrescentado um modo sem subagentes, para chats que não têm essa ferramenta.
7. Os pedidos aos subagentes passaram a exigir resposta em português de Portugal.
8. Removida a última nota do original sobre um relatório em HTML, que contradizia o passo 5 (o veredicto é dado no chat, sem ficheiros).
9. Cabeçalho simplificado (`name` e `description`) para ser compatível com o carregamento de skills no Claude.
10. Sem alterações aos cinco conselheiros, à avaliação anónima nem à estrutura do veredicto.
