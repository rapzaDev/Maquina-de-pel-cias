# 10 — Resumo executivo da investigação

Data: 21/10/2026. Foram inspecionadas **37/37 fotografias**, preservadas no projeto com manifesto e hashes. As dez etapas documentais foram concluídas até o limite das evidências disponíveis. **Nenhuma integração, leitura de firmware, medição elétrica ou operação de hardware foi executada.**

**A alternativa mais promissora é manter a placa original e reproduzir seus controles com interface eletricamente compatível e reversível.** A base do joystick provavelmente usa contatos de lâmina. Isso justifica investigar a solução A; ainda não demonstra que um relé, optoacoplador ou outro circuito específico funcionará. Não existe pinagem de adaptação aprovada.

## Descobertas e pendências

As classificações são: **CONFIRMADO** para a evidência especificada, **PROVÁVEL** para inferência sustentada, **NÃO IDENTIFICADO** para informação insuficiente. Etiqueta confirmada não significa tensão medida ou função testada.

| DESCOBERTA | EVIDÊNCIA | CONFIANÇA | PENDÊNCIA |
|---|---|---|---|
| Máquina de captura de pelúcias com arte Fun Time | F01/F05/F35–F37 | CONFIRMADO | Fabricante, modelo, revisão e série NÃO IDENTIFICADOS |
| Controladora original com sete relés e etiqueta PG01 | F18–F20/F24–F26 | CONFIRMADO | Fabricante/revisão da PCB, firmware e significado de PG01 NÃO IDENTIFICADOS |
| Dois CIs com marcação 74HC245D | Recortes de F20 corroborados por F26 | CONFIRMADO | Fabricante e ligações no barramento da placa pendentes; não revelam API externa |
| Fonte Wangma WM-ATX400-24-48; etiqueta 5/12/24/48 V e 320 W totais | F27/F28 | CONFIRMADO | Medir saídas, referências, carga/reserva e proteção; manual exato não localizado |
| Base amarela corresponde ao joystick e utiliza contatos de lâmina | F05–F09, sobretudo recorte F09 | PROVÁVEL | Unir eixo/base em vista contínua e mapear contatos, corrente e circuito |
| Tipo de sinal, pinagem e comum das direções/captura | Nenhuma medição ou esquema disponível | NÃO IDENTIFICADO | Rastreio desenergizado e posterior caracterização profissional |
| Porta candidata serial | Inscrições 12V/GND/RXD/TXD/5V em F19/F20 | PROVÁVEL | Níveis, referência, protocolo e finalidade. Inscrições em si são CONFIRMADAS |
| Controle remoto pela interface nativa do firmware | Não há manual/protocolo correspondente | NÃO IDENTIFICADO | Documentação vinculada à revisão ou investigação futura de artefatos compatíveis |
| Aceitador eletrônico de moeda | Etiqueta CPU ELECTRONIC COMPARABLE COIN MECH em F12–F16 | CONFIRMADO | Modelo, sinal de crédito, habilitação e confirmação de início |
| Dois módulos são validadores de cédulas | F10/F17/F32/F33, formato de transporte e etiquetas ALPHA | PROVÁVEL | Identificação e estado funcional de cada módulo; ALPHA não prova fabricante |
| Barra inferior detecta passagem de prêmio | Localização F22 e PCB F31; chicote PRÊMIO F24 | PROVÁVEL | Vínculo elétrico, função, protocolo e confiabilidade de detecção |
| Câmera interna existe | F04/F35–F37 | CONFIRMADO | Modelo, acesso local, codec e atraso; marca aparente não basta |
| Modelos dos motores, limites de curso e proteção funcional | F02 mostra mecânica, sem etiquetas/ensaios suficientes | NÃO IDENTIFICADO | Inspeção de atuadores/sensores e validação da resposta segura |
| Preservar C02 e reproduzir comandos é caminho viável | Base mecânica provável e controladora com potência própria | PROVÁVEL | Compatibilidade elétrica e comportamento sob falhas precisam ser demonstrados |
| REA não foi usado e não está disponível na sessão/caminhos usuais verificados | Diagnóstico de leitura e análise dos artefatos em [05](05-avaliacao-rea.md) | CONFIRMADO | Reconsiderar apenas se houver arquivo/captura compatível e pergunta concreta |

## Respostas às decisões do projeto

**1. Qual máquina possuímos?** Um gabinete de garra de três dedos para pelúcias com identidade visual **Fun Time**. Fabricante, modelo exato e versão são **NÃO IDENTIFICADO**. Adesivo comercial não equivale à identificação técnica.

**2. Qual é a controladora?** A PCB original verde das fotos F18–F26, com sete relés, potência e etiqueta **PG01**. O adesivo está **CONFIRMADO**; não é suficiente para chamar a placa de “modelo PG01” nem identificar fabricante/firmware. Há pistas de família HF/JQX-115F nos relés e IAP/15… num CI, sem modelo completo deste último.

**3. Como recebe comandos do joystick?** **PROVÁVEL** por contatos eletromecânicos, possivelmente de lâmina, vistos junto ao verso do painel. Não confirmamos se as entradas são independentes, uma matriz, contatos multipolares ou chaveamento de outra natureza. Não há prova de tensão, polaridade ou comum.

**4. Podemos manter a placa original?** É a hipótese prioritária e **PROVÁVEL**, sujeita a ensaios. A PCB já contém lógica e potência para a mecânica instalada. Preservá-la evita assumir imediatamente o controle dos motores/garra, mas não dispensa avaliar proteções e parada.

**5. Qual estratégia é mais promissora?** **Solução A:** interface reversível dos controles após levantamento elétrico. Solução B só ganha prioridade se a interface nativa puder ser documentada; C é alternativa de maior intervenção se A/B falharem. A tecnologia de comutação continua **NÃO IDENTIFICADO**. Não há recomendação automática de relés.

**6. Precisamos de Raspberry Pi, ESP32 ou outro?** Raspberry Pi **não é requisito demonstrado**. Um MCU como ESP32 é candidato para autorização local, limites e comandos; outro MCU adequado pode cumprir o papel. Computador Linux só será necessário se vídeo, câmera ou serviços locais o exigirem. Notebook/mini-PC existente pode atender a PoC. Escolha de placa depende da interface e do caminho de vídeo.

**7. O que os componentes adicionais fariam?** Controlador local verifica sessão/exclusividade, comandos recentes e intertravamentos; interface reproduz o sinal medido; chicote permite reversão; alimentação/proteção mantém separação adequada; permissão/parada local contém falhas; câmera/publicador entrega vídeo de baixa latência. Telemetria/crédito só serão automatizados onde os sinais e a semântica forem validados. Ver [09](09-componentes-custos.md).

**8. O REA foi necessário?** Não. O projeto só forneceu fotos, sem firmware, binários, aplicativos ou capturas. A documentação oficial não apresenta extração de esquema/pinagem dessas fotos. Instalar agora não resolveria o bloqueio principal; nada foi instalado ou configurado. [Avaliação e fontes oficiais](05-avaliacao-rea.md).

**9. O que não confirmamos?** Identidade exata da PCB, circuito dos controles/crédito, protocolo RXD/TXD, sequência/telemetria do firmware, motores/garra, sensores de posição, parada real em falha, ligação da barra de prêmio e adequação da câmera. Soltar uma entrada remota não prova que um ciclo automático pare.

**10. Quais evidências faltam?** Plaqueta do gabinete; macros da PCB/CI/conectores; vista que relacione joystick, base amarela, terminais e chicote até a controladora; verso do botão separado da iluminação; etiquetas de aceitadores/câmera/motores; limites de curso e trajeto da barra de prêmio; documentação do fornecedor. Depois da inspeção, medir sinais e comportamento conforme [08](08-plano-validacao.md), exclusivamente por profissional qualificado. A lista fotográfica específica está em [01](01-inventario-fotografico.md).

**11. Qual é a primeira validação física?** Inspeção profissional com a máquina desenergizada, energias residuais/mecânicas tratadas e ausência de tensão comprovada. O objetivo é identificar C04/C05 e rastrear seu circuito, preservando a instalação. Ainda não é teste de comando nem medição improvisada com a máquina ligada.

**12. O que não comprar ainda?** Módulos de relés, PhotoMOS/optoacopladores, USB–serial/RS-232/RS-485, drivers de motor, controladora “PG01”/universal, fonte ATX de PC, conectores escolhidos por aparência, nova câmera ou kit Raspberry Pi. Primeiro fechar a especificação; os itens de [09](09-componentes-custos.md) são funções condicionais, não pedido de compra. Não há orçamento brasileiro fechado ou preços inventados.

**13. Qual é o menor caminho até controlar pelo navegador?** Identificar e caracterizar entradas → ensaiar interface independente e falhas em bancada → validar na máquina sob supervisão e com parada local → página mínima de teste com sessão única, quatro direções, neutro, captura e vídeo medido → internet em acesso restrito. Crédito inicialmente pelo meio original validado, sem pagamento real. Fila comercial, aplicativo Flutter e cobrança vêm depois da PoC; não foram implementados.

## Entregáveis e limite da conclusão

[01 Inventário](01-inventario-fotografico.md) · [02 Hardware](02-identificacao-hardware.md) · [03 Arquitetura eletrônica](03-arquitetura-eletronica.md) · [04 Controles](04-investigacao-controles.md) · [05 REA](05-avaliacao-rea.md) · [06 Alternativas](06-alternativas-integracao.md) · [07 Controle remoto](07-arquitetura-controle-remoto.md) · [08 Validação](08-plano-validacao.md) · [09 Materiais/custos](09-componentes-custos.md).

O funcionamento foi reconstruído no nível de blocos, com conexões locais observadas separadas das hipóteses. Foram definidos caminho de integração, materiais condicionais, lacunas e critérios de prova. **Não foi demonstrado funcionamento remoto nem fechada uma interface elétrica.** A consulta pública da concorrente não revelou sua arquitetura; ela não foi presumida nesta proposta.

## Única próxima ação prioritária

**Realizar uma inspeção profissional desenergizada do joystick C04, botão C05 e seus chicotes até a controladora, entregando fotografias nítidas e um mapa verificável de contatos/conexões.** Essa única ação resolve a maior incerteza: se conseguimos reproduzir os comandos mantendo C02 e qual caracterização elétrica será necessária. Ela desbloqueia a seleção da interface, os componentes e a PoC sem compras antecipadas ou alterações por tentativa.
