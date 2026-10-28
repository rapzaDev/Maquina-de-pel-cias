# 02 — Identificação do hardware

Data da consulta pública: 21/10/2026. Evidências Fxx referem-se ao [inventário](01-inventario-fotografico.md) e ao [manifesto](../evidencias/manifesto.json). Nenhuma medição elétrica, leitura de firmware ou ligação física foi realizada.

## Resultado e limites

A máquina é **CONFIRMADO** um gabinete de captura de pelúcias com arte “Fun Time”. Seu fabricante legal, modelo e revisão são **NÃO IDENTIFICADO**. O nome da arte não basta para atribuir fabricante. A fonte tem identificação muito mais forte que o gabinete: etiqueta **WM / wangma, WM-ATX400-24-48**. A controladora tem adesivo **PG01**, mas não encontramos comprovação de que isso seja um modelo de PCB, e não uma identificação de programa/lote.

| ID | Componente / identificação | Classificação | Evidência e qualidade | Documentação e pendência |
|---|---|---|---|---|
| C01 | Gabinete “Fun Time”, captura de pelúcias | CONFIRMADO para nome da arte; NÃO IDENTIFICADO para fabricante/modelo/revisão | F01, F05, F35–F37; alta para arte | Não foi localizado manual oficial inequivocamente correspondente. Fotografar plaqueta de identificação, número de série e notas/manuais do proprietário |
| C02 | Placa principal verde, banco de relés, circuitos de potência, diversos chicotes; adesivo PG01 | CONFIRMADO para existência/adesivo; NÃO IDENTIFICADO para fabricante/modelo/revisão | F18–F20, F24–F26; alta para topologia geral | Não foi encontrado esquema, manual ou repositório oficial correspondente à placa. Fotografar bordas e verso, sem desmontagem energizada; não remover adesivos apenas para investigar |
| C03 | Fonte WM / wangma WM-ATX400-24-48 | CONFIRMADO como inscrição na etiqueta | F27–F28; alta, sobretudo F28 e [recorte](../evidencias/recortes/F28-hardware.png) | Catálogo atual da Guangzhou Wangma localizado; não foi localizado datasheet oficial desse modelo exato |
| C04 | Joystick com esfera transparente iluminada | CONFIRMADO para comando visível; PROVÁVEL para base de contatos mecânicos | F05 e F06–F09; média/alta | Conjunto amarelo simétrico com atuador branco e lâminas metálicas favorece contatos de lâmina; fabricante, terminais, comum e circuito não identificados. Ver [investigação dos controles](04-investigacao-controles.md) |
| C05 | Botão circular iluminado de captura | CONFIRMADO para presença; PROVÁVEL para função pelo contexto do painel | F05, F35–F36; alta para forma | Verso/terminais do botão não individualizados com certeza. Modelo e contato versus circuito eletrônico desconhecidos |
| C06 | Display de jogo e placa traseira com conector multipolar | CONFIRMADO para display | F05–F09; média | Código traseiro insuficientemente nítido; leitura candidata não é identificação. Documentação de controlador gráfico semelhante não fornece pinagem deste módulo |
| C07 | Aceitador comparador de moeda; etiqueta “CPU / ELECTRONIC COMPARABLE COIN MECH”, alavanca “REPLACE COIN” | CONFIRMADO para descrição da etiqueta; NÃO IDENTIFICADO para modelo | F11–F16; média/alta; [recorte](../evidencias/recortes/F13-hardware.png) | “CPU” não é fabricante confirmado. QR e texto lateral exigem macro frontal. Alimentação, saída, polaridade e tempos não documentados |
| C08 / C09 | Dois conjuntos de recepção de cédulas, superior e inferior | PROVÁVEL quanto à função; CONFIRMADO para dois mecanismos | F10, F17, F32–F33; média | Etiquetas “ALPHA” parecem etiquetas de manutenção; não comprovam fabricante. Exigem plaqueta completa de cada unidade; não assumir protocolos ou mesma configuração |
| C10 | Barra eletrônica no compartimento inferior, fileira de elementos marcados T/S | CONFIRMADO para placa; PROVÁVEL como detector óptico de passagem/prêmio | F21–F22, F31; boa em F31 | Lê-se T1/S1 e série de posições T/S, LED, ajuste e conector. Código/modelo, direção óptica e tipo de saída não confirmados. Não foi localizado manual exato |
| C11 | Carro superior, trilhos, roldanas, engrenagens e suspensão | CONFIRMADO | F02; alta para mecanismo | Motores, redução, limites de curso, sensores e suas etiquetas não suficientemente expostos. Não há especificação para escolher drivers |
| C12 | Garra de três dedos, cilindro central, bielas e cabo espiral | CONFIRMADO para construção; PROVÁVEL como atuação eletromagnética | F02; alta para mecânica | Bobina/atuador, resistência e regime de força não identificados. A presença de 48 V na fonte não prova tensão aplicada à garra |
| C13 | Câmera interna branca/preta com alimentação por cabo | CONFIRMADO | F04, F35–F37; alta para presença | Marca pequena não tem foco suficiente para transcrição confiável; não determinar modelo, RTSP, ONVIF, WebRTC ou acesso local pela aparência |
| C14 | Painel de serviço com voltímetro CC 0–50 V, interruptor, botões e contadores | CONFIRMADO | F34; alta para instrumentos, baixa para função dos botões | Ausência de legenda funcional impede usar botões como crédito/teste. A posição do ponteiro na foto não é medição confiável |
| C15 / C16 | Iluminação e chicotes | CONFIRMADO para presença | F01–F37 | Não individualizar tensão das luzes ou destinos de todos os fios pela cor |
| C17 | Relés com logotipo HF e inscrição JQX-115F; marcação 24VDC visível | CONFIRMADO para inscrições legíveis; PROVÁVEL para família Hongfa | F20, F25–F26 e [ampliação](../evidencias/recortes/reles.png); média/alta | Linha de variante começa por 024; sufixo completo não suficientemente seguro. Datasheet oficial atual HF115F é referência da família, não valida substituição ou ligações desta PCB |
| C18 | CI de controle com marcação inicial IAP / 15… | CONFIRMADO para marcação parcial; PROVÁVEL como MCU da família STC/IAP15 | F20, F25–F26 e [recorte](../evidencias/recortes/mcu2.png); média/baixa | Modelo exato NÃO IDENTIFICADO. Catálogo STC15/IAP15 é compatível com a pista, sem autorizar pinagem ou gravação |
| C19 | Conector lateral com serigrafia 12V, GND, RXD, TXD, 5V; D-sub superior; pads inferiores esquerdos | CONFIRMADO para inscrições visíveis; PROVÁVEL para porta serial no lateral | F18–F20, F25–F26; alta | Não há protocolo publicado, níveis ou funções comprovados. D-sub não implica RS-232. A fileira inferior “5V / OE / RC / SC / DAT / 12V / GND / GND…” não é uma API conhecida |

## Fonte: transcrição e consequências verificáveis

A etiqueta de C03 declara:

- Modelo **WM-ATX400-24-48**; marca **WM: wangma** e texto chinês Guangzhou Wangma.
- Entrada **100–240 V AC, 4 A, 50/60 Hz**.
- Saída **+5 V: 0,5–12 A MAX**; **+12 V: 6 A MAX**; **+24 V: 6 A MAX**; **+48 V: 6 A MAX**.
- **TOTAL MAX POWER: 320 W**.
- Pequena tabela de conectores A/B com indicação de posição e cores; endereço de site lido como **wmsps.com**.

Isto comprova a especificação **impressa**, não os valores medidos, a saúde da fonte, sua certificação ou uma capacidade extra disponível. Os limites de corrente não podem ser somados como cargas simultâneas: o limite total também deve ser respeitado, além de possíveis restrições cruzadas não publicadas. “ATX” no código não torna a fonte intercambiável com uma ATX de computador. A tabela de cores vale como etiqueta deste item; não determina destinos no chicote nem substitui identificação de orientação do conector.

A serigrafia da controladora mostra os caracteres 48V, 12V, 24V e 5V nas regiões de alimentação/indicadores, coerentes em magnitude com a fonte. O [recorte da entrada](../evidencias/recortes/F20-entrada-alimentacao.png) permite ler 12V, 48V e GND; sinal ou pequeno traço adjacente a 48V não foi transcrito como polaridade comprovada. A correspondência de distribuição é **PROVÁVEL**, sem rastreamento de todos os condutores nem pinagem validada; a etiqueta +48 V da fonte não resolve a orientação da PCB. Não se deve alimentar um gateway a partir dela antes de avaliar isolamento, consumo, carga existente, transientes e retorno de corrente.

A página [Guangzhou Wangma — fabricante](https://www.wmsps.cn/) identifica a empresa como fabricante de fontes e lista aplicações em automação e equipamentos de entretenimento. A ferramenta retornou a página inicial como HTML com 218 linhas e conteúdo textual do fabricante, além de uma resposta do [catálogo](https://www.wmsps.cn/Product.html) com 138 linhas; o modelo exato não foi localizado no material retornado. Não foi baixado manual ou datasheet desse modelo; o acesso foi parcial e uma abertura posterior pela investigação principal encontrou timeout. A identidade empresarial é compatível com a etiqueta, mas a página atual não autentica o exemplar físico. O endereço antigo [wmsps.com](http://wmsps.com) não pôde ser acessado pela ferramenta nesta consulta.

## Relés e acionamento

As fotografias mostram relés eletromecânicos e semicondutores de potência na própria controladora. A inscrição JQX-115F e o símbolo HF sustentam a pista Hongfa. A documentação oficial da [família HF115F](https://www.hongfa.com/product/industrial-relay/HF115F) oferece datasheet e variantes; ainda precisamos de macro de um relé para vincular sufixo, arranjo de contatos e bobina ao modelo específico. Esta referência não fornece o esquema da máquina.

Não foi identificada a referência dos componentes de potência adjacentes ao dissipador ou dos encapsulamentos de três terminais. Não há evidência suficiente para chamá-los de ponte H específica, controladores de passo ou MOSFET de modelo determinado. Correntes, polaridade, reversão dos motores e método de controle da força da garra permanecem pendentes.

## Revisão dos circuitos integrados menores

A inspeção adicional dos recortes F19/F20/F25/F26, incluindo [F20 rotacionado](../evidencias/recortes/F20-ci-rot.png), permite registrar os seguintes limites de leitura sem atribuir novas pinagens à placa:

| Região de C02 | Leitura / interpretação | Classificação e limite |
|---|---|---|
| Dois CIs de aproximadamente 20 terminais próximos ao MCU, um junto de C81 e outro acima de C98 | Inscrição **74HC245D** legível com maior clareza em F20, reiterada por F26 | CONFIRMADO para inscrição; fabricante do exemplar não identificado com segurança. Correspondência da função à família é PROVÁVEL; não sabemos quais linhas da máquina passam por esses CIs |
| CIs menores adjacentes ao banco de relés | Há marcações, mas os caracteres do código não são suficientemente separados para transcrição completa | NÃO IDENTIFICADO; não registrar ULN2003, ULN2803 ou 74HC específico por expectativa de circuito |
| Repetição de encapsulamentos com quatro terminais junto aos conectores inferiores e acima do MCU | Estrutura e disposição são compatíveis com optoacopladores | PROVÁVEL para tipo; código NÃO IDENTIFICADO. Não se pode assumir relação de transferência, polaridade, barreira elétrica ou isolamento funcional de todo o circuito |
| Encapsulamentos de potência com aba metálica | Código frontal não legível | NÃO IDENTIFICADO; não escolher transistor/driver por encapsulamento |

A página oficial [Nexperia 74HC245D](https://www.nexperia.com/product/74HC245D), aberta e lida nesta consulta, documenta um transceptor lógico bidirecional de oito bits com saídas em três estados e controles OE/DIR. Essa informação explica a existência possível de buffers de barramento entre circuitos; não transforma a PCB em um barramento externo documentado e não identifica o circuito do joystick. O fabricante exato do exemplar fotografado permanece pendente. O [datasheet da família](https://assets.nexperia.com/documents/data-sheet/74HC_HCT245.pdf) foi localizado por busca oficial; seu conteúdo indexado foi retornado, sem inspeção integral do PDF.

## MCU, firmware e interfaces

A gravação parcial “IAP / 15…” levou ao [datasheet oficial STC15, incluindo IAP15](https://stcmicro.com/datasheet/STC15-English.pdf), localizado por busca no domínio do fabricante. O texto indexado retornado inclui o nome STC15 e menção à série IAP15; não se leu o PDF integral nem se validaram suas páginas/pinagens. A tentativa posterior de acesso direto da investigação principal não disponibilizou o PDF. A pista é coerente com um microcontrolador programável, mas não identifica seu modelo nem seu firmware. Ser da família não garante possibilidade de extração, acesso livre à memória ou protocolo operacional. Não foi executado software STC-ISP e não se deve utilizar função de gravação ou apagamento para identificar o CI.

A serigrafia RXD/TXD é a melhor pista de uma interface nativa. Ainda não comprova UART TTL/CMOS, RS-232, RS-485, velocidade, orientação do conector, recepção de comandos ou função ativa no firmware PG01. É possível que seja destinada a manutenção, programação ou a um módulo ausente. Não conectar adaptador USB serial, analisador ou GPIO antes de verificar eletricamente a interface e documentar o CI associado.

## Pesquisa documental: o que foi e não foi encontrado

| Busca baseada na evidência | Resultado desta consulta | Uso permitido da informação |
|---|---|---|
| Fun Time + crane/máquina de garra/manual; PG01 + claw/placa/pelúcia | Nenhum manual oficial inequivocamente vinculado às fotos | Manter fabricante e modelo como NÃO IDENTIFICADO; homônimos de outros produtos não identificam esta máquina |
| WM-ATX400-24-48; Guangzhou Wangma; domínio impresso | Fabricante compatível localizado; datasheet exato ausente | Etiqueta física é a fonte principal das especificações; solicitar documentação pelo canal do proprietário/fornecedor |
| JQX-115F / HF115F | Família oficial Hongfa localizada | Referência de família; não escolher variante nem importar esquema de circuito semelhante |
| IAP15 / STC15 | Datasheet da família localizado e trecho indexado retornado; PDF integral não inspecionado | Pista para nova fotografia e identificação posterior; sem atribuir pinagem |
| CPU ELECTRONIC COMPARABLE COIN MECH / REPLACE COIN | Descrição genérica repetida em equipamentos distintos | Não chamar C07 de TW-130B, HG-818, CH-926 ou outro modelo por semelhança |
| ALPHA e mecanismo receptor | Inscrição insuficiente para fabricante/modelo | Precisar etiqueta de cada unidade antes de buscar manual de manutenção |
| Barra T/S, câmera, motores, joystick e botão sem códigos seguros | Sem chave de busca exclusiva para modelo | Nenhum datasheet de similar é tratado como documentação deste exemplar |

As buscas não encontrarem um manual não prova que ele não exista. Não localizamos repositório técnico verificável para o firmware/PCB exatos. A etapa documental só poderá fechar quando surgir identificação do fabricante/PCB, um manual original ou um levantamento elétrico correspondente.

## Fotografias/documentos que fecham identificação

Solicitar em inspeção desenergizada apropriada: plaqueta do gabinete; visão ortogonal completa da frente e verso da PCB e bordas; macro sem reflexo de C18, C17 e semicondutores de potência; verso e etiquetas de C04/C05; etiquetas de C08 e C09 separadamente; QR/etiqueta completa de C07; modelo da câmera e motores; detalhes dos limites do carro; ambos lados da barra C10 e orientação no caminho do prêmio. O objetivo é registrar, sem mudar conexões, quais chicotes chegam a cada componente. O primeiro levantamento físico prioritário é o circuito dos controles C04/C05, conforme [plano de validação](08-plano-validacao.md).
