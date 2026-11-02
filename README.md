# Motor de IA para Análise de Debates Eleitorais em Tempo Real
Pipeline em duas etapas criado para o projeto **TMC – CISO (Painel Interativo de Análise Eleitoral)**: transcreve debates ao vivo, identifica quem fala e usa IA para resumir o que cada candidato disse.
Painel publicado: https://ciso-espm.tmc.com.br/

## Etapa 1 – Captação e transcrição em tempo real
Notebook: `pipeline-transcrição.ipynb`
- **Captura de streaming:** `yt-dlp` e `ffmpeg` extraem o áudio de uma live do YouTube.
- **Identificação de falantes:** `pyannote.audio` gera a "impressão digital" de cada voz e compara por similaridade de cosseno com um banco de vozes cadastradas.
- **Transcrição:** `faster-whisper` (large-v3) em GPU, em blocos de 10 segundos, com horário e nome do falante.
Resultado: um debate de 2h processado em tempo real, no lugar de uma transcrição manual estimada em mais de 8h.

## Etapa 2 – Resumo com API de IA
Notebook: `resumo_com_API.ipynb`
Lê a transcrição e usa a **API do Gemini** para devolver, por candidato: temas principais, propostas, números citados e perguntas sem resposta.
- Exemplo de entrada: `transcricao_limpa.txt`
- Exemplo de resultado: `resumo_debate.md`

## Como usar
1. Rode a etapa 1 no Google Colab (GPU T4) para gerar a transcrição.
2. Guarde a chave da API em `GEMINI_API_KEY`, no Secrets do Colab.
3. Rode a etapa 2 apontando para o arquivo de transcrição.
