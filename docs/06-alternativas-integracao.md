# 06 — Alternativas de integração e seleção do controlador

Data: 21/10/2026. A decisão possível hoje é **priorizar a investigação da solução A**. Não há evidência suficiente para aprovar um circuito, modelo de interface ou compra. Preservar a placa original é promissor porque a lógica/potência já está reunida em C02 e há indícios de controles eletromecânicos C04, não porque já demonstramos compatibilidade elétrica.

## Comparação das três estratégias

| Critério | A — Reproduzir entradas e manter C02 | B — Usar comunicação nativa | C — Adaptar/substituir controle |
|---|---|---|---|
| Princípio | Acrescentar interface compatível com as entradas de direção/captura; deixar ciclo de motores/garra com a PCB | Implementar comandos suportados por porta/protocolo comprovados do firmware original | Acrescentar/substituir parte da lógica/potência e assumir as funções removidas |
| Evidência a favor no exemplar | F05–F09: controles acessíveis e base provável de lâminas; F18–F26: PCB original com relés e potência | F19/F20: header com RXD/TXD e outros sinais | Mecanismo e fonte existem e podem, em princípio, ser caracterizados separadamente |
| Evidência contrária ou lacuna | Contatos, referências, corrente, endpoint e comportamento não validados; controle pode usar matriz ou até potência | Nenhum manual, nível, framing, comando ou finalidade da porta identificado; componentes não populados em áreas da PCB | Motores, sensores, driver/força da garra, homing e proteções sem especificação. Escopo de validação muito maior |
| Viabilidade atual | **PROVÁVEL**, condicionada ao levantamento dos controles | **NÃO IDENTIFICADO**; nem sua existência como porta de comando foi demonstrada | **NÃO IDENTIFICADO** para projeto concreto; possibilidade de engenharia, sem dados para executar |
| Compatibilidade com nossa unidade | Melhor pista disponível, ainda sem demonstração experimental | Não se pode transportar protocolo de placa visualmente semelhante | Não se pode comprar controladora universal sem mapear atuadores e chicote |
| Componentes adicionais | Controlador, interface apropriada, chicote reversível, alimentação/proteção, permissão local e caminho de vídeo | Gateway/controlador, transceptor compatível e possível isolamento, alimentação e controle local; vídeo separado | Controlador, drivers de potência, interface de sensores, lógica de elevação/garra, proteções, chicotes e eventualmente nova fonte/sensores |
| Instalação | Menor escopo esperado; pode permitir adaptador removível após mapear plugs | Pode ser pequena se porta for documentada; investigar sem documentação acrescenta risco e tempo | Maior intervenção, mais pontos elétricos e mecânicos a revalidar |
| Desenvolvimento | Firmware limitado de comandos/segurança e software remoto; crédito e estado exigem trabalho separado | Driver de protocolo, estados e recuperação; engenharia reversa pode superar custo de A | Controle completo de movimentos/ciclo e falhas, além da plataforma remota |
| Risco elétrico | Entrada desconhecida ou módulo inadequado pode danificar PCB; isolamento precisa de projeto | Conversor errado, nível incompatível ou comando de serviço pode alterar placa/configuração | Acionamento direto de cargas, corrente de partida e energia indutiva; maior exposição a falhas de potência |
| Risco mecânico | Comando retido, conflito local/remoto ou ciclo automático não interrompível pelo joystick | Comando mal interpretado pode acionar manutenção, movimento ou configuração | Colisão, perda de referência, descida/queda, força indevida e perda de proteções originais |
| Custo relativo | Menor **se** forem entradas simples e vídeo reaproveitável | Baixo em hardware se documentada; custo de investigação imprevisível na situação atual | Maior escopo e custo de engenharia/validação; sem orçamento confiável |
| Manutenção | Interface padronizada, mas conservar registro da revisão elétrica por máquina | Dependência de versão de firmware e protocolo; precisa detectar incompatibilidade | Responsabilidade integral por hardware/firmware e peças próprias |
| Reversibilidade | Alta com adaptador removível e sem alterar configuração; não garantida se cortar chicote | Alta se uso só operacional e sem gravação; comandos de serviço podem mudar estado persistente | Parcial e trabalhosa; conservar controle removido e mapa de reversão |
| Escala para frota | Boa se houver variantes documentadas e teste de aceitação por unidade | Boa se fabricante sustentar API estável/versionada; atualmente desconhecido | Possível padronizar frota, mas cada mecânica exige caracterização e manutenção |
| Dependência de fornecedores | Mantém dependência da PCB original, reduz dependência de gateway/interface proprietária | Maior dependência do protocolo e da continuidade do firmware | Reduz dependência da lógica original, amplia responsabilidade e dependência de componentes de potência |

Não há razão evidencial para substituir agora a PCB que já reúne o sequenciamento original. Também não há razão para descartar B: as inscrições justificam buscar documentação, mas não ligar um adaptador ou iniciar varredura de comandos.

## Critérios que mudam a decisão

**Continuar em A** se o levantamento confirmar entradas reproduzíveis, alimentação/referências conhecidas, preservação dos controles/sensores e resposta local segura a falhas. A ausência de telemetria não impede uma PoC supervisionada, mas impede fingir que o backend conhece estado/prêmio com certeza.

**Priorizar B** apenas se surgir documentação vinculada à revisão da PCB/firmware e ela comprovar comandos operacionais, estados, camada elétrica e comportamento de falha. Uma UART de gravação ou diagnóstico não satisfaz esses critérios. Captura passiva futura, por profissional após identificação elétrica, pode investigar tráfego; não deve incluir transmissão exploratória desconhecida.

**Avaliar C** se A for tecnicamente incompatível ou insegura e B não oferecer caminho documentável. A substituição parcial deve identificar exatamente o bloco removido. Por exemplo, substituir apenas recepção de comandos mantendo potência é diferente de assumir motores/garra. Cada fronteira precisa de esquema e critérios de validação; “usar motores existentes” não reduz automaticamente esse trabalho.

## Controlador de comandos e processador de vídeo são escolhas diferentes

O trabalho de comandos é pequeno em volume: receber estados recentes, verificar autorização, limitar duração, arbitrar direções, acionar uma interface e observar entradas validadas. O trabalho de vídeo envolve captura, codec, filas, transporte e possivelmente transcodificação. Os requisitos de CPU/energia do segundo não determinam a placa do primeiro.

| Opção | Adequação ao controle | Adequação ao vídeo | Custo/operabilidade e limite nesta máquina |
|---|---|---|---|
| **ESP32 em placa adequada** | Candidato para comandos de baixa banda, lógica local e conexão de rede; precisa de interface elétrica e contenção de boot/falhas | Não presumir capacidade de converter a câmera atual e publicar vídeo na qualidade exigida | Escopo/consumo tendem a ser menores que computador Linux. Modelo, GPIO utilizável, rede, alimentação e interface ainda dependem do levantamento |
| **Raspberry Pi 4 ou SBC Linux equivalente** | Pode manter agente de rede/logs, mas processo Linux/GPIO não substitui supervisão independente | Candidato quando captura/ponte/codificação local forem necessárias; codec e desempenho devem ser medidos | Mais administração de sistema, armazenamento, alimentação e atualização; não necessário só para reproduzir contatos |
| **Notebook/mini-PC já existente + MCU** | Boa composição para bancada/PoC: MCU limita saídas enquanto computador publica vídeo e executa serviços | Pode reduzir aquisição inicial; USB/rede disponíveis precisam atender câmera | Economia por reaproveitamento, consumo e recuperação de falhas a medir; não é decisão de hardware de frota |
| **Pico/RP2040 ou outro MCU documentado + gateway** | Alternativa para supervisão e interface local com conexão ao gateway | Não substitui gateway de mídia | Pode ser adequado se rede ficar no computador. Pico comum não tem rádio; Pico W é variante distinta. Seleção não exige usar marca específica |
| **Controlador industrial/PLC com rede e I/O adequados** | Avaliável quando robustez, ambiente e equipe de manutenção justificarem | Vídeo permanece separado | Custo e instalação tendem a aumentar. I/O de 24 V não é compatível automaticamente com nossa entrada desconhecida; certificação do equipamento não certifica a adaptação completa |

As páginas oficiais do [ESP32-DevKitC](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32/esp32-devkitc/user_guide.html), [Raspberry Pi 4](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) e [Pico](https://www.raspberrypi.com/products/raspberry-pi-pico/) documentam suas interfaces e variantes. São candidatos adicionais, **nenhum deles foi identificado nas fotografias**. A documentação [Espressif de watchdogs](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/wdts.html) sustenta avaliar supervisão de execução, sem garantir abertura de uma saída física defeituosa.

Não especificamos pinagem MCU→máquina. Alimentação de uma devboard não determina tolerância de seus GPIO. Uma fonte com trilho nominal de 5 V não demonstra que alimentar a placa por esse trilho seja apropriado ou que haja reserva de corrente, isolamento e comportamento de transiente adequados.

## Arquitetura candidata com menor intervenção

Após confirmar A: **navegador → backend com sessão exclusiva → agente local/MCU → interface validada → controles da C02**. Em paralelo, **câmera → publicador de vídeo, se necessário → navegador**. ESP32 é o primeiro candidato a avaliar para comandos; gateway Linux entra somente se câmera/rede/mídia exigirem. Um computador existente pode cumprir essa função na PoC.

Manter C02 preserva seu sequenciamento, mas não comprova segurança ou adequação para operar sem supervisão. Precisamos medir o que acontece ao soltar controles e durante captura, subida e retorno. A análise deve definir também uma função local de parada/retirada de permissão independente da internet.

Para várias máquinas, uma configuração por unidade deve registrar fabricante/modelo quando encontrados, revisão de PCB/firmware, ficha elétrica, interface instalada, câmera, proteção e ensaios aprovados. A mesma arte Fun Time não autoriza reaplicar uma pinagem.

## Referência comercial consultada

A [página pública Online Machine](https://www.onlinemachine.com.br/) foi aberta em 21/10/2026. O conteúdo acessível mostra chamada para instalar aplicativo e uma referência de câmera. Isso não informa placa, gateway, firmware, protocolo de comandos ou arquitetura de vídeo interna. Nenhuma dessas tecnologias foi atribuída à concorrente, e nenhum endpoint privado/controle foi acessado. A referência aqui é o objetivo de experiência descrito pelo usuário, não um esquema para copiar.

**Resultado:** solução A é a prioridade de investigação, com B como oportunidade dependente de documentação e C como alternativa de maior intervenção. A tecnologia da interface elétrica continua **NÃO IDENTIFICADO** até o levantamento de C04/C05; o orçamento e a escolha definitiva de controlador permanecem condicionais.
