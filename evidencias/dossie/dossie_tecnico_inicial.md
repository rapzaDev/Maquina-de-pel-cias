# Investigação técnica inicial — Máquina Fun Time (fotografias)

**Base de evidências:** `Arquivo.zip` do proprietário, contendo 37 JPEGs distintos (960×1280 ou 1280×960). Este relatório analisa evidências visuais e pesquisa documental pública; NÃO é esquema elétrico confirmado nem autorização para conectar componentes.

## Achados com evidências diretas

| Item | Evidência no ZIP | Constatação / grau de certeza | Próxima pergunta |
|---|---|---|---|
| Identidade externa | `WhatsApp Image 2026-10-21 at 19.14.51.jpeg` e `19.14.59 (19).jpeg` | **Confirmado**: marca/arte 'Fun Time' no gabinete e no painel. **Desconhecido**: empresa fabricante e número de modelo; marca gráfica não comprova fabricante. | Há uma placa de identificação/nota de compra, número de série ou contato de quem forneceu? |
| Placa central | `WhatsApp Image 2026-10-21 at 19.14.59 (4).jpeg` | **Confirmado**: placa de controle verde com sete relés visíveis, botão `SET`, conectores inferiores e um conector D-sub multipinos. Sem modelo/PCB revision legível e confirmado. | Identificar serigrafia do verso da placa e códigos completos dos ICs. |
| Comunicação candidata | `WhatsApp Image 2026-10-21 at 19.14.59 (4).jpeg` | **Confirmado**: impressão `12V`, `GND`, `RXD`, `TXD`, `5V` junto a um conector. **Hipótese**: canal de dados; protocolo, finalidade e nível de sinal desconhecidos. Nunca associar `RXD/TXD` automaticamente a UART TTL, RS232 ou comando de jogo. | Manual ou documentação da interface, ou posterior caracterização por profissional. |
| Identificação 'PG01' | `WhatsApp Image 2026-10-21 at 19.14.59 (4).jpeg` | **Confirmado**: etiqueta PG01 aplicada sobre encapsulamento de CI. **Não confirmado** que PG01 seja o modelo da PCB; pode ser identificação de programa/componente. | Identificar gravações da própria PCB e marcação do chip por baixo da etiqueta, se legal e possível sem dano. |
| Créditos e prêmios | `WhatsApp Image 2026-10-21 at 19.14.59.jpeg` | **Confirmado**: chicotes próximos à controladora identificados `CRÉDITO` e `PRÊMIO`. **Não confirmada** a função elétrica e o sentido dos sinais. | Rastrear as duas etiquetas ao conjunto de origem/destino, sem desconectar nada nesta fase. |
| Aceitador de moedas | `WhatsApp Image 2026-10-21 at 19.14.59 (9).jpeg`, `(10).jpeg`, `(11).jpeg` | **Confirmado**: módulo identificado `CPU Electronic Comparable Coin Mech`; é um periférico moedeiro, não processador central. | Modelo legível e esquema de saída de pulsos do próprio módulo. |
| Fonte | `WhatsApp Image 2026-10-21 at 19.14.53 (3).jpeg` | **Confirmado**: fonte `Wangma WM-ATX400-24-48`, etiqueta com saídas 5V/12V/24V/48V e limite total declarado. São saídas da fonte, não tensões comprovadas nos conectores de controle. | Garantir alimentação independente/adequada do futuro gateway; validação elétrica profissional. |
| Câmera | `WhatsApp Image 2026-10-21 at 19.14.59 (20).jpeg` | **Confirmado visualmente**: uma câmera aparentemente independente já instalada sobre o recinto da garra. Marca/modelo não legíveis; latência, RTSP e acesso remoto não confirmados. | Identificar modelo e avaliar vídeo de baixa latência; evitar comprar câmera até avaliar a existente. |
| Painel do jogador | `WhatsApp Image 2026-10-21 at 19.14.59 (19).jpeg` | **Confirmado**: joystick, botão iluminado e visor. **Ausente nas fotos**: visão inequivocamente nítida dos contatos/terminais do joystick por baixo. | Uma foto clara da parte inferior do joystick e do botão, feita de forma segura com o equipamento desligado. |
| Placa estreita | `WhatsApp Image 2026-10-21 at 19.14.53.jpeg` | **Confirmado**: PCB estreita separada com componentes e chicote. Função exata não estabelecida. | Localização funcional, visão da frente do painel correspondente e marcações do verso. |

## Modelo funcional mínimo para a primeira prova de conceito

**Web/App → backend (autenticação, exclusividade, temporizador, fila) → gateway local → interface isolada/documentada → entradas autorizadas na controladora original.** Fluxo de vídeo separado: **câmera → servidor/gateway de mídia → web/app**. Fluxo de resultados separado: **sinal de crédito/sensor de premiação somente após caracterização → backend com auditoria**.

**Hipóteses prioritárias:**

1. **Entrada de controles convencionais** (joystick e botão): pode ser o caminho mais simples se contatos/níveis forem validados. Avaliar interface isolada e reversível; não presumir que conectores ou cores já indiquem pinagem.
2. **RXD/TXD**: pesquisar documentação de fabricante primeiro. A existência de RXD/TXD não permite concluir que a placa aceita comandos de movimento; pode ser diagnóstico, configuração ou comunicação interna.
3. **CRÉDITO / PRÊMIO**: as etiquetas são ótimas pistas para o sistema comercial, mas não garantem entrada de crédito e saída confiável de premiação sem traçar os circuitos.
4. **Câmera existente**: investigar se é reaproveitável em baixa latência antes de comprar streaming adicional.

## Informações ainda não disponíveis mesmo com as 37 fotos

- Modelo exato do gabinete e origem comprovada da controladora;
- Esquema, pinagens, tipo elétrico e protocolo da porta RXD/TXD;
- Contatos/terminais inequívocos do joystick e do botão;
- Caminho completo de `CRÉDITO` e `PRÊMIO` até periférico, sensores e controlador;
- Modelo e características de streaming da câmera já instalada;
- Verificações elétricas, segurança e comportamento em falhas.

## Pesquisa pública

- Consultas abertas realizadas para `PG01 RXD TXD claw PCB`, `PG01 娃娃机 主板`, e `Fun Time PG01 claw`; **não identificaram correspondência inequívoca da placa**.
- Um índice de registros de importação contém descrição de **máquinas modelo FUN TIME**, mas não prova que seja o mesmo fabricante/equipamento do proprietário: https://kingcrabweb.com/ncm/95043000
- Exemplos de controladoras diversas de máquinas de pelúcia têm entradas separadas para joystick, moedas e garra, mas pinagens de outras máquinas NÃO devem ser usadas neste equipamento: https://www.betson.com/wp-content/uploads/wpallimport/files/service-manuals/grab-n-win-42-merchandiser-crane-ice-service-manual.pdf

## Próxima ação única recomendada

**Pedir ao Codex uma investigação focalizada usando EXATAMENTE as fotografias de referência listadas acima.** Produzir mapa de evidência por arquivo, testar hipóteses contra documentação verificável, identificar as lacunas de imagem e propor uma prova de conceito SEM energizar, tocar em circuitos desconhecidos, instalar programa ou comprar hardware. Se, ao fim, os terminais reais do joystick forem a única lacuna decisiva, solicitar fotografia nítida da parte inferior do joystick e botão, realizada com equipamento desenergizado e medidas adequadas de segurança.
