# 08 — Plano progressivo de validação física

Data: 21/10/2026. **Este documento descreve trabalho futuro. Nenhum ensaio físico, medição elétrica ou acionamento foi realizado nesta investigação.**

## 1. Regras e registros para todas as fases

O proprietário autoriza a investigação, mas as intervenções elétricas exigem planejamento e profissional com qualificação, competência e autorização compatíveis. Retirar o plugue ou apagar LEDs, por si só, não comprova ausência de tensão; capacitores e outras fontes precisam ser considerados. O procedimento de desenergização, impedimento de reenergização e verificação deve ser elaborado/executado pelo responsável técnico, incluindo o tratamento das energias mecânicas.

A NR-10 publicada pelo MTE trata da segurança em eletricidade e dos requisitos para trabalhadores e testes. A página oficial distingue o texto vigente até 31/05/2027 e a nova redação da Portaria 737/2026, cuja vigência começa em 01/06/2027. O responsável deve confirmar a redação aplicável na data dos ensaios. Este plano não substitui procedimento profissional nem demonstra conformidade normativa da máquina. [MTE — NR-10 e versões oficiais](https://www.gov.br/trabalho-e-emprego/pt-br/acesso-a-informacao/participacao-social/conselhos-e-orgaos-colegiados/comissao-tripartite-partitaria-permanente/normas-regulamentadora/normas-regulamentadoras-vigentes/norma-regulamentadora-no-10-nr-10).

Para cada fase, registrar responsável, data, unidade da máquina, revisão de placa, instrumentos e respectivas limitações, fotografias antes/depois, hipóteses, resultado bruto, critério aplicado, anomalias e decisão de avanço. Registros não obtidos serão marcados `NÃO MEDIDO`, sem preencher com estimativas. Preservar as fotos originais e ligar novas evidências aos IDs F01–F37 do [inventário](01-inventario-fotografico.md).

São regras de passagem: aprovação explícita de cada fase; ausência de pessoa no volume de movimentação durante ensaios; exclusão de clientes e acesso público; operador local apto a interromper o ensaio; nenhuma ponte ou ligação determinada por cor de fio; nenhum teste de continuidade em circuito energizado; nenhum analisador lógico conectado a nível ou referência desconhecidos.

Os ensaios quantitativos abaixo são **metas iniciais propostas**, não certificação e nem prova estatística de confiabilidade. O responsável pode exigir amostras maiores ou limites mais restritivos conforme risco. Critérios de segurança física dependem da caracterização do mecanismo, não dos limites de latência do software.

## 2. Fase A — Fotografias e documentação

**Objetivo:** fechar o mapa do que foi visto e do que precisa ser inspecionado, sem tocar no equipamento.

**Pré-requisitos:** acesso às fotografias originais, identificação estável dos arquivos e autorização já fornecida para leitura/pesquisa.

**Evidências necessárias:** inventário de todas as imagens; referências cruzadas; identificação do painel, fonte, placa, pagamentos, garra, câmera e barra de saída; resultados das buscas oficiais e lacunas. `PG01` deve permanecer etiqueta observada, sem promover a modelo confirmado.

**Ferramentas apropriadas:** visualizador de imagens, recortes locais derivados, leitura de etiquetas e documentação pública. Não executar firmware desconhecido, instalar ferramentas ou modificar equipamento.

**Riscos:** transformar aparência em pinagem; usar manual de placa semelhante; associar tensão da fonte diretamente ao joystick; tomar a barra de saída como protocolo conhecido.

**Critério de aprovação:** todas as fotos abertas e individualmente registradas; cada hipótese tem evidência/limitação; lista de fotos adicionais inclui vistas nítidas da provável base de joystick de F06–F09 e do botão, conectores nas duas extremidades e identificação de sensores/câmera; nenhum pino funcional inventado.

**Impedimentos:** foto original inacessível sem declaração; etiqueta relevante apresentada como lida quando ilegível; documentação de outro modelo tratada como prova.

**Próximo passo:** inspeção dirigida e desenergizada na Fase B. A etapa documental pode terminar com identidade exata ainda desconhecida, desde que a lacuna esteja explícita.

## 3. Fase B — Inspeção física desenergizada

**Objetivo:** documentar a parte inferior do joystick/botão e rastrear os chicotes até seus conectores sem alterar a lógica original.

**Pré-requisitos:** responsável técnico; procedimento de isolamento e impedimento de reenergização; verificação de ausência de tensão por método/instrumento adequado; tratamento de energia armazenada e partes móveis. A escolha e a execução desses procedimentos cabem ao profissional.

**Evidências necessárias:** fotos nítidas do corpo inferior do joystick, contatos/microinterruptores ou placa, botão e iluminação separados quando existirem; inscrição da PCB e versão; conectores vistos frontalmente com orientação inequívoca e contagem de vias; percurso físico de cada chicote; etiquetas da câmera e sensor; motores, fim de curso e aterramento. Registrar o estado dos conectores antes de qualquer desconexão que o profissional julgar necessária.

**Ferramentas apropriadas:** câmera com foco/macro, iluminação, espelho/boroscópio já disponível se necessário, etiquetas temporárias de identificação e documentação. Instrumentação para assegurar desenergização somente pelo profissional. Não introduzir ferramentas no carro/garra sem contenção adequada.

**Riscos:** tensão residual, reenergização por terceiros, corte/queda de peças, perda da orientação de conectores, esforço sobre cabos antigos e movimento de massa suspensa.

**Critério de aprovação:** origem/destino e orientação de todos os condutores de controle são rastreáveis em fotos; fabricante/referência dos controles registrados quando existentes; pontos inacessíveis identificados. Identificar também como a máquina será impedida de aceitar comando remoto durante manutenção.

**Impedimentos:** ausência de controle da energia; fiação danificada ou terminais expostos sem tratamento pelo responsável; controle não acessível com segurança; massa suspensa sem condição segura.

**Próximo passo:** Fase C, caracterização do circuito sem energia. **Esta é a próxima ação prioritária da investigação atual: uma inspeção dirigida do joystick/botão e seu chicote.**

## 4. Fase C — Identificação dos circuitos de controle

**Objetivo:** decidir se cada direção/captura é contato, circuito resistivo/analógico, matriz ou comunicação digital e separar comando de iluminação.

**Pré-requisitos:** B aprovada; circuito desenergizado e liberado; orientação documentada dos conectores; estratégia profissional para evitar medições por caminhos paralelos da placa.

**Evidências necessárias:** tabela das relações elétricas de cada posição do joystick e estado do botão; valores medidos e escala; continuidade/abertura somente onde aplicável; marca/referência de microinterruptores/potenciômetros/CI; rastreio até conector de destino. As cores serão apenas nomes de identificação física, nunca definição de função.

**Ferramentas apropriadas:** multímetro em funções adequadas ao circuito desenergizado, documentação dos componentes e registro fotográfico; instrumentos especializados somente se a hipótese justificar. Um teste isolado de continuidade não prova tensão de operação, corrente nem ausência de multiplexação.

**Riscos:** leitura falsa por semicondutores/caminhos paralelos; confundir LEDs com contatos; danificar entradas com instrumento inadequado; perder conexão original.

**Critério de aprovação:** cada canal necessário tem natureza elétrica fundamentada; mapa de pares/referências e posição dos conectores documentado e revisado; requisitos que dependem de energização ficam separados para D. Se os controles forem digitais, identificar o circuito e obter documentação antes de propor emulação.

**Impedimentos:** relações ambíguas, inscrição/documentação incompatível, controles unidos a rede perigosa sem interface apropriada, impossibilidade de separar alimentação de comando.

**Próximo passo:** preparar plano específico de medições da Fase D. Nenhuma compra de módulo de interface deve anteceder essa definição.

## 5. Fase D — Medições elétricas por profissional

**Objetivo:** obter os parâmetros que determinam a interface e verificar comportamento da máquina original, incluindo seus limites de proteção.

**Pré-requisitos:** A–C aprovadas; plano de trabalho e de risco específico; instrumentos com categoria/faixa adequadas; acesso controlado; contenção e proteções estabelecidas; profissional tecnicamente qualificado executando ou supervisionando. Não é atividade de bancada doméstica para pessoa sem qualificação.

**Evidências necessárias:**

| Questão | Registro exigido | Por que determina o projeto |
|---|---|---|
| Sinais de direção/captura | Tensão diferencial e relativa à referência comprovada, DC/AC, faixa/picos, polaridade e formas de onda nas condições relevantes. | Seleção entre contatos isolados, optoacopladores, chaves bidirecionais ou protocolo. |
| Corrente e impedância das entradas | Método seguro escolhido pelo profissional, sem curto experimental de sinais desconhecidos; limites documentados. | Corrente nominal/mínima, fuga e queda admissível da interface. |
| Comando mantido/liberado | Resposta observada ao controle original, tempo de liberação e prioridade de direções. | Saber se soltar a entrada efetivamente para a movimentação manual. |
| Captura e ciclo automático | Sequência original descida/fechamento/subida/retorno/abertura. Ensaios de perda de comunicação ficam para F/G, após interface validada. | Distinguir ciclo independente da entrada e risco de interrompê-lo. |
| Crédito/início | Interface e semântica documentadas; como a placa confirma partida e encerra crédito. | Evitar crédito repetido/partida duplicada. |
| Fins de curso e falhas | Existência, tipo, posição e função por documentação/observação controlada. Não forçar colisões para descobrir limite. | Não presumir proteção existente ou independente. |
| Sensor de prêmio | Identidade, alimentação, forma de saída e critério de detecção; isolar apenas mediante projeto. | Não interpretar barra de quatro fios como saída simples. |
| Fonte/terra/chassi | Tensões medidas nos pontos identificados, capacidade disponível documentada e condição de proteção. | Não usar apenas etiqueta da fonte para alimentar adição. |
| Parada física | Função segura em manual, descida, içamento e retorno, incluindo retenção de massa e retorno de energia. | Definir resposta local à falha sem criar queda/perda de referência. |

**Ferramentas apropriadas:** multímetro, osciloscópio e sondas diferenciais/isoladas adequadas quando necessárias, documentação e aquisição de dados; analisador lógico apenas após confirmar limites e referência. Terra de osciloscópio pode unir indevidamente referências e provocar curto; o arranjo de medição precisa de avaliação profissional. Não remover terra de proteção para “isolar” um instrumento.

**Riscos:** choque, arco, curto por sonda, acionamento inesperado, carga suspensa, aquecimento e dano a entrada proprietária.

**Critério de aprovação:** ficha de interface por canal com máximos medidos/documentados, método e incerteza; sequência original observada; critérios de estado seguro e tempos máximos físicos definidos pelo responsável; resposta de manutenção e retorno de energia compreendida. Não basta a máquina mover uma vez.

**Impedimentos:** níveis desconhecidos/instáveis, ausência de caminho de parada validável, retorno automático perigoso, limites mecânicos sem condição segura, instrumentação inadequada ou evidência insuficiente de isolamento.

**Próximo passo:** escolher e projetar interface somente agora; ensaiá-la separadamente na Fase E.

## 6. Fase E — Protótipo independente em bancada

**Objetivo:** demonstrar temporização, compatibilidade e comportamento de falha sem conexão à máquina.

**Pré-requisitos:** D aprovada; especificação revisada; componentes compatíveis selecionados; alimentação de bancada adequada, cargas/simulador que representem as entradas medidas; nenhuma ligação ao chicote original.

**Evidências necessárias:** esquema e revisão do protótipo, ratings, isolamento/fuga/queda medidos conforme tecnologia; comportamento em boot/reset/queda parcial de energia; estados das saídas e registros de comandos; versão de firmware de teste. A supervisão externa deve atuar independentemente da tarefa que recebe comandos.

**Ferramentas apropriadas:** simulador de entradas, fonte de bancada, multímetro/osciloscópio/registrador apropriados, cargas representativas e gerador de tráfego local; rede de teste sem hardware real.

**Riscos:** dimensionamento incorreto, ativação por estado inicial de GPIO, contato travado, falha da fonte e confiar apenas no log do firmware.

**Critério de aprovação proposto:** 100 transições por canal sem opostos; 30 ciclos de energização/reset sem pulso indevido detectável pelo arranjo de medição; expiração de saída em até 300 ms após última atualização válida no perfil inicial; comandos com idade acima de 250 ms rejeitados; mensagens de sessão/boot/geração antigos e duplicatas incapazes de ativar saída. Esses tempos serão reduzidos se a análise mecânica exigir. Medir a interface eletricamente, não apenas LEDs/logs.

**Impedimentos:** qualquer pulso de boot, saída mantida por falha do processo, watchdog incapaz de remover permissão, efeito indevido de mensagem antiga ou incompatibilidade com limites da entrada.

**Próximo passo:** Fase F, avaliação da interface/proteções no conjunto de teste antes de conectá-la à máquina.

## 7. Fase F — Interface e proteções

**Objetivo:** validar contenção de falhas e autorizar tecnicamente a futura integração reversível.

**Pré-requisitos:** E aprovada; análise de falhas; circuito de permissão/parada local projetado; chicote adaptador documentado; enclausuramento, fixação, proteção de condutores e alimentação avaliados. O dimensionamento e eventual ensaio de isolamento devem ser definidos pelo profissional, sem aplicar testes destrutivos à PCB original.

**Evidências necessárias:** ensaio de perda de rede, perda do gateway, MCU bloqueado, reset/brownout, saída travada e troca local/remoto em simulador; limites de tempo e corrente registrados; procedimento de remoção da interface e retorno ao original. Ensaiar falha de contato preso por simulação controlada, sem soldar ou forçar defeito na máquina.

**Ferramentas apropriadas:** bancada da fase anterior, supervisão temporal independente, simulador, instrumentos selecionados pelo profissional e checklist baseado no esquema real.

**Riscos:** falha comum entre MCU e watchdog, supervisão alimentada pelo mesmo ponto que falha sem assumir estado seguro, ignorar contato de relé soldado, interferir em sensor ou proteção original.

**Critério de aprovação:** todas as falhas previstas retiram permissão ou são detectadas e contidas segundo a análise; saídas de crédito/captura não repetem na recuperação; controle local e remoto têm exclusão demonstrada; resposta física segura projetada e tempos definidos; nenhuma dependência exclusiva de backend ou Wi-Fi para proteção.

**Impedimentos:** falha de saída que escapa à contenção; existência de controle simultâneo local/remoto não previsto; ausência de resposta segura a movimento automático; circuitos sem ratings suficientes.

**Próximo passo:** profissional poderá autorizar integração controlada na Fase G. A aprovação de F não constitui autorização para usuário leigo conectar circuitos.

## 8. Fase G — Integração controlada com a máquina

**Objetivo:** demonstrar em uma unidade que a interface reproduz o comando original e preserva suas proteções e operação.

**Pré-requisitos:** A–F aprovadas; profissional e operador local presentes; máquina retirada do uso público; acesso remoto externo bloqueado; montagem inicialmente desenergizada conforme procedimento; chicote reversível e possibilidade de retorno ao original.

**Evidências necessárias:** fotos da montagem, configuração da máquina antes/depois, comandos locais de teste, medição das saídas e observação do mecanismo; comportamento ao liberar cada direção; sequência de captura; retorno de energia; operação local após remover adaptador; atuação da parada local em fases definidas pelo responsável.

**Ferramentas apropriadas:** controlador local de ensaio sem internet, instrumentação prevista, câmera para documentar sequência e tempos, barreiras/proteções e meio local de interrupção validado.

**Riscos:** movimento automático diferente do esperado, colisão, alteração da força da garra, queda de objeto, ciclos não interrompíveis pelo joystick e acionamento simultâneo por usuário local.

**Critério de aprovação proposto:** 20 comandos breves por direção e 20 ciclos completos de captura sem anomalia, respeitando regime/cooldown do fabricante quando identificado; todas as proteções originais verificadas sem provocar colisão; soltura e parada medidas dentro dos limites físicos definidos em D; nenhum reinício gera comando da interface; retorno ao original demonstrado. Amostra não prova vida útil nem segurança completa.

**Impedimentos:** divergência entre saída e movimento, fim de curso inoperante, avanço residual fora do limite, estado seguro não demonstrado, aquecimento anormal ou qualquer condição que exija contornar proteção.

**Próximo passo:** Fase H, interface web mínima em ambiente controlado e com operador local.

## 9. Fase H — Movimentação pela interface web de teste

**Objetivo:** validar o menor fluxo navegador → autorização → gateway → interface → máquina → vídeo.

**Pré-requisitos:** G aprovada; sessão de teste sem pagamento real; crédito inicial pelo meio original quando a interface de crédito não estiver validada; um jogador e um operador local; vídeo com enquadramento suficiente; página mínima de teste, sem exposição pública irrestrita.

**Evidências necessárias:** identificação de sessão/máquina, logs correlacionados, imagem de resposta física e saída, exclusividade, foco/toque/soltura, congelamento de vídeo e cancelamento de sessão. Confirmar controle frente/trás pela imagem e etiquetá-lo corretamente.

**Ferramentas apropriadas:** navegadores/dispositivos móveis, telemetria de rede, medição de vídeo vidro a vidro, registro elétrico quando exigido e software de teste isolado.

**Riscos:** aba suspensa, toque perdido, vídeo enganoso/atrasado, usuário controla máquina errada, sessão concorrente, comando retenido na reconexão.

**Critério de aprovação proposto:** apenas a sessão autorizada gera saída; 100 tentativas de outra sessão negadas; `pointercancel`, perda de foco, fechamento da aba e expiração liberam saídas dentro do limite de bancada e mantêm resposta física conforme D/G; captura duplicada não gera segunda ativação; p95 de comando ≤150 ms e vídeo vidro a vidro ≤300 ms na condição de teste, ou registrar reprovação e ajustar arquitetura. Não declarar prêmio/partida finalizada sem observação validada.

**Impedimentos:** qualquer comando sem sessão, retomada automática após reconexão, vídeo congelado que permite seguir jogando, dupla captura, limite físico excedido ou falta de operador local na PoC.

**Próximo passo:** Fase I, testes de falhas e estabilidade em redes representativas.

## 10. Fase I — Estabilidade, latência e recuperação

**Objetivo:** avaliar falhas reais de rede/software, consistência da partida e operação prolongada antes de decidir um piloto restrito.

**Pré-requisitos:** H aprovada; limites e respostas registrados; rede de teste capaz de degradar tráfego; procedimento profissional para ensaios que possam interromper energia; nenhuma falha elétrica improvisada no equipamento.

**Evidências necessárias:** resultados de perda/atraso/duplicação de mensagens no ambiente de teste, mudança de rede, backend indisponível, gateway travado, MCU reiniciado, falta/retorno de vídeo, sensor ausente/contraditório e pagamento simulado duplicado/atrasado. Separar falhas injetadas em simulador das efetivamente exercitadas na máquina.

**Ferramentas apropriadas:** emulação de rede já disponível ou fornecida por equipe autorizada, monitoramento, logs, medição elétrica/visual e registrador; ensaio térmico e interrupção de alimentação apenas conforme plano do responsável.

**Riscos:** acúmulo de comando antigo, assumir ausência de efeito após ACK perdido, dupla cobrança/crédito, fadiga do mecanismo e retorno inesperado após falha.

**Critérios de aprovação propostos:**

- 100 ciclos funcionais distribuídos em pelo menos 8 horas de observação, respeitando regime da máquina, sem comando inesperado, duplo crédito/captura ou violação de exclusividade. Não impor 8 horas contínuas de motor energizado.
- Cada falha de comunicação exercitada 20 vezes, com saídas remotas inativas no limite especificado e resposta física segura correspondente; nenhum replay após restabelecer conexão.
- Medir p50/p95/p99 e máximo de idade de comando e atraso de vídeo em rede cabeada/Wi-Fi local e internet representativa; incluir relay TURN se for caminho suportado. Falhar fechado se a idade não puder ser verificada.
- Em todas as interrupções nas janelas de crédito/captura, resultado físico desconhecido leva a reconciliação, sem retransmissão automática. Pagamentos duplicados simulados não produzem novo direito de jogo.
- Reinício do backend não permite nova sessão enquanto a máquina estiver em ciclo ou em estado desconhecido; reinício do dispositivo invalida autorização do boot anterior.
- Manutenção e parada locais continuam prioritárias; recuperação exige estado seguro confirmado e nova autorização.

**Impedimentos:** qualquer movimento não autorizado, replay físico, falha que mantenha saída/motor fora do limite, efeito de energia não compreendido, sensor usado comercialmente sem validação ou dados insuficientes para calcular os indicadores.

**Próximo passo:** revisão técnica dos registros e decisão sobre piloto restrito. Disponibilização comercial, operação sem presença local e pagamentos reais exigem avaliação adicional da instalação, manutenção e requisitos aplicáveis; aprovação deste plano não libera automaticamente essas etapas.

## 11. Modelo mínimo de folha de ensaio

| Campo | Preenchimento obrigatório |
|---|---|
| Ensaio / fase / requisito | Identificador único e critério objetivo associado. |
| Máquina / PCB / interface | Identidade física e revisão, com fotos. |
| Responsáveis / condições | Executor, supervisor, pessoas presentes, área controlada. |
| Energia e proteção | Procedimento aplicado, fontes consideradas, estado mecânico e meio local de parada. |
| Instrumentação | Modelo, escala/sonda, resolução, referência e limitações. |
| Estímulo | Controle original ou simulador/interface; tempo, direção e estado inicial. |
| Resultado elétrico | Dados brutos e tempos, sem inferir pela cor do fio ou pelo log. |
| Resultado mecânico | Movimento observado, estado final, sensor e vídeo vinculados. |
| Resultado financeiro lógico | Partida/crédito fictício, deduplicação e eventual reconciliação. |
| Decisão | Aprovado/reprovado/inconclusivo, justificativa e pendência. |

Até a inspeção B/C e caracterização D, a escolha elétrica permanece **NÃO IDENTIFICADO**. O resultado desejado do próximo trabalho de campo é um mapa verificável dos controles; não um acionamento remoto improvisado.
