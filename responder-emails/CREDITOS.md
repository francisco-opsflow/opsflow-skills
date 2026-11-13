# Créditos

Esta skill é uma tradução e adaptação para português de Portugal da skill **cowork-inbox-triage**.

- **Autor original:** OneWave AI
- **Repositório:** https://github.com/onewave-ai/claude-skills (pasta `cowork-inbox-triage`)
- **Licença:** MIT -- Copyright (c) 2025 OneWave AI (texto completo no ficheiro `LICENSE`, que acompanha esta skill e não pode ser retirado)

Os autores originais não revêem nem apoiam esta versão.

## Alterações em relação ao original

1. Tradução e adaptação do texto para português de Portugal.
2. **Removido o arquivo de mensagens.** A skill já não arquiva nem etiqueta nada, nem aplica regras de arquivo automático; a categoria "ruído" apenas é contada no resumo.
3. **Removidos os bloqueios de calendário.** A skill já não cria nem propõe eventos; as datas encontradas são só referidas no resumo.
4. A única alteração à caixa de correio passa a ser a criação de rascunhos.
5. Cabeçalho simplificado (`name`, `description`, `license`) para ser compatível com o carregamento de skills no Claude.
