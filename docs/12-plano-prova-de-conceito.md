# 12 — Plano focalizado de prova de conceito

Data: 24/10/2026. Complementa [08 — validação](08-plano-validacao.md), sem repetir suas fases ou afirmar que foram executadas. Base: [segunda investigação](11-investigacao-focalizada.md). **Escolha atual: investigar A; manter B condicional; reservar C para inviabilidade comprovada de A/B.** Não há hardware, circuito, orçamento ou ensaio físico aprovado nesta rodada.

## Decisão A/B/C e custo

| Critério | A — Reproduzir controles existentes | B — Protocolo nativo comprovado | C — Substituição parcial |
|---|---|---|---|
| Compatibilidade hoje | **PROVÁVEL**, contatos de lâmina candidatos | **NÃO IDENTIFICADA**, há apenas porta candidata | **NÃO IDENTIFICADA**, atuadores/sensores sem especificação |
| Dado que libera avaliação | Mapa e caracterização elétrica de joystick/botão | Identidade da revisão, níveis e documentação operacional correspondente | Especificação do bloco substituído, atuadores, limites e proteções |
| Hardware adicional esperado | Interface por sinal validado, controlador local, chicote e alimentação/proteção | Interface elétrica/transceptor apropriado, gateway e autorização local | Controlador, interfaces/possíveis drivers, sensores e proteções conforme fronteira |
| Custo relativo de engenharia | Menor se contatos simples forem confirmados; cresce com matriz, isolamento e arbitragem | Incerto: pode ser pequeno com manual; investigação sem documentação pode superar A | Maior escopo de projeto, montagem, testes e manutenção |
| Risco principal | Falsear entrada, conflito local/remoto e saída presa | Transmitir para manutenção/programação ou interpretar ACK como efeito | Assumir ciclo, movimento, força e proteções sem equivalência demonstrada |
| Reversibilidade | Alta somente com adaptador removível e circuito validado | Alta somente para operação documentada sem gravar configuração/firmware | Menor; requer mapa de retorno e conservação do conjunto original |
| O que a evidência atual não permite | Escolher automaticamente relé, opto ou PhotoMOS | Tratar RXD/TXD como API de joystick | Escolher controladora universal ou drivers de motor |

Não há cotação monetária nesta etapa: quantidade de polos, tecnologia de interface, conectores e reaproveitamento do vídeo ainda estão indefinidos. O custo deve separar levantamento profissional, interface/chicote, gateway/vídeo, montagem/proteções e validação. Priorizar instrumentos e computador já disponíveis. Não comprar conversor serial, módulo de relés ou câmera antes de fechar a respectiva especificação.

**Mudança possível na decisão:** uma interface nativa documentada pode servir somente a crédito/telemetria. Nesse caso, A continua para movimento e B é avaliada separadamente para eventos. Não se presume suporte a ambas as funções por compartilhar um conector. O documento público encontrado é uma referência de pesquisa, sem compatibilidade demonstrada com esta máquina.

## Única próxima evidência prioritária

**Entregar uma ficha profissional desenergizada do joystick e botão até o conector de destino na controladora.** A ficha deve conter uma vista contínua eixo–base, macros dos contatos/terminais do botão separados da iluminação, conectores com orientação identificada e tabela de continuidade por posição, com os contatos adequadamente isolados da eletrônica. Não precisa remover etiquetas ou alterar firmware.

O profissional deve tratar fontes, energia residual e partes móveis e comprovar ausência de tensão antes do levantamento. Um mapa só de cores não atende. Uma fotografia isolada do conector da PCB também não relaciona o comando ao destino. Essa ficha é o primeiro portão; os itens abaixo ficam dependentes dela.

## Portões de evidência antes de compra ou adaptação

| Portão | Entrega mínima | Aprovação objetiva | Situação |
|---|---|---|---|
| P0 — acervo | Originais, hashes e inspeção | 37 originais únicos, hashes correspondentes e todas as aberturas registradas | **CONCLUÍDO** nesta investigação |
| P1 — controles | Ficha descrita acima | Cada direção, neutro e botão relacionados a terminais e destino; iluminação separada; nenhuma ambiguidade de comum/polo | **PENDENTE** |
| P2 — características elétricas | Relatório profissional de caracterização planejada | Faixa, polaridade, referências, corrente, varredura, aberto/fechado, transientes e tempos medidos; instrumentos apropriados | **PENDENTE**; nenhuma medição executada |
| P3 — resposta da máquina original | Registro supervisionado do ciclo e falhas permitidas | Consumo de crédito, soltura, captura, retorno e resposta de parada definidos por fase | **PENDENTE** |
| P4 — especificação da interface | Componente/variante, limites, proteção, alimentação, chicote e arbitragem | Margens verificáveis para P2; estado no boot/sem alimentação e tratamento de saída presa definidos | **PENDENTE** |
| P5 — vídeo | Modelo/manual e ensaio local de caminho de vídeo | Acesso autorizado, campo útil, atraso e detecção de congelamento medidos | **PENDENTE** |

P1 deve ser desenergizado. P2/P3 são trabalhos físicos posteriores, exclusivamente planejados e executados pelo profissional responsável em ambiente controlado; este documento não fornece procedimento de ligação em eletrônica energizada. Não conectar GPIO, adaptador serial ou analisador a circuito desconhecido. Compras só podem ser especificadas após os portões correspondentes; integração na máquina exige também bancada e validação do plano 08.

## Arquitetura mínima proposta

Fluxo de comandos: **navegador → backend com reserva exclusiva → agente local → controlador de saídas → interface validada → entradas da controladora original**. O ciclo dos atuadores permanece na placa original, sujeito à resposta real verificada em P3.

Fluxo de observação: **entradas/sensores validados → registro local → backend**. Fluxo de vídeo independente: **câmera identificada → caminho de mídia adequado → navegador**. A seleção de MCU/SBC depende dessas cargas; vídeo não deve bloquear a expiração local de comandos.

Uma autorização exclusiva deve abranger tanto o usuário remoto quanto o modo local: um adaptador em paralelo não impede o painel físico de comandar o sentido oposto. A definição elétrica da arbitragem deve preservar a possibilidade de uso original e prioridade de manutenção/parada local; não pode depender apenas de um aviso no navegador.

O controlador local inicia inibido e exige nova sessão após reinício. Aceita apenas estados recentes de movimento, com identificação de máquina, sessão, geração de autorização e sequência crescente. Mantém prazo local independente do navegador/backend, rejeita direções opostas e não repassa fila antiga depois da reconexão. O relógio usado para medir validade precisa ter seu erro/limite definido, sem confiar em horário arbitrário enviado pelo cliente.

Captura e crédito são eventos separados. Cada evento tem identidade persistente e resultado observado, quando disponível. Uma interrupção entre emitir o evento e confirmar seu efeito gera **resultado desconhecido**, bloqueio de repetição automática e reconciliação local. Sem realimentação validada não existe garantia física de execução exatamente uma vez. Na PoC inicial, manter crédito pelo método original e não habilitar pagamento real.

Não exibir “prêmio confirmado” com base em ACK, clique de captura, temporizador ou uma imagem estática. A barra candidata pode observar passagem; sua semântica só entra no sistema após ser validada. O estado “disponível” exige sessão encerrada e máquina conciliada, além de conectividade.

## Bancada isolada da máquina

Após P4, ensaiar primeiro a lógica e a interface com simulador/carga de teste dimensionada segundo P2, sem qualquer ligação à máquina. Antes de P4, é possível revisar o contrato e simular estados sem selecionar hardware; essa simulação não foi implementada neste trabalho.

| Cenário de bancada | Resultado exigido e registro |
|---|---|
| Boot, reset e alimentação ausente/retornada | Nenhum comando transitório; nova autorização obrigatória; medir saídas reais do protótipo |
| Expiração, backend fora e agente travado | Saídas voltam ao neutro especificado dentro do limite de bancada; registrar máximo, não só média |
| Sessão concorrente ou autorização antiga | Nenhuma saída; teste inclui mensagens atrasadas após troca de jogador |
| Sequência duplicada/fora de ordem | Não restaurar movimento antigo; evento de captura/crédito não repetir |
| Esquerda+direita ou frente+trás | Estado rejeitado/neutro conforme contrato; diagonais inicialmente desabilitadas |
| Reconexão com mensagens acumuladas | Sem replay; sessão inválida até recuperação explícita |
| Evento emitido e confirmação perdida | Resultado desconhecido, sem emissão automática adicional |
| Saída simulada presa | Bloqueio e contenção independente conforme projeto; timeout de software sozinho não basta |
| Vídeo ausente/congelado | Inibir novos movimentos; recuperar somente com quadros úteis e autorização válida |

Os números de 07/08 são metas iniciais de engenharia: comando p95 até 150 ms, vídeo p95 até 300 ms e liberação elétrica da interface até 300 ms após a última atualização válida. Não são valores medidos ou limites de segurança. P3 deve definir prazo e deslocamento físicos admissíveis por fase; esses requisitos prevalecem sobre as metas de bancada. Um ciclo automático pode continuar após todas as entradas remotas serem liberadas.

## Validação na máquina e critérios de sucesso

Somente depois de P1–P4, bancada aprovada e resposta de parada definida, planejar integração profissional removível com operador local, sem uso público. Aplicar os ensaios e amostras do [plano 08](08-plano-validacao.md), registrando separadamente o que foi simulado, medido eletricamente e observado mecanicamente. Não provocar falhas destrutivas nem contornar fins de curso/proteções.

A PoC só pode ser considerada bem-sucedida quando:

1. As cinco funções de jogador forem reproduzidas com equivalência documentada ao painel, sem alterar força/configuração da garra ou sensores originais.
2. Neutro, término e falhas tiverem comportamento físico registrado por fase; existir resposta local validada para o estado real da máquina.
3. Apenas uma autorização válida controlar a máquina; modo local/manutenção invalidar o remoto; nenhuma reconexão ou inicialização gerar comandos.
4. O caminho de vídeo tiver modelo/acesso documentados, enquadramento útil e latência medida nas condições de rede declaradas.
5. Crédito, início, captura, término e passagem de prêmio permanecerem eventos distintos; informação não observável continuar marcada como desconhecida.
6. Remover o adaptador restaurar a operação original demonstrada, com registros e fotografias antes/depois.

Se qualquer portão reprovar, registrar motivo e revisar a fronteira da interface. Migrar para B apenas com evidência específica; considerar C se A/B forem incompatíveis ou insuficientes para a resposta segura exigida. **Estado desta entrega: documentação e acervo concluídos; PoC física não iniciada.**
