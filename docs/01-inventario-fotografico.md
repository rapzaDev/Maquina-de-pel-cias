# 01 — Inventário fotográfico

Investigação documental em 21/10/2026. **37/37 fotografias abertas e inspecionadas visualmente**, incluindo ângulos semelhantes. Não houve teste físico. As classificações usadas em toda a série são **CONFIRMADO** (observável/documentado dentro do escopo declarado), **PROVÁVEL** (inferência sustentada) e **NÃO IDENTIFICADO** (evidência insuficiente). Confirmar uma inscrição não confirma seu funcionamento elétrico.

## Origem e método

O diretório de trabalho estava vazio; `./evidencias/fotos/` não existia no início. Os 37 arquivos anexados estavam acessíveis em `/Users/ti/Downloads/`. Foram copiados para o projeto sem alteração. Todos foram abertos e decodificados com Pillow já instalado; depois foram vistos nas dez pranchas em `evidencias/inspecao/`, além dos anexos e de ampliações dos detalhes relevantes. Decodificar não foi tratado como inspeção visual. Não há outras fotos originais no projeto nesta rodada. Pranchas e recortes são derivados, não novas fotografias.

O [manifesto](../evidencias/manifesto.json) registra ID, caminho original, cópia no projeto, dimensões, formato e SHA-256 completo. F01 corresponde ao anexo #1, até F37/#37. Todas as cópias têm 960×1280 ou 1280×960 pixels. Ampliação não recupera letras ausentes; não foi usado preenchimento generativo/OCR como evidência. Nos apontamentos abaixo, “não legível” não significa ausência do componente.

Qualidade: **alta** para forma/inscrição nitidamente observável; **média** para identificação parcial/contexto; **baixa** para foco, reflexo, oclusão ou inscrições insuficientes. A confiança de cada hipótese é independente dessa qualidade.

## Catálogo único de componentes

| ID | Componente | Evidência e limite |
|---|---|---|
| C01 | Gabinete e identidade visual | CONFIRMADO: adesivos `Fun Time`; fabricante, modelo, revisão e série NÃO IDENTIFICADOS. |
| C02 | Placa controladora principal | CONFIRMADO: PCB verde, sete relés, dissipador, conectores e etiqueta `PG01`; identidade/revisão NÃO IDENTIFICADAS. |
| C03 | Fonte multissaída | CONFIRMADO na etiqueta: `WM wangma`, `WM-ATX400-24-48`, total 320 W; saídas não medidas. |
| C04 | Joystick | Alavanca iluminada confirmada em F05; base amarela com lâminas em F06–F09 PROVÁVEL parte do mesmo joystick. |
| C05 | Botão circular iluminado | Corpo superior confirmado; função captura PROVÁVEL; contatos e circuito NÃO IDENTIFICADOS. |
| C06 | Display e PCB traseira | Display azul com mensagens em português; conector longo e encapsulamentos pretos no verso. Modelo não legível integralmente. |
| C07 | Aceitador eletrônico de moeda | CONFIRMADO por inscrição `CPU ELECTRONIC COMPARABLE COIN MECH`; não confundir “CPU” com placa principal. |
| C08 | Módulo de cédulas superior | Mecanismo de transporte PROVÁVEL validador de cédulas; etiqueta `ALPHA` de manutenção, sem fabricante/modelo demonstrado. |
| C09 | Módulo de cédulas inferior | Outro mecanismo semelhante; presença não prova que esteja operacional ou ligado. |
| C10 | Barra eletrônica no compartimento de entrega | PROVÁVEL sensor óptico de premiação; múltiplas posições S/T, CI, LED e ajuste. Quatro fios visíveis, protocolo desconhecido. |
| C11 | Conjunto carro/trilhos/elevação | Barras, roletes/polias e engrenagem visíveis; três movimentos são hipótese de arquitetura, motores não identificados individualmente. |
| C12 | Garra de três dedos | Cilindro, haste e bielas confirmados; atuador eletromagnético PROVÁVEL, sem tensão/força medidas. |
| C13 | Câmera interna | Câmera branca/preta, cabo branco, logo aparentemente Intelbras; modelo e acesso a vídeo NÃO IDENTIFICADOS. |
| C14 | Painel de serviço | Voltímetro, dois botões, chave luminosa e dois contadores; funções exatas desconhecidas. |
| C15 | Iluminação | Faixas frontais e luz na porta confirmadas; tensão/controle desconhecidos. |
| C16 | Chicotes e conectores intermediários | Espirais plásticas/metálicas, cabo helicoidal, plugues e etiquetas `CRÉDITO`/`PRÊMIO`. Cores não fornecem pinagem. |
| C17 | Banco de relés da C02 | Sete corpos contáveis; inscrições HF/JQX-115F em recortes, variante completa pendente. |
| C18 | Processadores/CI da C02 | CI quadrado com início de marcação `IAP`/`15...`; outro CI sob etiqueta `PG01`; códigos integrais não recuperados. |
| C19 | Interfaces candidatas na C02 | D-sub multipinos; header com `12V GND RXD TXD 5V`; ilhas `5V OE RC SC DAT 12V GND GNDP`; nenhuma API comprovada. |
| C20 | Alto-falante | Parcialmente visível na porta F32; interface não rastreada. |
| C21 | Placa/aviso Pix | Aviso impresso em F37; não demonstra integração automática de pagamento. |
| C22 | Painel de entrada/distribuição elétrica | Parte traseira de entrada/chaves/cabos em F23; identificação e circuito incompletos. |
| C23 | CI lógico à esquerda e acima do MCU em F20 | CONFIRMADO: marcação `74HC245D`; fabricante do exemplar não confirmado. |
| C24 | Segundo CI lógico à esquerda e abaixo do MCU em F20 | CONFIRMADO: marcação `74HC245D`; ligação aos sinais externos não rastreada. |

Os sete relés do banco C17 podem ser referidos individualmente como **C17.R1…C17.R7**, de cima para baixo na orientação original de F20. São identificadores deste levantamento, não designadores da PCB ou atribuição a motores. Em C18, **C18.MCU** designa o CI quadrado com marcação parcial IAP/15… e **C18.PG01** o CI coberto pela etiqueta. Nenhuma associação funcional entre esses dois foi comprovada.

### Complemento da inspeção ampliada dos CIs

As ampliações de F19/F20/F25/F26 e suas versões giradas em `evidencias/recortes/F20-ci-rot.png` e `F26-ci-rot.png` permitiram ler **74HC245D** em dois CIs, C23/C24. Isso completa os registros dessas quatro fotos: os dois códigos são CONFIRMADOS, mas não foi determinado qual conector cada barramento atende. Outros CIs de 16 terminais continuam sem transcrição confiável. Encapsulamentos de quatro terminais repetidos são PROVÁVEIS optoacopladores; modelo, função e barreira de isolamento da placa permanecem NÃO IDENTIFICADOS. Componentes de potência com aba/dissipador não têm código legível. [Identificação e fonte primária](02-identificacao-hardware.md).

## Registro individual de todas as fotografias

### F01 — WhatsApp Image 2026-10-21 at 19.15.00 (2).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.15.00 (2).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C01, C11, C12, C13, C15, C16.
- **Observações/inscrições:** Vista lateral/frontal, porta aberta, pelúcias e estrutura. `Fun Time` legível. Câmera no fundo, faixa azul e carro ao alto.
- **Qualidade:** Alta para conjunto; baixa para detalhes elétricos.
- **Relação e pendência:** Relacionar F35/F36/F37; nenhum modelo em etiqueta nesta vista.

### F02 — WhatsApp Image 2026-10-21 at 19.15.00 (1).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.15.00 (1).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C11, C12, C16.
- **Observações/inscrições:** Carro: trilhos paralelos, rodas/polias brancas, engrenagem escura, carcaça metálica. Garra aberta com três dedos, haste/bielas e cabo helicoidal branco. Sem código de motor legível.
- **Qualidade:** Alta para mecanismo; baixa para atuadores/sensores.
- **Relação e pendência:** Relaciona posição vista em F01; faltam etiquetas de motores, pontos de ancoragem e fins de curso.

### F03 — WhatsApp Image 2026-10-21 at 19.15.00.jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.15.00.jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C16, C13.
- **Observações/inscrições:** Plugue branco intermediário de chicote multicolorido; entrada em espiral metálica de proteção. Cabo branco da câmera ao fundo. Sem numeração legível; quantidade de cavidades ocultada. Aviso de menores parcialmente visível.
- **Qualidade:** Alta para conexão local; baixa para vias/pinagem.
- **Relação e pendência:** Caminho completo entre C02 e C11 não mostrado; não atribuir função a fio por cor.

### F04 — WhatsApp Image 2026-10-21 at 19.14.59 (20).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (20).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C13, C12, C01.
- **Observações/inscrições:** Câmera interna branca/preta fixada no fundo; cabo branco e LED pontual visíveis. Logotipo sugere Intelbras; etiqueta de modelo ausente. Parte de dedo da garra à esquerda.
- **Qualidade:** Média: reflexo e foco limitam logo.
- **Relação e pendência:** Relacionar F01/F35/F37. Aparência não comprova RTSP, ONVIF, WebRTC ou câmera USB.

### F05 — WhatsApp Image 2026-10-21 at 19.14.59 (19).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (19).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C04, C05, C06, C01.
- **Observações/inscrições:** Topo do painel: joystick translúcido iluminado, botão circular luminoso com centro aparentemente sem tampa, display e cadeado solto sobre a tela. `Fun Time`, `Tempo`, `00`, `1Play`, `Insira Moeda:00` legíveis; linha de valor parcialmente coberta. `STAM` é marca do cadeado.
- **Qualidade:** Alta para controles; média para texto coberto.
- **Relação e pendência:** F06–F09 mostram verso próximo. Não inferir defeito elétrico do aspecto do botão ou preço completo da tela obstruída.

### F06 — WhatsApp Image 2026-10-21 at 19.14.59 (18).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (18).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C06, C04, C16, C08.
- **Observações/inscrições:** Verso do display, conector branco longo; mecanismo amarelo com lâminas, atuador branco e fios. Módulo cinza à esquerda. Sem marcação nítida.
- **Qualidade:** Média para forma; baixa para inscrições.
- **Relação e pendência:** Comparar F07–F09: candidato à base C04, não microcontrolador identificado.

### F07 — WhatsApp Image 2026-10-21 at 19.14.59 (17).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (17).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C06, C04, C16.
- **Observações/inscrições:** Melhor vista do verso do display: três encapsulamentos pretos e conector longo multipinos. Início de referência parece `12864-`; restante incerto. Mecanismo amarelo abaixo.
- **Qualidade:** Média; desfoque impede código completo.
- **Relação e pendência:** Não fixar resolução/controlador pelo prefixo. C06 não prova barramento de controle do joystick.

### F08 — WhatsApp Image 2026-10-21 at 19.14.59 (16).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (16).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C06, C04, C16.
- **Observações/inscrições:** Outro ângulo do mesmo display e base amarela. Conector e passagem do chicote confirmam contexto de F07; nada novo legível.
- **Qualidade:** Média para correlação; baixa para letras.
- **Relação e pendência:** Analisada individualmente: oclusão permanece; não há terminais do botão C05 identificáveis com certeza.

### F09 — WhatsApp Image 2026-10-21 at 19.14.59 (15).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (15).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C04, C06, C07, C16.
- **Observações/inscrições:** Close do mecanismo amarelo: peças simétricas, lâminas metálicas, centro branco e fios passando à frente. Forma favorece joystick com contatos de lâmina. Aceitador de moeda parcial no canto.
- **Qualidade:** Média para hipótese; baixa para ligações ocultas.
- **Relação e pendência:** Recorte F09-mecanismo-amarelo.png. É preciso ligar visualmente eixo ao topo e documentar cada contato; não há comum comprovado.

### F10 — WhatsApp Image 2026-10-21 at 19.14.59 (14).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (14).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C08, C07, C16.
- **Observações/inscrições:** Módulo cinza de transporte e rótulo `ATENÇÃO`; frase de instalação parcialmente legível. Chicote superior e mecanismo de moeda lateral.
- **Qualidade:** Média; etiqueta inclinada.
- **Relação e pendência:** Mesmo módulo superior em F17/F32; não usar instrução parcialmente legível como autorização para montar invertido.

### F11 — WhatsApp Image 2026-10-21 at 19.14.59 (13).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (13).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C08, C16.
- **Observações/inscrições:** Aceitador lateral preto, tampa eletrônica, fita plana curta, conectores e mecanismo de retenção/comparação. `REPLACE COIN` na peça superior.
- **Qualidade:** Alta para forma; média para letras.
- **Relação e pendência:** F12–F16 completam etiqueta. Ajustes de fábrica/manutenção não foram manipulados.

### F12 — WhatsApp Image 2026-10-21 at 19.14.59 (12).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (12).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C08, C16.
- **Observações/inscrições:** Etiqueta `CPU`, `ELECTRONIC COMPARABLE COIN MECH`; QR e código de barras sem leitura confiável. Fios e placa lateral.
- **Qualidade:** Alta para classe do módulo; baixa para modelo.
- **Relação e pendência:** “CPU” descreve aceitador; não é identificação do controlador C02.

### F13 — WhatsApp Image 2026-10-21 at 19.14.59 (11).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (11).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C08, C16.
- **Observações/inscrições:** Outra vista mais frontal da mesma etiqueta e suporte de moeda; `REPLACE COIN` legível. QR, fabricante e número exato não recuperados.
- **Qualidade:** Alta para inscrições maiores; baixa para QR.
- **Relação e pendência:** Confrontada F12/F14/F15; nenhum protocolo de crédito demonstrado.

### F14 — WhatsApp Image 2026-10-21 at 19.14.59 (10).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (10).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C08, C16.
- **Observações/inscrições:** Repetição próxima com foco distinto: etiqueta de classe do aceitador, chicote com conector branco e alavanca/solenoide.
- **Qualidade:** Média; texto pequeno desfocado.
- **Relação e pendência:** Confirma montagem compartilhada; não constitui segunda placa principal.

### F15 — WhatsApp Image 2026-10-21 at 19.14.59 (9).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (9).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C16.
- **Observações/inscrições:** Close de etiqueta `CPU` e QR; foco insuficiente para ler caracteres menores, apesar de maior enquadramento.
- **Qualidade:** Baixa para identificação fina.
- **Relação e pendência:** Solicitar macro frontal do código/modelo e legenda do aceitador, sem presumir padrão pulse/ccTalk/MDB.

### F16 — WhatsApp Image 2026-10-21 at 19.14.59 (8).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (8).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C08, C16.
- **Observações/inscrições:** Lateral do aceitador: placa estreita, trimpot ajustável, conector com quatro condutores visíveis e bobina/mecanismo amarelo. Fita plana superior.
- **Qualidade:** Alta para componentes; baixa para legenda elétrica.
- **Relação e pendência:** Quatro fios não determinam alimentação ou protocolo. Não alterar trimpot.

### F17 — WhatsApp Image 2026-10-21 at 19.14.59 (7).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (7).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C08, C09, C07, C16.
- **Observações/inscrições:** Visão conjunta: dois módulos cinza empilhados, aceitador à direita. `ALPHA` nas etiquetas com grade de manutenção/data, não placa de identificação técnica.
- **Qualidade:** Alta para quantidade/disposição.
- **Relação e pendência:** F32/F33 correlacionam. Só há ligação parcial visível no inferior; funcionalidade não provada.

### F18 — WhatsApp Image 2026-10-21 at 19.14.59 (6).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (6).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C02, C03, C17, C18, C19, C16.
- **Observações/inscrições:** Vista oblíqua da placa principal. Sete relés, dissipador, capacitores, vários CI, etiqueta `PG01`. Fonte metálica à direita.
- **Qualidade:** Alta para arquitetura; média para códigos.
- **Relação e pendência:** F19/F20/F25/F26 melhoram inscrições. LEDs acesos são estado capturado, não ensaio de saúde.

### F19 — WhatsApp Image 2026-10-21 at 19.14.59 (5).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (5).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C02, C17, C18, C19, C16.
- **Observações/inscrições:** Vista frontal ampla: `PG01`, `SET`, `12V GND RXD TXD 5V` no header lateral; ilhas à esquerda `5V OE RC SC DAT 12V GND GNDP`. LEDs de alimentação e chicote `CRÉDITO`.
- **Qualidade:** Alta para inscrições maiores e disposição.
- **Relação e pendência:** Porta lateral candidata serial, sem níveis/protocolo. Funções de conectores inferiores parcialmente ocultas.

### F20 — WhatsApp Image 2026-10-21 at 19.14.59 (4).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (4).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C02, C17, C18, C19, C16.
- **Observações/inscrições:** Vista frontal mais próxima. D-sub superior, sete relés, três componentes de potência verticais abaixo do dissipador; LEDs marcados `48V`, `12V`, `24V`, `5V`; headers e áreas não populadas.
- **Qualidade:** Alta para layout; média para códigos.
- **Relação e pendência:** C18 início `IAP`/`15...` incompleto. Sem assinatura inequívoca de fabricante/revisão PCB. Ampliação F20-placa.png.

### F21 — WhatsApp Image 2026-10-21 at 19.14.59 (3).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (3).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C10, C16.
- **Observações/inscrições:** Close desfocado da barra no compartimento de entrega: CI, capacitores, ajuste, conector e quatro fios. Sem modelo legível.
- **Qualidade:** Baixa para texto; média para objeto.
- **Relação e pendência:** F22 situa e F31 melhora a inspeção. Não descartar foto por estar desfocada.

### F22 — WhatsApp Image 2026-10-21 at 19.14.59 (2).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (2).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C10, C16, C01.
- **Observações/inscrições:** Barra horizontal instalada na parede do compartimento inferior de entrega; chicote desce à direita preso por abraçadeira.
- **Qualidade:** Alta para localização; média para placa.
- **Relação e pendência:** Localização favorece detector de passagem de prêmio; não demonstra confirmação confiável de entrega.

### F23 — WhatsApp Image 2026-10-21 at 19.14.59 (1).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59 (1).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C22, C16, C01.
- **Observações/inscrições:** Vista interna ampla: chicote em espiral, fixações, cabos avulsos e painel traseiro de entrada/chaves parcialmente visível. Cabos azuis atravessam, sem conectores de rede identificáveis.
- **Qualidade:** Alta para trajetos locais; baixa para função.
- **Relação e pendência:** Não chamar cabos azuis de Ethernet nem definir aterramento pela cor. Falta frente do painel C22.

### F24 — WhatsApp Image 2026-10-21 at 19.14.59.jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.59.jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C02, C03, C16, C19.
- **Observações/inscrições:** Visão compartimento principal: PCB junto à fonte, dissipador, cabos e etiquetas `CRÉDITO` e `PRÊMIO`. Há conectores intermediários junto à borda superior.
- **Qualidade:** Alta para posição/etiquetas; média para rastreio.
- **Relação e pendência:** Etiqueta identifica intenção do chicote, não pulso/nível/polaridade. Pontas não estão rastreadas integralmente.

### F25 — WhatsApp Image 2026-10-21 at 19.14.58 (2).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.58 (2).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C02, C17, C18, C19, C16.
- **Observações/inscrições:** Outra frontal da placa: D-sub, conectores de energia e inferiores, `PG01`, `SET`, série de LEDs e chicote `CRÉDITO`.
- **Qualidade:** Alta; reflexo em partes dos CI.
- **Relação e pendência:** F26 mostra LED diferente; não inferir código de erro ou versão de firmware pelo acendimento.

### F26 — WhatsApp Image 2026-10-21 at 19.14.58 (1).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.58 (1).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C02, C17, C18, C19, C16.
- **Observações/inscrições:** Frontal correlata: etiqueta `PG01`, sete relés, header serial candidato, LEDs de alimentação e LED próximo ao centro.
- **Qualidade:** Alta para estrutura; média para caracteres pequenos.
- **Relação e pendência:** Comparação mantém mesma placa fotografada. Quantidade de LEDs acesos varia com instante/exposição.

### F27 — WhatsApp Image 2026-10-21 at 19.14.58.jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.58.jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C03, C16, C22.
- **Observações/inscrições:** Fonte em carcaça metálica com cabo de entrada no alto; `WM wangma`, modelo e quadro de tensões parcialmente legíveis, reflexo inferior.
- **Qualidade:** Média para etiqueta; alta para forma.
- **Relação e pendência:** F28 permite leitura superior. Modelo contém ATX, sem provar compatibilidade de pinagem com PC.

### F28 — WhatsApp Image 2026-10-21 at 19.14.53 (3).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.53 (3).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C03, C16.
- **Observações/inscrições:** Etiqueta melhor: `WM-ATX400-24-48`, `AC INPUT:100-240V 4A 50/60Hz`, `+5V:0.5-12A MAX`, `+12V:6A MAX`, `+24V:6A MAX`, `+48V:6A MAX`, `TOTAL MAX POWER:320W`. Quadro impresso associa cores às saídas da própria fonte. URL `http://wmsps.com` em ampliação.
- **Qualidade:** Alta para etiqueta; média para campos menores.
- **Relação e pendência:** São dados nominais, não medição. Limites de cada saída não podem ser somados como potência simultânea; tabela de cor não se transfere aos chicotes da máquina.

### F29 — WhatsApp Image 2026-10-21 at 19.14.53 (2).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.53 (2).jpeg>) · 1280×960 · abertura e inspeção visual concluídas.

- **Componentes:** C16, C10, C01.
- **Observações/inscrições:** Trajeto no compartimento inferior: chicote em espiral e cabo preto cruzando; fios da barra seguem parede. Nenhuma legenda nova.
- **Qualidade:** Alta para fixações; baixa para origem/destino completo.
- **Relação e pendência:** Relacionar F22/F23/F30; partes somem fora do enquadramento.

### F30 — WhatsApp Image 2026-10-21 at 19.14.53 (1).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.53 (1).jpeg>) · 1280×960 · abertura e inspeção visual concluídas.

- **Componentes:** C16, C10, C01.
- **Observações/inscrições:** Outro trecho dos quatro fios na parede, abraçadeira e fita/plástico no gabinete. Barra parcial no topo.
- **Qualidade:** Alta para caminho parcial; baixa para terminação.
- **Relação e pendência:** Complementa F29, sem fechar percurso até C02.

### F31 — WhatsApp Image 2026-10-21 at 19.14.53.jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.53.jpeg>) · 1280×960 · abertura e inspeção visual concluídas.

- **Componentes:** C10, C16.
- **Observações/inscrições:** Melhor vista da barra: fileira de pares/posições marcadas `S` e `T`, CI `U1` etc., LED, capacitores e ajuste. Conector de quatro fios visíveis. Código do produto e CI não legíveis com certeza.
- **Qualidade:** Alta para layout; média para inscrições.
- **Relação e pendência:** Compatível com sensor óptico multifeixe; não atribuir função por pino. Recorte F31-barra.png rotacionado.

### F32 — WhatsApp Image 2026-10-21 at 19.14.52 (3).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.52 (3).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C08, C09, C15, C16, C20.
- **Observações/inscrições:** Porta iluminada aberta: dois módulos de transporte empilhados, aceitador à direita, cabos e alto-falante parcial inferior esquerdo.
- **Qualidade:** Alta para conjunto; baixa por luz azul em detalhes.
- **Relação e pendência:** Comparar F17/F33. Não há evidência de ligação de todos os módulos até C02 nesta foto.

### F33 — WhatsApp Image 2026-10-21 at 19.14.52 (2).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.52 (2).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C07, C08, C09, C16.
- **Observações/inscrições:** Vista próxima da mesma porta, iluminação azul; posição do aceitador, módulos e conector pendente.
- **Qualidade:** Média para fios; baixa para letras.
- **Relação e pendência:** Foto distinta inspecionada; conector pendente não comprova defeito nem interface livre para integração.

### F34 — WhatsApp Image 2026-10-21 at 19.14.52 (1).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.52 (1).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C14, C01, C16.
- **Observações/inscrições:** Painel serviço: voltímetro `V` contínua 0–50, `85C1`, dois botões, chave luminosa, dois contadores. Rascunho `99`, etiqueta `0099`; dígitos iniciais `00406...` e `13135...` com último dígito incerto. Ponteiro junto ao zero no instante.
- **Qualidade:** Alta para painel; média para números menores.
- **Relação e pendência:** Não prova tensão zero no circuito nem função dos botões/contadores; não assumir parada de emergência.

### F35 — WhatsApp Image 2026-10-21 at 19.14.52.jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.52.jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C01, C04, C05, C11, C12, C13, C15.
- **Observações/inscrições:** Frontal ampla com porta inferior aberta e manipulação local registrada na foto. `Fun Time`; câmera e conjunto mecânico.
- **Qualidade:** Alta para disposição; baixa para eletrônica.
- **Relação e pendência:** Relacionar F01/F36; fotografia não valida funcionamento ou teste de segurança.

### F36 — WhatsApp Image 2026-10-21 at 19.14.51 (1).jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.51 (1).jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C01, C04, C05, C13, C15.
- **Observações/inscrições:** Outra frontal: pessoa junto ao painel e portas. Placa impressa lateral `R$ 2,00` visível.
- **Qualidade:** Alta para identidade/disposição; média para preço.
- **Relação e pendência:** Preço impresso é evidência histórica da foto, não configuração ativa comprovada. Não executar ações retratadas.

### F37 — WhatsApp Image 2026-10-21 at 19.14.51.jpeg

[Fotografia original copiada](<../evidencias/fotos/WhatsApp Image 2026-10-21 at 19.14.51.jpeg>) · 960×1280 · abertura e inspeção visual concluídas.

- **Componentes:** C01, C13, C21, C12, C15.
- **Observações/inscrições:** Topo iluminado com adesivo `Fun Time`, câmera abaixo, garra parcial e aviso Pix impresso à direita.
- **Qualidade:** Alta para identidade; baixa para interfaces câmera/Pix.
- **Relação e pendência:** Pix impresso não comprova webhook, controlador de crédito ou processamento automático.

## Lacunas fotográficas específicas

1. **C04/C05:** fotografia contínua unindo topo, eixo, base amarela, terminais, contatos e plugue; macro de legendas; verso integral do botão separando luz de contato. O conjunto amarelo já aparece: falta confirmar sua correspondência e circuito, não apenas repetir o topo.
2. **C02/C18/C19:** macro perpendicular sem reflexo de cada CI e conector, quatro cantos, bordas e serigrafia integral da PCB; verso somente se acesso profissional apropriado permitir. Etiqueta `PG01` não deve ser removida nesta fase. D-sub deve ser fotografado na face de contatos para contagem e gênero; número de vias dos headers deve ser registrado pelo corpo, não pela quantidade de fios aparentes.
3. **C03/C22:** etiqueta completa, conectores vistos de frente e distribuição de entrada, proteção/fusível e conexão de proteção ao gabinete. Não abrir carcaça da fonte.
4. **C11/C12:** etiquetas dos motores e atuador, cabos com pontos de origem/destino, fins de curso e mecanismo de elevação/cordão. Fotos atuais não identificam quais sensores limitam cada eixo.
5. **C10:** etiqueta/serigrafia de modelo, marcações de CI, frente óptica, possível contraparte e conector até o chicote `PRÊMIO`.
6. **C07/C08/C09/C13/C14:** placas de identificação e conectores/legendas, inclusive painel traseiro do serviço; câmera precisa etiqueta/modelo e portas, sem expor senha ou QR de vinculação de conta.

As novas fotos devem ser produzidas dentro da inspeção desenergizada por profissional qualificado descrita em [08](08-plano-validacao.md), preservando posição e configuração dos componentes. Nenhuma pinagem definitiva foi obtida nesta etapa.
