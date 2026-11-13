---
name: voz-dna
description: Extrai uma voz de escrita portátil a partir de textos reais da pessoa. Usa quando pedirem ao Claude para escrever como elas, aprender o seu estilo, criar um guia de voz ou perceber porque é que a voz se foi desviando. Aceita 3 a 5 textos próprios (e-mails, publicações, mensagens) e devolve uma skill de escrita que a pessoa pode guardar e editar.
license: MIT
---

# Voz DNA

## O trabalho

Transforma os textos reais que a pessoa tiver disponíveis numa skill de voz de escrita portátil, que passa a ser dela. Três a cinco textos variados dão uma base mais forte, mas pouca evidência não impede o trabalho.

## Porque é que o resultado é um ficheiro de skill

Um resumo de estilo cola-se uma vez e perde-se. Um ficheiro de skill é infraestrutura reutilizável, para as ferramentas que suportam skills. As regras de voz são portáteis, mas os locais de instalação e os formatos aceites variam consoante a ferramenta. A pessoa fica com um recurso editável, não com um conselho.

## Como executar

1. Recolhe a escrita genuína que existir. Bons exemplos: e-mails enviados, publicações, mensagens para colegas e tudo o que tenha sido escrito sobretudo por palavras da própria pessoa. Procura 3 a 5 textos em pelo menos dois contextos, mas continua mesmo com menos:
   - `Evidência forte`: 3 a 5 textos variados. Constrói o perfil completo.
   - `Evidência provisória`: 1 a 2 textos, textos curtos ou um só contexto. Constrói um perfil inicial utilizável, indica o grau de confiança e identifica o que precisa de confirmação.
   - `Sem textos`: pede à pessoa que escreva uma mensagem curta e natural, ou que responda a duas ou três perguntas pelas suas palavras, e constrói depois um perfil provisório.
   Textos escritos com ajuda de IA só contam se a pessoa indicar quais as partes que ainda soam a ela. Não rejeites o trabalho todo por a evidência ser pouca.

2. Analisa estas dimensões, citando evidência dos textos em cada conclusão:
   - **Registo**: como soa, numa frase, dita como comparação ("um amigo atento a explicar ao café", não "conversacional").
   - **Ritmo**: distribuição do comprimento das frases, onde corta parágrafos, se avança logo com o essencial ou se o vai construindo.
   - **Impressão digital do vocabulário**: 5 a 8 palavras ou construções a que recorre; 3 a 5 que nunca usa.
   - **Marcas próprias**: padrões repetíveis sustentados pelos textos ("abre com a objeção que o leitor já está a pensar", não "aberturas cativantes"). Não forces três se a evidência sustentar menos.
   - **Regras de nunca**: 3 a 5 coisas que quebrariam logo a voz, incluindo hábitos de pontuação (há quem nunca use ponto e vírgula; há quem nunca escreva parágrafos de uma só frase).
   - **Hábitos de formatação**: listas ou prosa, quebras de linha, maiúsculas peculiares, política de emojis.
   Separa as **constantes da voz**, que surgem em todos os contextos, dos **hábitos de cada contexto**, como a estrutura formal de um e-mail a um cliente ou os fragmentos informais de uma publicação nas redes.

3. Mostra a análise, a confiança em cada conclusão importante e as lacunas. Deixa a pessoa corrigir. Ela conhece a sua voz; os textos são evidência, não veredicto. Incorpora as correções.

4. Gera o resultado: um ficheiro de skill completo e válido, com o nome da pessoa (por exemplo `ana-voz-de-escrita`), com:
   - Cabeçalho YAML: `name` em minúsculas com hífenes (máximo 64 caracteres) e `description` com menos de 1024 caracteres, a dizer quando aplicar a voz.
   - Secções: Resumo da voz, Confiança e evidência, Constantes da voz, Hábitos por contexto, Regras de ritmo, Vocabulário (usa / nunca), Marcas próprias, Regras de nunca, e um par curto de antes/depois tirado dos textos da pessoa (formulação genérica de IA vs. a formulação dela).
   - Num perfil provisório, marca as regras incertas como provisórias dentro do ficheiro, para continuar útil sem fingir que a evidência está completa.

5. Prova que funciona: escreve um parágrafo curto sobre um tema que a pessoa escolha, uma vez na voz por defeito da IA e outra com a nova skill, lado a lado. Deixa-a sentir a diferença. Se falhar, ajusta o ficheiro e mostra as diferenças.

6. Explica como o instalar na ferramenta que a pessoa realmente usa. Verifica, quando possível, o formato e a localização atuais de skills dessa ferramenta, em vez de afirmar que todas instalam skills da mesma maneira. O ficheiro é dela: portátil na substância, editável e independente desta skill.

## Limites

- A análise e o ficheiro gerado ficam na conversa e no computador da pessoa; nada é enviado para lado nenhum.
- Nunca inventes padrões que os textos não mostram. Evidência escassa deve ser sinalizada como tal ("só um texto mostra isto; confirma se és mesmo tu").
- Nunca recuses criar um Voz DNA inicial só porque a pessoa tem menos de três textos.
- Nunca afirmes que o ficheiro captura tudo; a voz muda e o ficheiro é editável. Sugere repetir o processo passados alguns meses de uso real.
- Mantém uma voz central por execução. Regista as variações de contexto dentro dela; separa em skills diferentes apenas quando as vozes divergirem mesmo e a pessoa quiser essa separação.

Inspirada no padrão emergente de skills de análise de voz do ecossistema Claude; reconstruída para escritores não técnicos, com um ficheiro de skill portátil como resultado.

---

Baseada na skill `voice-dna` (nahiddotai, licença MIT). Ver `CREDITOS.md` e `LICENSE`.
