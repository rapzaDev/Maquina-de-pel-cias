# 09 — Componentes e custos preliminares

Data de referência: 21/10/2026. Esta é uma lista funcional para dimensionar o protótipo, **não uma lista de compra aprovada**. Não há interface elétrica dos controles validada. A solução mais promissora é a A, preservando C02 e acrescentando reprodução dos controles, condicionada às verificações de [04](04-investigacao-controles.md) e [08](08-plano-validacao.md). Não foram comprados componentes.

## Obrigatórios para a solução A, após aprovação elétrica

“Obrigatório” significa função necessária; peças já existentes ou emprestadas podem cumpri-la. Quantidades são por uma máquina. Referências Fxx e Cxx estão no [inventário](01-inventario-fotografico.md).

| Item / quantidade estimada | Função e especificação necessária | Compatibilidade a confirmar / motivo | Preço verificado / fonte |
|---|---|---|---|
| Controlador local, 1 | Receber comandos autenticados, aplicar estado seguro, intertravamentos, sequência, validade e watchdog; GPIO suficiente para canais confirmados | ESP32 é candidato econômico para controle, não escolha definitiva de placa. Deve iniciar com saídas inativas e não depender da internet para soltar comandos | Sem cotação da placa escolhida. [Documentação oficial Espressif DevKitC](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32/esp32-devkitc/user_guide.html) para avaliar placas, não para conectar à máquina |
| Interface elétrica dos comandos, 1 conjunto, estimativa inicial de 5 funções | Reproduzir esquerda/direita/frente/trás/captura com separação elétrica apropriada e saída segura; quantidade de contatos pode ser maior que cinco | Relés de sinal, PhotoMOS/chaves isoladas, optoacopladores ou interface digital somente após determinar circuito. Contatos de lâmina em C04 são PROVÁVEL; tipo e corrente desconhecidos. Cinco funções não significam cinco fios | Não cotado: tecnologia e limites elétricos ainda indefinidos. Base: F05–F09, [04](04-investigacao-controles.md) |
| Alimentação apropriada do controlador/interface, 1 conjunto | Fonte protegida e dimensionada; isolamento, aterramento e retorno examinados no projeto | Preferir fonte independente de bancada no início; não supor que C03 possua reserva ou que seus 5 V sejam adequados a um gateway | Não cotado: tensão, consumo e isolamento dependem da interface. Etiqueta C03 em F28 |
| Chicote adaptador reversível, 1 conjunto | Conectores compatíveis, condutores dimensionados, retenção e identificação; permitir retorno à instalação original | Pitch, polarização, série, corrente e pinagem ainda desconhecidos. Contar vias não identifica fabricante. Evitar cortes, emendas improvisadas e conectores escolhidos pela cor | Não cotado: depende do mapeamento de C04/C05/C02. F06–F09, F18–F20 |
| Invólucro, fixação, proteção e alívio de tração, 1 conjunto | Segregar eletrônica adicionada de rede, partes móveis e acesso de manutenção; proteção contra contato e curto | Dimensões, dissipação, local e proteção de circuitos precisam de avaliação presencial | Não cotado: projeto mecânico/elétrico pendente |
| Caminho de vídeo de baixa latência, 1 | Câmera mais caminho de captura/encaminhamento com métricas e teste real de latência | Reusar C13 apenas se modelo, acesso local, codec e desempenho forem demonstrados. A presença física não confirma adequação a WebRTC | Não cotado: primeiro identificar câmera C13 (F04, F35–F37) |
| Rede local e uplink, 1 conexão | Comunicação confiável para comandos e vídeo; saída autenticada e suporte à banda medida | Ethernet desejável onde disponível; Wi-Fi e internet de Tobias Barreto precisam de medição no local. Link existente pode bastar | Sem cotação; provedor, plano e instalação não foram verificados |
| Bloqueio/parada local e arbitragem local/remoto, 1 conjunto | Retirar a autorização de controle remoto e conduzir sistema ao estado seguro; prioridade local | Circuito e ação de parada devem ser definidos por profissional: desligar alimentação de modo indiscriminado não garante parada mecânica imediata. Avaliar chave de habilitação e proteção independente | Não cotado: função depende da análise de perigos e do comportamento de C02 |

## Possivelmente necessários

| Item / quantidade | Função e especificações | Quando incluir / compatibilidade | Preço / fonte |
|---|---|---|---|
| Gateway Linux existente, mini-PC ou SBC, 0–1 | Serviço local de vídeo, WebRTC, logs e atualização; Ethernet/USB conforme câmera | Somente se a câmera não entregar caminho adequado ou se o protótipo exigir processamento local. Notebook existente pode cumprir a função inicial | Equipamento escolhido não cotado. [Raspberry Pi 4 — oficial](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) apresenta Ethernet e USB; alternativa de gateway, não requisito |
| Interface de crédito/início, 0–1 | Criar exatamente uma oportunidade de jogo para uma autorização já confirmada e reconciliar partidas | Identificar primeiro semântica de C07/C08/C09, chicote “CRÉDITO” e controles de serviço. Não supor pulso baixo, 12 V ou duração específica | Não cotado; F11–F17, F24–F26 |
| Realimentação isolada de estado, quantidade pendente | Observar pronto/partida/fim/prêmio sem interferir na eletrônica original | Apenas após documentar saídas existentes. Comando enviado não confirma deslocamento físico nem prêmio | Não cotado; C10 e C19 pendentes |
| Câmera substituta, 0–1 inicialmente | Codec/captura compatíveis, latência avaliada e campo visual útil da garra e saída | Se C13 não atender; resolução elevada não substitui baixa latência. Interface USB UVC ou rede documentada depende do gateway | Não cotado: modelo de C13 e testes ainda ausentes |
| Watchdog/supervisor físico independente, 0–1 conjunto | Retirar habilitação quando controlador travar, conforme tempos seguros medidos | A necessidade e implementação seguem avaliação de perigos; não assumir que watchdog de software cobre falha de saída em curto | Não cotado: projeto pendente |
| Proteção elétrica e filtragem adicionais, 0–1 conjunto | Fusíveis, proteção contra transientes, segregação e redução de ruído dimensionadas | Definir por tensão, corrente, carga e caminho de alimentação medidos; não instalar supressores aleatórios nos controles | Não cotado: parâmetros desconhecidos |

## Opcionais

| Item / quantidade | Função / condição | Preço / fonte |
|---|---|---|
| Segunda câmera, 0–1 | Ângulo auxiliar, se melhorar julgamento de profundidade; duplica parte de banda e processamento | Não cotado; escolher após medir vídeo inicial |
| UPS para rede/gateway, 0–1 | Manter telemetria e encerramento ordenado em falta de energia; não é autorização de movimento | Não cotado; potência e autonomia pendentes |
| Armazenamento local, 0–1 | Logs limitados e diagnóstico sem reter vídeo desnecessariamente | Não cotado; depende do gateway |
| Monitoramento de temperatura/link/energia, 0–1 conjunto | Diagnóstico operacional da frota após estabilizar o protótipo | Não cotado; evitar sensores antes de haver requisito |

## Dependentes de validação; não comprar agora

| Item | Bloqueio técnico específico |
|---|---|
| Módulo de relés genérico 4/8 canais | Não há tensão/corrente do contato, isolamento, fuga ou comportamento no boot caracterizados. Isolação declarada de um componente não garante segregação da placa completa |
| Optoacopladores, PhotoMOS e chaves analógicas | Polaridade, corrente de detecção, resistência, fuga, capacitância e possível varredura/matriz precisam de verificação |
| USB–UART, RS-232, RS-485 ou conversores de nível | RXD/TXD em C19 não documentam camada elétrica, protocolo ou finalidade; podem danificar a placa ou iniciar gravação se conectados inadequadamente |
| Drivers de motor, pontes H ou novos atuadores | Modelos, tensão/corrente de trabalho e partida, limites e proteção não identificados; estratégia C é último recurso |
| Placa principal “PG01” de reposição ou controladora universal | Adesivo PG01 não é identificação suficiente; chicotes e firmware podem diferir |
| Fonte ATX de computador ou substituta por nome semelhante | C03 possui quatro saídas específicas e limite total de 320 W; nome ATX não define pinagem compatível |
| Raspberry Pi, kit com fonte/cartão/câmera | Sua necessidade depende do caminho de vídeo e do hardware já disponível. Não é necessário para meros contatos de controle |
| Câmera IP por aparência semelhante à instalada | Modelo, codec, modo local e latência precisam ser comprovados |
| Conectores por foto ou cor do plástico | Série, passo, polarização e capacidade de corrente ainda não identificados |

## Instrumentos da validação: recursos de trabalho, não peças da máquina

Primeiro aproveitar instrumentos adequados já disponíveis com o profissional responsável. A inspeção desenergizada requer registro fotográfico, identificação de condutores e instrumentos apropriados para comprovar ausência de tensão e continuidade após isolamento do circuito. Medições energizadas posteriores podem exigir multímetro, osciloscópio e sondas apropriados à categoria e referências do circuito, fonte de bancada limitada e analisador lógico somente se os níveis forem compatíveis. O aterramento de um osciloscópio pode provocar curto; seu uso precisa de planejamento técnico. Não sugerimos aquisição de instrumentos sem saber o que o profissional já possui.

## Custos: o que é possível afirmar

Não há orçamento total responsável enquanto não se definir o tipo e a quantidade de interfaces e o reaproveitamento da câmera. Nesta consulta não se verificaram faixas de preço brasileiras para uma lista fechada. Para evitar falsa precisão, as linhas não cotadas permanecem sem valores e sem indicação de estoque.

Como única referência numérica de catálogo primário consultada, a página oficial do [Raspberry Pi 4](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) exibia **“From $35”** em 21/10/2026. É preço inicial anunciado em dólares, não orçamento da versão necessária, nem disponibilidade no Brasil, nem preço entregue com impostos, alimentação, armazenamento e invólucro. Não entra em um total de projeto e não constitui recomendação de compra.

A pesquisa do código da fonte também retornou anúncios divergentes de terceiros (inclusive entrada restrita a 220 V e potências que diferem de F28). Eles não foram usados para especificar reposição ou preço deste exemplar. A referência técnica continua sendo a etiqueta e uma futura confirmação oficial.

O custo relativo mais favorável tende a ser controlador simples + interface validada + vídeo reaproveitado, se os controles mecânicos forem confirmados. Um gateway Linux e nova câmera aumentam custo e manutenção; substituição de controle acrescenta drivers, sensores, cabeamento e revalidação de toda a máquina. Isso é comparação de escopo de engenharia, não cotação.

Após aprovação do levantamento dos controles, a lista deve ganhar: fabricante e código de cada componente, folha técnica, limites elétricos medidos, quantidade final, fornecedor, preço datado, frete/impostos e custo de montagem/teste. Até lá, a prioridade é **identificar o circuito de C04/C05**, sem compra antecipada.
