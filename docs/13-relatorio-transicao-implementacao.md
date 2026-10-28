# Relatório de transição — prontidão para implementação

Data: 28/10/2026. Base documental revisada: README, documentos `01` a `12` e dossiê preservado em `evidencias/dossie/`. Este relatório distingue fatos observados, hipóteses e trabalho que ainda exige levantamento físico profissional.

## Decisão executiva

O projeto **pode iniciar agora a implementação de software desacoplada da máquina** e a preparação da PoC em simulador. A integração física, firmware de GPIO para a unidade real, compra de interface ou qualquer comando remoto da máquina **não podem começar ainda**.

O caminho prioritário permanece **A — preservar a controladora original C02 e reproduzir exclusivamente as entradas do jogador por um adaptador reversível**. A base amarela do joystick é provavelmente um conjunto de contatos de lâmina, mas isso ainda não estabelece pinagem, comum, nível elétrico ou compatibilidade com relé, PhotoMOS, optoacoplador ou GPIO. A alternativa B (porta RXD/TXD) é somente uma pista de investigação; C (substituição parcial) é contingência se A/B forem inviáveis.

O marco documental P0 está concluído: 37 fotos originais, hashes distintos e inspeção visual individual foram registrados. P1–P5 continuam pendentes.

| Portão | Situação | Efeito prático |
|---|---|---|
| P0 — acervo e rastreabilidade | Concluído | Evidências de foto são auditáveis. |
| P1 — mapa dos controles | Pendente | Bloqueia a escolha de interface e a ligação à placa. |
| P2 — características elétricas | Pendente | Bloqueia seleção de componente, isolação e limites elétricos. |
| P3 — ciclo e parada da máquina | Pendente | Bloqueia a definição de estado seguro e a integração real. |
| P4 — interface, chicote, arbitragem e proteção | Pendente | Bloqueia bancada ligada à máquina e instalação. |
| P5 — vídeo | Pendente | Bloqueia escolha do caminho de streaming e UX operacional real. |

## O que já está suficientemente definido

- A unidade é uma máquina de garra para pelúcias com arte `Fun Time`; há joystick iluminado, botão candidato a captura, display, câmera interna, sensor candidato de prêmio e uma controladora original com potência e sete relés.
- A fonte é identificada pela etiqueta como Wangma `WM-ATX400-24-48`, com trilhos nominais de 5/12/24/48 V e potência total declarada de 320 W. Isso não é medição, reserva disponível nem pinagem de integração.
- A C02 deve ser preservada inicialmente: ela já concentra lógica e acionamento da máquina. Essa é uma decisão de redução de escopo, não uma prova de compatibilidade elétrica.
- A arquitetura lógica candidata está clara: `navegador → backend/reserva exclusiva → agente local → MCU/supervisor → interface elétrica validada → entradas da C02`; vídeo segue caminho separado.
- O contrato de segurança de software já tem direção: autorização curta, `boot_id`, sessão, geração/fencing token, sequência monotônica, expiração local, rejeição de mensagens antigas/duplicadas, bloqueio de direções opostas e partida inibida após boot/reconexão.
- A PoC deve manter crédito pelo meio original e tratar prêmio como desconhecido até haver evidência de sensores/eventos. Pagamento real não integra a primeira PoC.

## Implementação que pode começar agora

Estas entregas não devem conter pinos reais, esquemas, acionamento elétrico ou alegação de controle de máquina.

| Frente | Entregável inicial | Limite obrigatório |
|---|---|---|
| Domínio/backend | Modelo de máquinas, jogadores, reserva exclusiva, fila, sessão, partida, auditoria e estados `OFFLINE…RECONCILING/FAULT/MAINTENANCE` | Não inferir estado físico por timer ou ACK. |
| Protocolo de controle | Especificação versionada e validador de mensagens: `machine_id`, `boot_id`, `session_id`, geração, sequência, prazo e intenção | O protocolo deve produzir apenas comandos simulados enquanto P1–P4 não fecharem. |
| Supervisor lógico | Máquina de estados que expira comandos, rejeita opostos, falha fechada e invalida sessão após reinício | Implementar contra uma porta abstrata/simulador, não contra GPIO real. |
| Simulador e testes | Simulador da interface e testes de boot, expiração, duplicata, mensagens fora de ordem, duas sessões, perda de conexão e captura com confirmação perdida | Resultado de captura/prêmio deve poder permanecer `desconhecido`. |
| Web de teste | Tela de fila/reserva, vídeo simulado, joystick virtual, botão de captura, indicadores de conexão e motivo de bloqueio | Não publicar como operação real nem permitir continuação com vídeo congelado. |
| Agente local (software) | Canal de saída autenticado, logs correlacionados, persistência de `boot_id`/geração e adaptador de saída simulado | A escolha de MCU, SBC ou linguagem de firmware pode ser adiada; não há I/O físico definido. |
| Observabilidade | Esquema de logs e métricas para idade de comando, recusa, watchdog lógico, estado da sessão e reconciliação | Metas atuais — p95 comando 150 ms, vídeo 300 ms e liberação 300 ms — são metas de engenharia, não medições ou limites de segurança. |
| Vídeo (preparação) | Interface abstrata de câmera/publicador e ambiente com stream de teste WebRTC | Não assumir RTSP, ONVIF, codec ou acesso da câmera existente. |
| Operação de campo | Fichas de P1–P5, folha de ensaio e registro de configuração por unidade | A documentação já contém modelos; o próximo agente pode digitalizá-los sem tocar na máquina. |

## Investigação que falta para entender a máquina e liberar a PoC física

### Prioridade 1 — P1: joystick e botão até a C02

É a única próxima evidência prioritária. Um profissional, com a máquina desenergizada e energia residual/partes móveis tratadas, deve produzir uma ficha contendo:

- vista contínua entre haste do joystick, base amarela, atuadores/terminais e chicote;
- macros orientadas dos terminais do joystick e do botão, separando contatos da iluminação;
- conectores identificados por posição/orientação e rastreio físico até a C02 ou placa intermediária;
- tabela de continuidade em neutro, nas quatro direções e no botão, com os contatos isolados adequadamente da eletrônica.

Esse portão decide se as entradas são contatos independentes, matriz/varredura, contatos multipolares, potência, analógico ou painel digital. Uma foto de fios, cor de condutor ou conector isolado não resolve essa questão.

### Prioridade 2 — P2 e P3: caracterização energizada e comportamento original

Após P1 e somente por profissional qualificado, registrar por comando: tensão e referência, polaridade, DC/AC/varredura, corrente/impedância, transientes, estado aberto/fechado, duração mínima/máxima e repetição. Também observar o ciclo original de crédito, início, movimento, soltura, captura, descida, fechamento, subida, retorno e parada.

Este trabalho é o que permite definir a interface e, principalmente, a resposta segura a falhas. Soltar a entrada remota não demonstra que um ciclo automático ou uma garra sustentando carga tenha parado.

### Prioridade 3 — P4: especificar e ensaiar a interface fora da máquina

Com P1–P3 aprovados, definir componente/variante, isolação, alimentação, chicote reversível, arbitragem local/remoto, estado no boot/sem alimentação e contenção de saída presa. Ensaiar primeiro com simulador/carga representativa em bancada. Só depois considerar integração reversível supervisionada na unidade.

### Prioridade 4 — P5: câmera e vídeo

Identificar modelo da câmera sem expor senha ou QR de provisionamento; obter manual e medir acesso local, codec, campo útil, latência e congelamento. Só então decidir entre reutilizá-la, usar gateway de mídia ou trocá-la. Vídeo não deve estar no laço de segurança do comando, mas vídeo ausente/congelado deve bloquear novas ações remotas na PoC.

### Pesquisa complementar, sem bloquear o software simulado

- Plaqueta do gabinete, revisão/duas faces da PCB, macros do CI `IAP/15…`, componente sob `PG01`, semicondutores de potência e relés.
- Modelos e trajetos elétricos de moedeiro, validadores de cédula, chicotes `CRÉDITO`/`PRÊMIO`, barra óptica e contadores de serviço.
- Etiquetas de motores, fins de curso, atuador da garra, aterramento e circuito de parada local.
- Documentação vinculada à revisão da PCB para avaliar a porta `12V/GND/RXD/TXD/5V`. Não conectar serial, GPIO ou analisador antes da caracterização; a porta não comprova UART, CNGPI ou comando de movimento.
- Medições de rede no local para dimensionar vídeo/controle. A localização e o link da máquina não foram validados pela documentação.

## Regras de decisão para o próximo agente

1. Tratar `CONFIRMADO`, `PROVÁVEL` e `NÃO IDENTIFICADO` literalmente; não converter hipótese visual em requisito elétrico.
2. Não comprar relé, SSR, PhotoMOS, optoacoplador, USB-serial, ESP32, Raspberry Pi, câmera, conector ou driver de motor para integrar a máquina antes dos portões correspondentes. Um componente candidato não é uma especificação.
3. Não conectar GPIO, USB–UART, osciloscópio/analisador ou alimentação à placa desconhecida; não usar RXD/TXD para experimentação.
4. Não automatizar crédito/pagamento nem chamar captura, ACK ou imagem estática de prêmio confirmado. Usar os estados `observado`, `desconhecido` e `reconciliação` no modelo de software.
5. Não permitir operação pública/remota real até P1–P4, bancada aprovada, integração supervisionada e os ensaios do plano 08. A decisão comercial exige ainda validação operacional, rede e pagamentos.

## Sequência recomendada de trabalho

1. Implementar contrato, simulador, backend mínimo, interface web de teste e testes de falha sem hardware real.
2. Contratar/executar P1, a ficha desenergizada de joystick/botão até a C02.
3. Atualizar o modelo elétrico e a matriz de riscos com P1; escolher a estratégia A, B ou C somente se a evidência mudar.
4. Executar P2/P3 supervisionados; registrar dados brutos e limites físicos.
5. Projetar e validar P4 em bancada isolada.
6. Fechar P5 em paralelo com a investigação de vídeo.
7. Integrar uma única máquina de modo reversível, controlado, sem pagamento real; depois executar as fases G–I do plano de validação.

## Referências de entrada para o handoff

- `README.md` — índice e conclusão provisória.
- `docs/10-resumo-executivo.md` — visão de decisão e inventário de lacunas.
- `docs/11-investigacao-focalizada.md` — evidência consolidada e hipóteses excluídas.
- `docs/12-plano-prova-de-conceito.md` — portões P0–P5, arquitetura e critérios de sucesso.
- `docs/08-plano-validacao.md` — fases B–I e folhas de ensaio.
- `docs/04-investigacao-controles.md` — bloqueio técnico principal e critérios de seleção da interface.
- `docs/07-arquitetura-controle-remoto.md` — contrato conceitual de software e segurança.

## Conclusão

Há informação suficiente para construir a **plataforma de controle simulada** e para planejar uma PoC segura. Ainda não há informação suficiente para construir ou instalar a **interface elétrica da máquina**. A passagem objetiva entre esses estágios é P1: o mapa profissional, desenergizado e rastreável de joystick/botão até a controladora. Depois dele, P2/P3 definem se a solução A se torna uma adaptação simples e reversível ou se será necessário investigar B/C.
