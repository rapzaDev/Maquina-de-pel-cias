# 11 — Segunda investigação focalizada

Data: 24/10/2026. Escopo: preservação, inspeção individual das fotografias e investigação documental. **A integração A continua sendo a prioridade de investigação; nenhum circuito ou controle remoto foi demonstrado.** Os relatórios 01–10 e o README foram preservados. O dossiê recebido permanece como material preliminar, separado deste relatório.

## Preservação concluída antes da investigação

**CONFIRMADO: 37 fotografias persistidas, 37 SHA-256 distintos, 37 aberturas visuais individuais bem-sucedidas, zero arquivos inacessíveis.** Cada original foi aberto com `view_image`; decodificação, pranchas e descrições anteriores não substituíram essa abertura. Foco insuficiente para ler uma inscrição não foi tratado como falha de abertura nem como identificação positiva.

Foram localizados:

- Pasta fornecida: `/Users/ti/Downloads/Pacote_Completo_Maquina_Pelucia_Codex/`.
- `/Users/ti/Downloads/Arquivo.zip`: 37 fotografias; todas coincidem com os originais locais.
- `/Users/ti/Downloads/Pacote_Completo_Maquina_Pelucia_Codex.zip`: 37 fotografias, dez imagens derivadas, dossiê técnico, manifesto e dois textos de orientação.

As 37 fotos já existiam em `evidencias/fotos/`: os bytes foram conferidos contra a pasta recebida, o manifesto recebido e ambos os ZIPs. Não foi necessário substituir nenhuma foto. Os arquivos do dossiê foram mesclados em `evidencias/dossie/` com rejeição de conflitos de conteúdo. Nenhum original foi convertido, recomprimido, redimensionado ou renomeado. A preservação se refere aos arquivos recebidos; não permite afirmar que sejam arquivos brutos anteriores ao envio pelo WhatsApp.

O [manifesto atualizado](../evidencias/manifest_fotos.csv) contém nome original, bytes, dimensões, SHA-256, origem, resultado visual individual e observação. O [manifesto recebido preservado](../evidencias/dossie/manifest_fotos-recebido.csv) conserva o registro anterior à atualização. A [verificação de persistência](../evidencias/verificacao-persistencia-2026-10-24.json) registra hashes da origem/destino e dos ZIPs. O [manifesto da primeira etapa](../evidencias/manifesto.json) mantém os IDs F01–F37, que continuam válidos. A ordem lexicográfica da inspeção atual é uma coluna distinta; não renumera os IDs antigos.

## O que esta rodada acrescenta

| Resultado | Situação em relação à primeira etapa | Classificação e consequência |
|---|---|---|
| Auditoria independente das 37 fotos contra duas distribuições ZIP e o manifesto recebido | Nova verificação; a preservação já era afirmada em 01 | **CONFIRMADO** para igualdade dos bytes e abertura individual nesta rodada |
| CI com inscrição parcial `IAP/15…` e CI sob `PG01` são componentes fisicamente distintos | Explicitação adicional a partir de F20/F25/F26 | **CONFIRMADO** para dois encapsulamentos; não atribuir o programa do primeiro ao segundo |
| Datasheet oficial STC15F2K60S2 disponível por uma URL alternativa, com IAP15F2K61S2 na capa | Nova consulta documental; o acesso integral falhara em 02 | **CONFIRMADO** para conteúdo retornado da capa/sumário; modelo exato da fotografia continua **NÃO IDENTIFICADO** |
| Protocolo público CNGPI localizado na busca chinesa | Nova pista documental | **CONFIRMADO** para documento de referência; implementação nesta máquina **NÃO IDENTIFICADA** |
| Porta de cinco posições e região com footprints sem componentes junto a RXD/TXD | Detalhamento da observação de áreas não populadas já feita em 06 | **CONFIRMADO** visualmente; população/opções de revisão precisam entrar no levantamento |
| Falta de vínculo completo entre etiquetas, periféricos, contadores e sensores | Pendência reiterada, não descoberta de nova função | Impede converter pulso ou ACK em início/fim/prêmio confirmado |

Não se apresentam como novidades a fonte multissaída, os sete relés, os dois 74HC245D, a hipótese de contatos de lâmina ou a arquitetura de sessão exclusiva: esses pontos já constavam dos relatórios anteriores.

## Controladora, componentes e identidade

Em **F20 — `WhatsApp Image 2026-10-21 at 19.14.59 (4).jpeg`**, corroborada por F25/F26, há sete relés, dissipador, botão `SET`, D-sub, conectores inferiores e dois CIs quadrangulares distintos: um com gravação parcial `IAP/15…`, outro coberto por `PG01`. O [recorte existente de F20](../evidencias/recortes/F20-ci-rot.png) e o [detalhe do IAP](../evidencias/recortes/mcu2.png) ajudam a localizar os componentes, sem recuperar caracteres ausentes.

**CONFIRMADO:** presença e posição desses elementos. **PROVÁVEL:** o CI IAP pertence à família STC/IAP15. **NÃO IDENTIFICADO:** fabricante/revisão da PCB, código completo dos CIs, função do componente sob PG01 e significado da etiqueta. Não há base para identificar dois microcontroladores, chamar PG01 de firmware de movimento ou atribuir esse nome à placa inteira.

Os dois CIs `74HC245D`, já registrados na etapa 1, são compatíveis com buffers/transceptores lógicos. A ficha [Nexperia 74HC245D](https://www.nexperia.com/product/74HC245D) descreve um transceptor de oito bits com três estados. Isso não identifica a marca dos exemplares nem estabelece relação elétrica com o conector RXD/TXD. Não foi identificado um transceptor RS-232 ou RS-485 por código legível nas fotos; isso não prova sua ausência na placa.

A [documentação oficial STC15F2K60S2](https://www.stcmicro.com/datasheet/STC15F2K60S2-en.pdf) inclui IAP15F2K61S2/IAP15L2K61S2, duas UARTs e programação ISP/IAP; o sumário distingue interfaces com conversores RS-232 e USB. São capacidades da família documentada, sem vínculo comprovado com os sinais desta PCB. O retorno textual identifica 887 páginas; foram examinados os trechos retornados da capa e sumário. Não houve leitura integral nem inspeção visual bem-sucedida do PDF. O download local retornou HTTP 403 e consultas posteriores oscilaram entre erro e timeout. Nenhuma pinagem foi transferida para a máquina.

**Fabricante da máquina e da PCB: NÃO IDENTIFICADO.** Arte Fun Time, fonte Wangma e componentes de fornecedores conhecidos não demonstram quem projetou ou montou a controladora. As buscas em três idiomas não trouxeram manual inequivocamente correspondente ao conjunto fotografado.

## RXD/TXD: duas perguntas independentes

Em F20/F19/F25/F26 e no [recorte recebido da porta](../evidencias/dossie/recorte_placa_serial.png), lê-se `12V`, `GND`, `RXD`, `TXD`, `5V` ao lado de um conector aparentemente sem cabo nas vistas disponíveis. **CONFIRMADO:** inscrições e cinco posições. **NÃO IDENTIFICADO:** níveis, referência, sentido visto pela placa, continuidade, velocidade, protocolo e finalidade.

Há footprints não populados próximos, incluindo U33/U34 e posições de componentes passivos. Isso exige registrar a população da revisão real. Não demonstra porta desativada: as trilhas podem contornar componentes opcionais, e as fotos não mostram todas as camadas/face inferior.

| Hipótese | Evidência favorável | Lacuna decisiva e forma de resolvê-la |
|---|---|---|
| Canal serial operacional de periférico/crédito/telemetria | RXD/TXD e alimentações adjacentes | Manual vinculado à revisão ou captura passiva profissional, após caracterização elétrica, correlacionada aos eventos originais |
| Programação/manutenção de um CI | Pista IAP e documentação da família | Rastreio profissional desenergizado da porta ao CI identificado; não executar programador para descobrir |
| Porta de movimento/captura | Possibilidade abstrata de firmware | Não há comando documentado nem tráfego disponível; exige documentação específica e comportamento demonstrado |
| Interface opcional incompleta nesta revisão | Região próxima parcialmente não populada | Levantamento de trilhas e componentes das duas faces por profissional |

O [documento público CNGPI](https://github.com/frankroad/CNGPI) descreve integração de periféricos, crédito, estados e resultados. Sua interface fixa tem quatro posições e níveis TTL de 3,3 V; a fotografia mostra cinco posições, incluindo 5 V. O texto diferencia crédito, notificação de início enviada pela máquina e notificação de término com resultado, usando identificadores transacionais. O índice consultado não documenta comandos de direção do joystick. Há trechos incompletos e referências de versão inconsistentes. **Não há evidência de CNGPI nesta PCB.** A divergência física impede tratar a porta como compatível por encaixe; tampouco exclui implementação elétrica distinta. A utilidade é formular perguntas ao fornecedor sobre crédito/telemetria separadamente de movimento. A referência upstream indicada no texto, `xsharkx/CNGPI`, retornou 404; o material acessível está no repositório citado.

A outra fileira de pads, no canto inferior esquerdo de F20, lê-se como `5Vb`, `OE`, `RC`, `SC`, `DAT`, `12V`, `GND`, `GNDb` no [recorte recebido](../evidencias/dossie/recorte_placa_conector_esquerda.png). Esta leitura refina a transcrição anterior; os sufixos não comprovam fontes ou terras isolados. O conjunto de nomes é diferente de RXD/TXD. Sua função continua **NÃO IDENTIFICADA**; não chamar de UART, SPI, display ou porta de expansão utilizável sem rastreio.

## Joystick e botão: o que separa as alternativas

**F05 — `19.14.59 (19).jpeg`** mostra topo do joystick iluminado, LCD e botão. **F06–F09 — `19.14.59 (18)` a `(15).jpeg`** mostram, por baixo, suportes amarelos, lâminas e atuador branco. O [recorte existente F09](../evidencias/inspecao/F09-mecanismo-amarelo.png) favorece contatos mecânicos. A relação contínua eixo–atuador–terminais ainda não está documentada. Iluminação e contatos devem ser identificados separadamente.

**PROVÁVEL:** joystick por contatos de lâmina. **NÃO IDENTIFICADO:** comum, polos, matriz, sinal analógico adicional, tensão/corrente, destino na PCB e contato do botão. O [catálogo de interruptores Baolian](https://www.bao-lian.com/en/products/microswitches/) é referência de tecnologia; não identifica o conjunto amarelo como produto desse fabricante.

| Resultado do levantamento futuro | Interface que passa a ser candidata | O que ainda precisa atender |
|---|---|---|
| Contatos passivos independentes de baixa energia | Relé de sinal/reed ou chave isolada bidirecional | Carga mínima/máxima, resistência, fuga, tempos, estado sem alimentação e falha fechada |
| Matriz/varredura | Fechamento flutuante compatível por contato/polo | Polaridade variável, capacitância, fuga e tempo de reconhecimento; não impor comum |
| Entrada DC unidirecional comprovada | Optotransistor, se compatível | Polaridade, saturação, corrente e velocidade |
| Analógico ou mensagem digital do painel | Emulação própria do sinal documentado | Neutro e transferência/protocolo; fechamento de contato não resolve |
| Contato conduz potência | Reavaliar a fronteira da adaptação | Nenhuma das opções de baixo sinal é aprovada por aparência |

A evidência prioritária é **um levantamento profissional desenergizado do conjunto joystick/botão até o conector de destino**, com vista contínua do eixo/base, macros dos terminais e tabela de continuidade em neutro/quatro direções/botão, com os contatos adequadamente isolados da eletrônica. Esse resultado discrimina contatos, polos e comuns. Só uma caracterização elétrica posterior planejada determina se há varredura e quais limites a interface deve cumprir. Não se atribuem posições numéricas ou funções por cor dos fios.

## Crédito, partida, captura e prêmio

O aceitador em **F11–F16 — `19.14.59 (13)` a `(8).jpeg`** exibe `CPU ELECTRONIC COMPARABLE COIN MECH` e `REPLACE COIN`. Isso identifica a classe de periférico, sem modelo ou protocolo. Em F16 há três condutores visíveis no conector inferior; quantidade e cor não comprovam alimentação, sinal ou polaridade. Os dois mecanismos na porta, vistos em F17/F32/F33, continuam **PROVÁVEIS** validadores de cédulas, sem prova de operação.

**F24 — `19.14.59.jpeg`** mostra etiquetas `CRÉDITO` e `PRÊMIO` próximas à placa. Os condutores entram em feixes e o trajeto completo até aceitadores, barra e contadores não é visível. **F34 — `19.14.52 (1).jpeg`** mostra dois contadores no painel de serviço; suas funções não têm legenda suficiente. Assim, `PRÊMIO` também pode denominar circuito de contagem, e não necessariamente o fio de um sensor. Essa é hipótese concorrente, não nova identificação.

| Evento | O que seria uma confirmação válida | Situação atual |
|---|---|---|
| Crédito reconhecido | Mudança observável no saldo/controladora, correlacionada ao método original | Não há registro de operação ou forma de onda |
| Início/consumo de partida | Transição observável da máquina, distinguindo crédito acumulado de jogo em andamento | LCD estático e etiquetas não resolvem |
| Pedido de captura | Entrada do botão reconhecida ou evidência equivalente | Um fechamento solicitado pelo gateway não comprova aceitação |
| Término/retorno | Estado original validado de ciclo encerrado/pronto | Relógio web e ausência de comando não bastam |
| Passagem de objeto na saída | Detector identificado, caracterizado e correlacionado à passagem | Barra óptica candidata, vínculo não demonstrado |
| Prêmio registrado pela máquina | Estado/contador validado com semântica conhecida | Não confundir com comando de captura ou objeto momentaneamente agarrado |

A barra em **F31 — `19.14.53.jpeg`**, instalada conforme F22, tem fileira de elementos, CIs, ajuste e chicote de quatro fios. **PROVÁVEL:** sensor óptico da saída. **NÃO IDENTIFICADO:** tipo de saída, lógica, qual objeto detecta, ligação à etiqueta PRÊMIO e tratamento de obstrução. A foto não demonstra unidade pareada, protocolo ou sensor pronto para ligar a GPIO.

A forma segura de fechar cada trajeto é um único mapa de continuidade desenergizado, executado por profissional, identificando ambas as extremidades e orientação de cada conector. A etapa funcional posterior deve correlacionar sinais com eventos originais supervisionados. Sem isso, a PoC mantém crédito pelo método original e prêmio como **não confirmado**.

## Câmera e REA

**F04 — `19.14.59 (20).jpeg`**, F35–F37 e F01 confirmam câmera interna branca/preta e cabo. O nome pequeno na base continua sem leitura segura. Modelo, fluxo local, autenticação, codec e latência são **NÃO IDENTIFICADOS**. A única evidência de identificação necessária é a etiqueta/modelo obtida sem divulgar senha/QR de provisionamento. Só depois se consulta o manual e se mede vídeo local; nenhuma promessa de RTSP, ONVIF ou WebRTC decorre da aparência.

No projeto e pacote foram encontrados fotografias, derivados, textos e manifestos; nenhum firmware, executável proprietário ou captura de sinais/rede. Não há ferramenta REA no catálogo da sessão, `rea` no PATH, diretório `~/.rea` ou skill nos dois caminhos usuais verificados. Isso não é varredura de todo o computador.

O [guia oficial de firmware REA](https://github.com/morluto/rea/blob/main/docs/firmware-analysis.md) descreve inspeção/extração com Binwalk/Unblob e limitações para bytes brutos. O [guia de gravações](https://github.com/morluto/rea/blob/main/docs/signal-recordings.md) exige gravação prévia, ferramentas do usuário e Linux; não adquire sinais nem adivinha fiação. **Decisão:** não usar/instalar REA nesta etapa. Não há arquivo de entrada pertinente, e a documentação não resolve o circuito a partir destas fotos. Nada foi instalado ou configurado.

## Registro de consultas e limites

Consultas públicas realizadas em 24/10/2026. Resultados de terceiros serviram apenas para localização; nenhuma pinagem ou identidade foi adotada de anúncio, homônimo ou manual de outra placa.

| Idioma / consulta | Resultado aproveitável |
|---|---|
| PT: `"placa" "pelúcia" "RXD" "TXD"`; `"Fun Time" "placa" "pelúcia" manual`; `"PG01" "controladora" pelucia` | Nenhuma identificação inequívoca; homônimos descartados |
| EN: `"PG01" "claw" board`; `"claw machine" "7 relay" board`; `claw machine mainboard manual UART 12V GND RXD TXD 5V` | Nenhuma correspondência comprovada; manual de outra máquina localizado, acesso direto indisponível |
| ZH: `"PG01" "娃娃机" 主板`; `"娃娃机主板" "RXD" "TXD"`; `"娃娃机" "主板" "串口" 协议`; `"娃娃机" "主板" "七" "继电器"` | CNGPI localizado; sete relés não identificam modelo/fabricante |
| EN/ZH: `"IAP15" UART ISP STC official`; `site.stcmicro.com IAP15F2K61S2 UART ISP` | Fonte oficial STC alternativa; comprova capacidades de família, não identidade da placa |
| EN: `"CPU electronic comparable coin mech" manual manufacturer`; busca da inscrição no domínio Weiya | Sem manual vinculado ao exemplar; modelo continua desconhecido |
| EN: `"morluto/rea"` e guias oficiais | Escopo de software/arquivos; nenhum artefato local pertinente |

Links de verificação adicionais: [catálogo Baolian de joysticks](https://www.bao-lian.com/en/products/joysticks/); [REA oficial](https://github.com/morluto/rea); [manual Neofuns localizado, mas não acessível nesta rodada](https://www.neofuns.com/wp-content/uploads/2017/09/31-Single-Claw-Crane-Machine-V4.3-003-Manual.pdf). A URL genérica STC15-English citada na etapa 1 continuou inacessível; a alternativa específica acima retornou texto, mas não download local. Ausência de resultado não prova inexistência de documentação.

## Hipóteses excluídas como fundamento de projeto

- `Fun Time` comprova fabricante; `PG01` comprova modelo da PCB: **sem sustentação**.
- `RXD/TXD` comprova UART TTL compatível, CNGPI ou comandos de movimento: **sem sustentação**.
- `CPU` do moedeiro é a CPU central: **incompatível com o contexto do periférico fotografado**.
- Etiqueta `PRÊMIO` identifica necessariamente saída lógica de vitória: **sem sustentação**.
- Cinco comandos de jogador exigem cinco fios, comum GND ou módulo genérico de relés: **sem sustentação**.
- Porta silenciosa ou footprints vazios provam interface inexistente: **sem sustentação**; não houve captura de sinais.

Essas exclusões impedem adotar premissas; não demonstram fisicamente a impossibilidade de cada tecnologia. O [plano de PoC](12-plano-prova-de-conceito.md) define quais evidências mudariam a decisão.

## Registro das 37 aberturas individuais

Todas as linhas abaixo correspondem a originais efetivamente abertos. Nenhuma foto ficou pendente. Os links apontam para os arquivos preservados; as observações delimitam o que foi legível.

| Ordem nesta rodada | ID anterior | Original inspecionado | Observação visual |
|---|---|---|---|
| 1 | F36 | [WhatsApp Image 2026-10-21 at 19.14.51 (1).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.51%20%281%29.jpeg) — aberta | Gabinete, jogador, câmera interna e painel. |
| 2 | F37 | [WhatsApp Image 2026-10-21 at 19.14.51.jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.51.jpeg) — aberta | Arte Fun Time e câmera ao fundo. |
| 3 | F34 | [WhatsApp Image 2026-10-21 at 19.14.52 (1).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.52%20%281%29.jpeg) — aberta | Painel de serviço, voltímetro, botões e dois contadores; funções sem legenda. |
| 4 | F33 | [WhatsApp Image 2026-10-21 at 19.14.52 (2).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.52%20%282%29.jpeg) — aberta | Periféricos na porta, aceitador lateral e chicotes; iluminação azul limita leitura. |
| 5 | F32 | [WhatsApp Image 2026-10-21 at 19.14.52 (3).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.52%20%283%29.jpeg) — aberta | Vista ampla dos dois mecanismos e aceitador lateral na porta. |
| 6 | F35 | [WhatsApp Image 2026-10-21 at 19.14.52.jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.52.jpeg) — aberta | Gabinete e painel em uso; não demonstra resposta elétrica. |
| 7 | F30 | [WhatsApp Image 2026-10-21 at 19.14.53 (1).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.53%20%281%29.jpeg) — aberta | Trecho de fiação e parede interna; destinos fora do enquadramento. |
| 8 | F29 | [WhatsApp Image 2026-10-21 at 19.14.53 (2).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.53%20%282%29.jpeg) — aberta | Chicote espiral e fios; não permite rastreio integral. |
| 9 | F28 | [WhatsApp Image 2026-10-21 at 19.14.53 (3).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.53%20%283%29.jpeg) — aberta | Etiqueta da fonte Wangma legível; valores nominais impressos. |
| 10 | F31 | [WhatsApp Image 2026-10-21 at 19.14.53.jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.53.jpeg) — aberta | Barra eletrônica, série de elementos e ajuste; função de prêmio provável. |
| 11 | F26 | [WhatsApp Image 2026-10-21 at 19.14.58 (1).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.58%20%281%29.jpeg) — aberta | Controladora frontal, sete relés, PG01 e conectores. |
| 12 | F25 | [WhatsApp Image 2026-10-21 at 19.14.58 (2).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.58%20%282%29.jpeg) — aberta | Controladora frontal e chicotes; RXD/TXD visíveis. |
| 13 | F27 | [WhatsApp Image 2026-10-21 at 19.14.58.jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.58.jpeg) — aberta | Fonte em vista geral; parte inferior da etiqueta desfocada. |
| 14 | F23 | [WhatsApp Image 2026-10-21 at 19.14.59 (1).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%281%29.jpeg) — aberta | Cabeamento interno e verso do painel de serviço; rotas parciais. |
| 15 | F14 | [WhatsApp Image 2026-10-21 at 19.14.59 (10).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2810%29.jpeg) — aberta | Aceitador comparador de moeda; inscrição CPU; gravações laterais desfocadas. |
| 16 | F13 | [WhatsApp Image 2026-10-21 at 19.14.59 (11).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2811%29.jpeg) — aberta | Aceitador de moeda em ângulo semelhante; lateral desfocada. |
| 17 | F12 | [WhatsApp Image 2026-10-21 at 19.14.59 (12).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2812%29.jpeg) — aberta | Aceitador de moeda e mecanismo ao fundo; desfoque impede modelo. |
| 18 | F11 | [WhatsApp Image 2026-10-21 at 19.14.59 (13).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2813%29.jpeg) — aberta | Aceitador e alavanca superior; foco parcial. |
| 19 | F10 | [WhatsApp Image 2026-10-21 at 19.14.59 (14).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2814%29.jpeg) — aberta | Mecanismo de transporte e etiqueta lateral; identidade não comprovada. |
| 20 | F09 | [WhatsApp Image 2026-10-21 at 19.14.59 (15).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2815%29.jpeg) — aberta | Mecanismo amarelo com lâminas e chicote sob painel; foco limitado. |
| 21 | F08 | [WhatsApp Image 2026-10-21 at 19.14.59 (16).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2816%29.jpeg) — aberta | Verso do LCD, conector longo e mecanismo amarelo; foco limitado. |
| 22 | F07 | [WhatsApp Image 2026-10-21 at 19.14.59 (17).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2817%29.jpeg) — aberta | Verso do LCD e lâminas do mecanismo amarelo; leitura parcial. |
| 23 | F06 | [WhatsApp Image 2026-10-21 at 19.14.59 (18).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2818%29.jpeg) — aberta | Mecanismo amarelo com lâminas em outro ângulo; terminais não mapeáveis. |
| 24 | F05 | [WhatsApp Image 2026-10-21 at 19.14.59 (19).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2819%29.jpeg) — aberta | Joystick iluminado, LCD parcialmente encoberto e botão iluminado. |
| 25 | F22 | [WhatsApp Image 2026-10-21 at 19.14.59 (2).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%282%29.jpeg) — aberta | Barra instalada na parede do compartimento e saída do chicote. |
| 26 | F04 | [WhatsApp Image 2026-10-21 at 19.14.59 (20).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%2820%29.jpeg) — aberta | Câmera interna, alimentação e suporte; marca/modelo sem leitura segura. |
| 27 | F21 | [WhatsApp Image 2026-10-21 at 19.14.59 (3).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%283%29.jpeg) — aberta | Extremidade da barra e conector; desfoque impede códigos. |
| 28 | F20 | [WhatsApp Image 2026-10-21 at 19.14.59 (4).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%284%29.jpeg) — aberta | Controladora frontal mais nítida, serigrafias RXD/TXD e pads de expansão. |
| 29 | F19 | [WhatsApp Image 2026-10-21 at 19.14.59 (5).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%285%29.jpeg) — aberta | Controladora frontal e chicotes inferiores. |
| 30 | F18 | [WhatsApp Image 2026-10-21 at 19.14.59 (6).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%286%29.jpeg) — aberta | Controladora oblíqua; serigrafias e potência com foco parcial. |
| 31 | F17 | [WhatsApp Image 2026-10-21 at 19.14.59 (7).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%287%29.jpeg) — aberta | Dois mecanismos na porta e aceitador de moeda lateral. |
| 32 | F16 | [WhatsApp Image 2026-10-21 at 19.14.59 (8).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%288%29.jpeg) — aberta | Lateral do aceitador, ajuste e conector com três fios visíveis. |
| 33 | F15 | [WhatsApp Image 2026-10-21 at 19.14.59 (9).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59%20%289%29.jpeg) — aberta | Etiqueta CPU Electronic Comparable Coin Mech; modelo não legível. |
| 34 | F24 | [WhatsApp Image 2026-10-21 at 19.14.59.jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.14.59.jpeg) — aberta | Vista de controladora/fonte e etiquetas CRÉDITO/PRÊMIO; trajeto interrompido. |
| 35 | F02 | [WhatsApp Image 2026-10-21 at 19.15.00 (1).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.15.00%20%281%29.jpeg) — aberta | Carro, roldanas, trilhos e garra; etiquetas de motores ausentes. |
| 36 | F01 | [WhatsApp Image 2026-10-21 at 19.15.00 (2).jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.15.00%20%282%29.jpeg) — aberta | Gabinete aberto, painel e câmera. |
| 37 | F03 | [WhatsApp Image 2026-10-21 at 19.15.00.jpeg](../evidencias/fotos/WhatsApp%20Image%202026-10-21%20at%2019.15.00.jpeg) — aberta | Conector de passagem do chicote da garra e cabo espiral; pinagem desconhecida. |
