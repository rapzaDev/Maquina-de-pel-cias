# 04 — Investigação do joystick, captura e início

Data: 21/10/2026. Resultado: **PROVÁVEL** possibilidade de reproduzir comandos mantendo a controladora. **NÃO IDENTIFICADO** o circuito elétrico necessário para fazê-lo. Não há esquema de ligação aprovado nem validação experimental.

## Evidência específica e hipóteses concorrentes

F05 mostra joystick iluminado, botão circular e LCD. F06–F09 mostram próximo ao verso do LCD um mecanismo com suportes amarelos, lâminas metálicas e peça central branca. A posição e a simetria são compatíveis com a base do joystick C04. O [recorte F09](../evidencias/inspecao/F09-mecanismo-amarelo.png) favorece a hipótese de contatos mecânicos de lâmina. Falta uma vista que una inequivocamente eixo do topo, atuador e terminais.

| Natureza do comando | Compatibilidade com nossas fotos | Classificação e teste que diferencia |
|---|---|---|
| Contatos mecânicos de lâmina | Melhor compatibilidade com o mecanismo amarelo; não há potenciômetro claramente reconhecível nesse recorte | PROVÁVEL; inspeção desenergizada deve relacionar deslocamento do eixo, contatos e circuito, com o conjunto corretamente isolado para levantamento |
| Microinterruptores encapsulados | Joysticks convencionais podem usá-los, mas não há cápsulas inequívocas na base amarela | NÃO IDENTIFICADO; macro dos contatos/peças e referência do fabricante |
| Contatos independentes com retorno comum | Uma implementação simples possível | NÃO IDENTIFICADO; mapear continuidade das posições e rastrear destino. Não assumir quatro entradas mais GND |
| Matriz/varredura ou contatos multipolares | Compatível com contatos físicos; o número de lâminas e fios não exclui isso | NÃO IDENTIFICADO; levantamento de contatos e depois formas de onda diferencia retorno fixo, linhas de varredura e polaridade variável |
| Chaveamento de alimentação/potência | Não excluído só pela presença de lâminas | NÃO IDENTIFICADO; determinar se conduz entrada lógica ou corrente de carga antes de selecionar contato/isolador |
| Sinal analógico por potenciômetro/Hall | Menos sustentado pela base visível, mas eletrônica pode estar oculta | NÃO IDENTIFICADO; procurar sensor/circuito e caracterizar saídas. Contato em paralelo não emula valor analógico |
| Comunicação digital/proprietária do conjunto | Possível placa intermediária, não demonstrada | NÃO IDENTIFICADO; rastrear conexões e identificar CI/protocolo. O conector do LCD não demonstra protocolo do joystick |

O catálogo primário [Baolian de joysticks](https://www.bao-lian.com/en/products/joysticks/) mostra soluções com e sem PCB e com Hall; seu [catálogo de interruptores](https://www.bao-lian.com/en/products/microswitches/) inclui contatos de lâmina. São referências para distinguir tecnologias, **não identificação do fabricante ou modelo do nosso C04**. O topo transparente iluminado pode ter circuito de luz independente dos contatos; sua iluminação não prova que o sinal de comando seja alimentado na mesma tensão.

## Funções a reproduzir e contrato físico que falta

| Função pretendida | Evidência atual | Condição necessária antes de reproduzir |
|---|---|---|
| Esquerda | Joystick e carro existem; contato correspondente desconhecido | Identificar posição física, contato(s), corrente/tensão, estado neutro e destino; definir orientação pela visão do jogador |
| Direita | Igual à esquerda | Mapear separadamente; bloquear esquerda+direita, sem concluir que a placa original oferece esse intertravamento |
| Frente | Igual às anteriores | Identificar sentido real, distância de parada e tolerância de movimento; a câmera pode inverter a percepção |
| Trás | Igual às anteriores | Mapear e bloquear frente+trás; diagonais só depois de demonstrar funcionamento permitido |
| Captura | C05 é candidato, sem verso identificável | Determinar contato/lógica, tempo mínimo, comportamento com acionamento longo, liberação e eventual função dupla de início |
| Início/crédito | Tela solicita moeda; C07 e CRÉDITO existem | Determinar se crédito já inicia, só habilita, ou é consumido no primeiro comando. Não confundir iniciar sessão web, registrar pagamento e iniciar máquina |

Cinco funções de jogador não equivalem a cinco fios, cinco contatos ou cinco GPIO. Crédito pode demandar outra interface; a primeira prova pode usar crédito local validado e supervisão, sem automatizar cobrança. Nenhum botão de C14 está documentado como crédito, teste ou parada de emergência.

## Comparação das interfaces candidatas

| Tecnologia | Quando poderia servir | Vantagens | Limitações verificáveis/condição de escolha |
|---|---|---|---|
| Relé eletromecânico **de sinal**, normalmente aberto, não retentivo | Contato mecânico comprovado, inclusive flutuante ou matriz dentro das especificações | Contato pode separar galvanicamente os lados e não exigir referência comum de sinal; baixa resistência | Dimensionar carga mínima/máxima, material, vida, bounce, tempo de operação, isolamento e driver. Pode colar fechado. Módulo de potência genérico pode ser inadequado a correntes baixas ou disparar no boot |
| Relé reed de sinal | Contato de baixa corrente com necessidade de isolamento e alta resistência desligado | Alternativa compacta para fechamento isolado | Limites de corrente/inrush, vida e sensibilidade mecânica/magnética devem ser adequados; também pode falhar fechado |
| Chave isolada com MOSFETs de saída, como família PhotoMOS | Contatos de baixa energia cuja faixa e varredura sejam compatíveis | Sem contato mecânico, silenciosa; existem variantes bidirecionais | Escolher variante AC/DC adequada. Resistência ligada, fuga desligada, capacitância e tempos podem falsear matriz ou detecção. “SSR” não garante adequação; SSR triac de rede não serve automaticamente para entrada DC |
| Optoacoplador com fototransistor | Entrada lógica DC comprovada, unidirecional e com polaridade/corrente conhecidas | Isolamento de sinal e custo potencialmente baixo | Não é contato seco universal; queda de tensão, fuga, CTR, saturação, direção e tempo contam. Pode não reproduzir varredura de polaridade alternada |
| Chave analógica/MOSFET sem isolamento próprio | Faixa de tensão/referência documentada e separação obtida por projeto adequado | Velocidade e tamanho | Não resolve isolamento por si; limites de modo comum, alimentação e falhas precisam ser analisados. Não conectar diretamente GPIO a entrada desconhecida |
| Interface digital nativa documentada | Firmware e protocolo compatíveis comprovados | Pode oferecer comando e estado sem emular contatos | J-SER tem somente inscrições conhecidas; sem documentação, não é atalho seguro. Programação, atualização e controle operacional são funções distintas |
| Emulação de sinal analógico | Somente se aparecer sinal analógico comprovado | Pode preservar placa em caso não discreto | Exige faixa, resolução, referência e neutro; DAC não é compra justificada hoje |

A documentação oficial [Omron G6K](https://omronfs.omron.com/en_US/ecb/products/pdf/en-g6k.pdf) exemplifica por que selecionar variante e carga de um relé de sinal importa. Não determina qual relé comprar aqui. A [FAQ PhotoMOS Panasonic](https://na.industrial.panasonic.com/knowledge-base/faqs/photomosr-faqs) explica efeitos de fuga e capacitância; a [FAQ Vishay de optoacopladores](https://www.vishay.com/docs/84360/optocouplersfaqs.pdf) documenta limites de entrada/saída e CTR. Nenhum desses dispositivos foi identificado na máquina como interface pronta de expansão.

**Decisão condicional:** se C04/C05 forem contatos passivos de baixa energia, comparar primeiro relé de sinal não retentivo e chave isolada bidirecional com os limites efetivamente medidos. Optotransistor só entra como opção de saída quando a polaridade e os níveis permitirem. A escolha final ainda não pode ser feita; não há preferência automática por relés.

## Levantamento necessário antes de qualquer adaptação

1. **Identificação e documentação:** macro do conjunto amarelo, terminais, verso do botão e trajeto dos chicotes até C02/placa intermediária; procurar marca/modelo e manual. Registrar estado original e conexão por posição, sem inventar pinagem por cor.
2. **Inspeção desenergizada profissional:** máquina isolada das fontes, energias residuais tratadas e ausência de tensão comprovada pelo profissional. Mapear contatos em neutro e em cada direção/captura com o circuito adequadamente isolado da eletrônica para não interpretar resistências paralelas como fechamento. Não usar teste de continuidade em circuito energizado. Só então determinar quantos polos, comuns e contatos normalmente abertos/fechados existem.
3. **Rastreio funcional:** relacionar terminais ao conector da controladora; distinguir contato, alimentação da luz, referência, possível matriz e circuito de potência. Mapear crédito separadamente. Um nome no chicote não fornece esse mapa.
4. **Medições energizadas posteriores, exclusivamente planejadas e executadas/supervisionadas por profissional qualificado:** tensões DC/AC e forma de onda entre os pontos documentados, polaridade, varredura, referências, corrente de detecção/carga por método apropriado, níveis aberto/fechado e transientes. Sonda/analisador deve tolerar os níveis e o modo comum; aterramento de osciloscópio pode criar curto. Não se propõe colocar amperímetro entre terminais desconhecidos.
5. **Comportamento original:** documentar início/consumo de crédito, captura, neutro, limites e resposta à soltura. A PCB pode continuar um ciclo automático mesmo com todos os comandos externos liberados. Estado inativo da interface não prova motores parados.
6. **Especificação da interface:** preencher a tabela abaixo e escolher componente, driver, proteção, isolamento, alimentação, conector e estado de falha. A aprovação pertence ao projeto elétrico/ensaio descrito em [08](08-plano-validacao.md).

| Parâmetro a registrar por comando | Situação nesta investigação |
|---|---|
| Origem, destino, conector, posição e orientação | NÃO IDENTIFICADO |
| Neutro, contatos por posição e retorno comum | NÃO IDENTIFICADO |
| DC/AC/varredura, amplitude, polaridade e referência | NÃO IDENTIFICADO |
| Corrente de detecção/carga e transientes | NÃO IDENTIFICADO |
| Limites de resistência ligada, fuga e capacitância aceitáveis | NÃO IDENTIFICADO |
| Tempo mínimo reconhecido, máximo permitido e repetição | NÃO IDENTIFICADO |
| Consumo de crédito, borda/nível de captura e sinal de fim | NÃO IDENTIFICADO |
| Tempo físico até parar e comportamento em falha | NÃO IDENTIFICADO |

## Integração reversível e contenção de falhas

Após validação, um chicote adaptador removível poderá reproduzir o comportamento identificado, preservando as conexões e sensores originais. A topologia concreta depende do levantamento: ligação em paralelo só faria sentido se for eletricamente compatível, e exigiria bloquear uso simultâneo local/remoto. Uma conexão em paralelo sem arbitragem permite, por exemplo, jogador remoto mandar direita enquanto alguém segura esquerda. Não apresentamos pontos a unir, pontes, numeração elétrica ou ligação definitiva.

A camada local deverá nascer inibida, não usar pinos que pulsem ao boot sem contenção externa e exigir sessão nova após reinicialização. Intertravamentos e tempo máximo devem existir localmente e ser testados em bancada. A saída deve permanecer inativa sem alimentação do controlador e após desconexão; isso é requisito a verificar, não propriedade presumida de qualquer módulo. Watchdog de software não cobre contato soldado ou semicondutor em curto: a análise de riscos deve definir contenção independente e parada local. Não se deve interromper arbitrariamente a sustentação da garra sem avaliar queda.

O resultado que falta é um **mapa elétrico e funcional de C04/C05**. Ele decide se A é uma adaptação simples de entradas ou se a investigação precisa migrar para outra interface.
