# MISSÃO 2 — INVESTIGAÇÃO FOCALIZADA E REGISTRO OBRIGATÓRIO DAS FOTOS

Você está no repositório de uma sociedade que possui uma máquina física de pegar pelúcias e pretende controlá-la pelo navegador. Já houve uma primeira investigação. Agora aprofunde a pesquisa em evidências reais, sem repetir dez relatórios superficiais.

## PRIMEIRA OBRIGAÇÃO: PERSISTIR AS FOTOGRAFIAS NO PROJETO

Antes de qualquer análise ou pesquisa:

1. Identifique todas as fotografias originais recebidas como anexos desta conversa, em ZIP ou já presentes no diretório. Localize e leia os arquivos reais; não considere miniaturas ou imagens apenas descritas como arquivos disponíveis.
2. Crie, se necessário, `evidencias/fotos/`, `evidencias/dossie/` e `docs/`, sob a raiz do projeto atual.
3. Copie as 37 fotos originais, preservando os bytes, de preferência com seus nomes originais, para `evidencias/fotos/`. Quando estiverem em ZIP, extraia os arquivos de imagem, ignorando `__MACOSX`, `.DS_Store` e outros metadados que não sejam imagens. **Não** converta, comprima, redimensione, renomeie em lote ou sobrescreva arquivos distintos.
4. Persista o dossiê recebido em `evidencias/dossie/`; se ele já estiver corretamente nessa pasta, apenas confira sua presença. O relatório preliminar deve permanecer identificável.
5. Gere ou atualize `evidencias/manifest_fotos.csv` com: nome, tamanho em bytes, dimensão, SHA-256, origem e status de leitura visual. Liste o total de fotos originais únicas e confira se são 37; caso haja contagem diferente, diagnostique faltantes/duplicatas.
6. Abra visualmente cada uma das fotos originais. Não marque como revisada uma imagem que a ferramenta não conseguiu abrir. Use recortes não destrutivos em pasta separada quando necessário. Não invente texto ilegível.
7. Antes de avançar, relate: número de imagens originais persistidas, caminhos reais, conferência de integridade e quais arquivos não foram acessíveis. Se anexos estiverem disponíveis só no contexto visual mas não no sistema de arquivos, **não alegue que os salvou**: explique qual ZIP ou caminho local preciso fornecer, e continue apenas com arquivos efetivamente acessíveis.

## INVESTIGAÇÃO TÉCNICA

Consulte os documentos de fases anteriores em `docs/` e releia `evidencias/dossie/dossie_tecnico_inicial.md`. Trate o dossiê como material secundário e valide todas as conclusões contra as imagens originais.

Investigue com autonomia, separando CONFIRMADO / PROVÁVEL / NÃO IDENTIFICADO:

A) **Controladora e fabricante:** identifique a PCB verde com sete relés, o chip com etiqueta PG01, serigrafias, circuitos integrados e conectores. Pesquise manuais, datasheets e referências em português, inglês e chinês. Não confunda a arte Fun Time com comprovação do fabricante nem PG01 com modelo confirmado da PCB.

B) **Interface digital candidata:** a placa exibe `12V`, `GND`, `RXD`, `TXD`, `5V`. Investigue finalidade, possíveis modelos de comunicação e circuitos relacionados. Não presuma UART TTL, RS-232, protocolo ou suporte a controle de movimento apenas pelas inscrições. Priorize documentação verificável; descreva a futura validação segura necessária.

C) **Joystick e botão:** identifique mecanismos, sinais e chicotes visíveis, hipóteses de entradas da controladora e alternativas para simular comandos preservando o painel físico. Não atribua pinagem ou tensão por cor de fio e não escolha relés automaticamente. Explique, com precisão, qual fotografia faltante ou medição profissional distingue hipóteses concorrentes.

D) **Créditos e prêmios:** investigue moedeiro `CPU Electronic Comparable Coin Mech`, os chicotes `CRÉDITO` e `PRÊMIO` e o possível caminho até a controladora. Etiquetas não provam direção/tipo elétrico dos sinais. Diferencie início de partida, término, confirmação de captura e detecção de prêmio.

E) **Câmera:** avalie se o dispositivo interno visível pode servir para streaming ao navegador; sem inventar marca/modelo/protocolo/latência.

F) **Uso do REA:** verifique se há firmware, executáveis, software proprietário ou capturas de sinais acessíveis que justifiquem `morluto/rea`. Use se instalado e relevante; não instale nem modifique configurações sem aprovação, nem confunda REA com interpretação visual de hardware.

G) **Arquitetura:** compare interface isolada que reproduza comandos existentes, protocolo digital nativo comprovado e substituição parcial como último recurso. Considere controle de exclusividade por jogador, timeout, parada segura, falhas de comunicação, registro de crédito/prêmio e fluxo de vídeo independente. Não compre ou acione hardware.

## MÉTODO E CRITÉRIO DE QUALIDADE

- Pesquise ativamente hipóteses de identificação da placa, incluindo buscas multilíngues, mas registre consultas, fontes e limitações; sem confundir parecidos com mesmo modelo.
- Apresente sempre arquivo da foto / recorte / detalhe que sustenta uma inferência.
- Não use números de pinagem, esquemas ou procedimentos de ligação não comprovados. Não realize testes em eletrônica energizada, não acione relés ou motores, não ligue GPIOs em circuitos desconhecidos e não sugira desativar proteções.
- Prefira descoberta técnica nova e auditável a volume de texto. Não repita o conteúdo antigo como novidade.
- Se houver limites físicos impossíveis de superar por foto, descreva exatamente a lacuna e uma única forma segura de obtê-la por profissional competente.

## ENTREGÁVEIS

Atualize apenas `evidencias/manifest_fotos.csv` e crie:

- `docs/11-investigacao-focalizada.md`: evidências por arquivo, fabricante/placa, RXD/TXD, joystick, créditos/prêmios, câmera, REA, novas descobertas versus a fase anterior e links consultados.
- `docs/12-plano-prova-de-conceito.md`: alternativas comparadas por custo, compatibilidade, risco, reversibilidade e dados faltantes; arquitetura proposta; testes em bancada isolada e validação elétrica profissional; critérios de sucesso antes de qualquer compra ou adaptação.

Termine no terminal com um resumo curto: total de fotos persistidas, cinco descobertas mais relevantes, hipóteses descartadas, o melhor caminho de integração A/B/C e a única próxima evidência prioritária. Não construa ainda o site, não instale ferramentas sem aprovação e não acione a máquina.
