# Motor de IA para Análise de Debates Eleitorais em Tempo Real

## O Contexto do Código
Este repositório contém o script original desenvolvido para o projeto **TMC - CISO (Painel Interativo de Análise Eleitoral)**. O objetivo foi criar um pipeline capaz de escutar um debate político ao vivo no YouTube, identificar quem estava falando e transcrever o discurso em tempo real.

Esse mesmo motor e arquitetura (que processa fluxos contínuos de áudio e separa locutores) serviu como base tecnológica para os meus estudos de transcrição em pesquisas qualitativas (Submissão ABEP).

## Como Funciona a Arquitetura
O sistema resolve o desafio de taguear múltiplas vozes em transmissões ao vivo de longa duração através das seguintes etapas integradas:
- **Captura de Streaming:** Integração de `yt-dlp` e `ffmpeg` para extrair o fluxo de áudio de forma contínua diretamente de uma live do YouTube.
- **Biometria de Voz (Diarização):** Uso do `pyannote.audio` para extrair embeddings vocais. O pipeline compara as vozes por similaridade de cosseno, tagueando automaticamente as falas de diferentes candidatos e mediadores com base em amostras de áudio cadastradas previamente.
- **Transcrição e Estruturação:** Processamento em tempo real com o modelo `faster-whisper` (large-v3) rodando em GPU para transformar o áudio diarizado em dados textuais estruturados.

## Execução
O código foi estruturado no Google Colab para aproveitar a aceleração de hardware (NVIDIA T4). Ele processa a transmissão em chunks de 10 segundos
