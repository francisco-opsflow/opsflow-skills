# Créditos

Esta skill é uma tradução e adaptação para português de Portugal da skill **meeting-to-tasks**.

- **Autor original:** OneWave AI
- **Repositório:** https://github.com/onewave-ai/claude-skills (pasta `meeting-to-tasks`)
- **Licença:** MIT -- Copyright (c) 2025 OneWave AI (texto completo no ficheiro `LICENSE`, que acompanha esta skill e não pode ser retirado)

Os autores originais não revêem nem apoiam esta versão.

## Alterações em relação ao original

1. Tradução do texto para português de Portugal, incluindo os ficheiros em `references/`.
2. Marcadores de decisão, tarefa e compromisso implícito adaptados a expressões em português (mantendo uma nota para reuniões noutras línguas).
3. Por defeito, os resultados (e-mail de seguimento, tarefas com datas e pontos por resolver) aparecem na conversa. Os ficheiros de tarefas para Linear/GitHub/genérico e a estrutura de pastas só são criados quando a pessoa os pede.
4. Aceita notas soltas com abreviaturas e pergunta quando não percebe uma delas.
5. Cabeçalho simplificado (`name`, `description`, `license`) para ser compatível com o carregamento de skills no Claude. Os nomes dos campos técnicos dos ficheiros de tarefas (por exemplo `title`, `assignee`) mantêm-se em inglês, para continuarem compatíveis com o Linear e o GitHub.
