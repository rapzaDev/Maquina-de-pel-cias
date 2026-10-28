# Instruções do pacote - Projeto Máquina de Pelúcia

Este pacote contém as 37 fotografias originais (sem alteração dos bytes), o dossiê derivado e o prompt da segunda etapa.

## Estrutura da pasta

- `evidencias/fotos/`: 37 JPEGs originais com nomes preservados.
- `evidencias/dossie/`: relatório técnico preliminar, painel, ampliação de trechos e placa anotada.
- `evidencias/manifest_fotos.csv`: SHA-256, tamanho, dimensão e nome para auditoria.
- `PROMPT_ETAPA_2_CODEX.md`: prompt autossuficiente para passar ao Codex.
- `docs/`: destino dos relatórios produzidos pelo Codex (a criar se não existir).

## Ingestão e integridade

Se você copiar o ZIP para o repositório e mandar o Codex descompactá-lo, instrua o agente a mesclar os arquivos neste formato sem sobrescrever arquivos existentes diferentes. Para conferir integridade, o agente deve calcular SHA-256 e comparar com `evidencias/manifest_fotos.csv`.

As marcações do dossiê são HIPÓTESES e não comprovam pinagem, tensões de entrada, protocolo ou fabricante da máquina. Analise sempre as fotografias originais. Não conecte eletrônica desconhecida à máquina sem validação profissional.
