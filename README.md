# Pipeline de Transcrição e Diarização para Pesquisa em Profundidade

## O Problema
Pesquisadores e estudantes frequentemente lidam com entrevistas em profundidade que geram áudios ininterruptos de 1 a 2 horas. As alternativas gratuitas de transcrição (como IA de iOS ou transcritores de aplicativos de mensagens) apresentam gargalos técnicos severos:
- Não suportam arquivos pesados, exigindo o picote manual do áudio.
- Focam em mensagens curtas, perdendo a precisão de termos técnicos específicos e distorcendo o contexto.
- Falham na diarização (incapacidade de identificar quem é o entrevistador e quem é o entrevistado).

## A Solução
Este repositório contém um pipeline em Python focado em resolver esses gargalos sem depender de licenças de softwares proprietários caros. 
A arquitetura utiliza o `faster-whisper` (large-v3) para transcrição de alta precisão e o `pyannote.audio` para separação de locutores em tempo real. O sistema permite ensinar a máquina a reconhecer vozes específicas a partir de pequenos fragmentos de áudio (como mensagens de voz trocadas no agendamento da entrevista). O processamento ocorre localmente ou via instâncias de nuvem isoladas, garantindo a privacidade dos dados da pesquisa.
