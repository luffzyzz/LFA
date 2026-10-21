# Atividade sobre Agentes Inteligentes

Aula: 20/10/2026 


Professora: Kadidja Valéria 

Inteligência Artificial

**Disciplina:** Linguagens Formais e Autômatos 

Ciência da Computação / Engenharia de Software

**Estudante:** Kaynã Barbosa 

**Turma:** Ciência da Computação / Engenharia de Software



## Exercício 2.3
Para cada afirmação, indique V ou F, justifique e forneça exemplo ou contraexemplo. Explicite as hipóteses utilizadas.

### a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.

- Julgamento: **Falso**

  
- Justificativa: A racionalidade avalia a qualidade da decisão tomada em face das informações sensoriais que o agente efetivamente possui, visando maximizar o resultado esperado. Ela não pressupõe onisciência ou conhecimento pleno do estado global do mundo. Um agente sob observabilidade parcial continua sendo perfeitamente racional quando pondera as probabilidades dos estados possíveis e escolhe a ação de maior utilidade esperada.
- Exemplo / Contraexemplo: Um sistema de diagnóstico médico em uma emergência hospitalar não conhece todos os parâmetros biológicos internos do paciente nem possui biópsias instantâneas (ambiente parcialmente observável). Contudo, prescrever exames laboratoriais preliminares e estabilizar sinais vitais com base nos sintomas imediatos é um comportamento perfeitamente racional.

### b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.

- Julgamento: **Verdadeiro**

  
- Justificativa: Agentes reativos simples não possuem memória e mapeiam diretamente a percepção instantânea em ações via regras condição-ação. Quando o ambiente é parcialmente observável e apresenta situações distintas que produzem exatamente a mesma entrada sensorial (perceptual aliasing), ações diferentes seriam necessárias dependendo do passado. Sem um estado interno para distinguir esses cenários, o agente reativo puro comete erros repetitivos ou entra em laços fechados de repetição infinita.
- Exemplo / Contraexemplo: Um agente aspirador desprovido de sensor de localização operando em um labirinto ou em duas salas. Ao perceber [Limpo], ele não tem como saber em qual sala está; se sua regra mandar virar à direita, ele baterá continuamente contra a parede caso já esteja no limite do cômodo. Para agir de forma racional, precisaria de histórico interno (agente baseado em modelo) ou comportamento estocástico.

### c. Existe um ambiente de tarefa em que todo agente é racional.

- Julgamento: **Verdadeiro**

  
- Justificativa: O conceito de racionalidade está atrelado a uma métrica de sucesso (a medida de desempenho). Se um ambiente for modelado de tal forma que a pontuação atribuída seja idêntica para qualquer sequência de ações possíveis (ou se a medida de desempenho for indiferente ao estado do mundo), qualquer escolha feita por qualquer agente satisfaz a maximização do resultado esperado.
- Exemplo / Contraexemplo: Um ambiente no qual a medida de desempenho premia o agente com 50 pontos por ciclo de clock de forma incondicional, independentemente de ele mover atuadores, executar cálculos complexos ou permanecer estático. Nesse mundo trivial, todo e qualquer agente projetado atinge a pontuação máxima possível, sendo formalmente racional.

### d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.

- Julgamento: **Falso**

  
- Justificativa: Há uma distinção estrutural entre a formulação matemática e a implementação física. A função de agente (f: P* → A) recebe formalmente como entrada a sequência inteira de percepções acumuladas desde a inicialização do agente (P*). O programa de agente, por outro lado, é um processo de software em tempo de execução que recebe fisicamente através dos drivers de hardware apenas a percepção individual do instante corrente (p ∈ P).
- Exemplo / Contraexemplo: O código de controle de um piloto automático de drone é acionado ciclicamente via `processarPercepcao(leituraGiroscopioAtual)`. O sensor não injeta no método uma lista com todos os terabytes de dados inerciais coletados desde o primeiro voo do aparelho; o programa utiliza variáveis de estado na memória para reter o histórico que considerar relevante.

### e. Toda função de agente é implementável por uma combinação de programa/máquina.

- Julgamento: **Falso**

  
- Justificativa: Nem toda função matematicamente expressável é computável. A teoria da computação demonstra a existência de problemas indecidíveis que nenhuma máquina de Turing finita consegue solucionar. Além disso, em espaços contínuos, o conjunto de funções de agente teóricas tem cardinalidade não enumerável, superando a quantidade enumerável de programas possíveis em computadores digitais.
- Exemplo / Contraexemplo: Uma função teórica de agente que devesse receber como entrada um código-fonte arbitrário e emitir a ação *Seguro* se o código nunca entrar em laço infinito, ou *Perigoso* caso contrário. Como essa função resolve o Problema da Parada, ela não pode ser codificada em nenhuma arquitetura de hardware ou software real.

### f. Suponha que um agente selecione sua ação uniformemente ao acaso do conjunto de ações possíveis. Existe um ambiente de tarefa determinista em que esse agente é racional.

- Julgamento: **Verdadeiro**

  
- Justificativa: Se o ambiente de tarefa for estruturado de modo que todas as alternativas de ação permitidas levem determinística e comprovadamente ao mesmo resultado ótimo avaliado pela medida de desempenho, escolher qualquer ação por sorteio equiprovável maximiza a recompensa esperada.
- Exemplo / Contraexemplo: Um agente colocado diante de três botões idênticos (1, 2 e 3) onde a regra do ambiente determina que pressionar qualquer um deles desativa um alarme e pontua 100% de sucesso. O sorteio puramente aleatório com probabilidade 1/3 para cada botão produzirá sempre o resultado ótimo, cumprindo rigorosamente a definição de agente racional.

### g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.

- Julgamento: **Verdadeiro**

  
- Justificativa: A política interna de decisões do agente pode ser abrangente o suficiente para satisfazer as condições de otimização de ambientes diferentes, especialmente quando um ambiente compartilha a mesma dinâmica de estados do outro ou quando variações ambientais secundárias não interferem na eficácia das ações do agente.
- Exemplo / Contraexemplo: Um agente termostato baseado na regra "se temperatura > 24°C, ligar refrigeração; senão, desligar". Ele é perfeitamente racional em uma sala de servidores comerciais em Brasília e também em uma estufa botânica em Curitiba que exija exatamente a mesma faixa térmica, embora os dois ambientes possuam umidade, isolamento e dinâmicas externas completamente distintas.

### h. Todo agente é racional em um ambiente não observável.

- Julgamento: **Falso**

  
- Justificativa: Em um ambiente inobservável (sem sensores disponíveis), as ações executadas ainda impactam o ambiente e a medida de desempenho continua julgando o estado real alcançado. Um agente inteligente constrói um plano cego coerente (plano conformante) baseado no conhecimento prévio para atingir o objetivo com segurança, ao passo que um agente tolo tomará atitudes contraproducentes.
- Exemplo / Contraexemplo: Um robô pintor de interiores sem câmeras em uma sala fechada. O agente A executa uma trajetória pré-calculada que cobre metodicamente toda a superfície das paredes, maximizando a área pintada. O agente B colide sucessivamente com um único canto e joga tinta no piso repetidas vezes. O agente B é irracional, o que prova que nem todo agente é racional nesse contexto.

### i. Um agente jogador de pôquer perfeitamente racional nunca perde.

- Julgamento: **Falso**

  
- Justificativa: A racionalidade assegura a escolha que maximiza a utilidade esperada frente às probabilidades conhecidas, mas não tem controle sobre o fator estocástico (a distribuição das cartas do baralho) nem sobre a assimetria causada pela observabilidade parcial (cartas ocultas dos concorrentes). Um agente racional joga para obter lucro estatístico no longo prazo, mas está inevitavelmente sujeito à variância e derrotas em mãos individuais.
- Exemplo / Contraexemplo: Um agente decide pagar uma aposta final segurando uma sequência forte no river, onde os cálculos demonstram que ele vence em 95% dos cenários possíveis contra o padrão de apostas do oponente. Se, nos 5% restantes, o rival estiver segurando um full house improvável, o agente perderá as fichas daquela rodada sem ter cometido qualquer falha lógica de racionalidade.

## Exercício 2.4
Para cada caso, delimite o agente, preencha o PEAS e justifique todas as classificações. Considere Titã como cenário hipotético do exercício.

### Caso 1 — Jogar futebol.

- Agente analisado: Robô atacante autônomo (agente individual em cooperação com sua equipe).
- Objetivo e hipóteses: Deslocar-se ofensivamente pelo campo, receber lançamentos, driblar marcadores e chutar ao gol adversário dentro dos regulamentos da liga de robótica.
- P — Medida de desempenho: Gols marcados, índice de finalizações certas no gol, retenção eficiente da posse de bola, participação em jogadas de gol e ausência de penalidades ou faltas cometidas.
- E — Ambiente: Gramado ou piso regulamentar, duas traves, bola, companheiros de linha e goleiro aliado, time rival em marcação defensiva, linhas de campo e árbitro.
- A — Atuadores: Motores elétricos de acionamento de rodas/pernas articuladas para corrida e giro de corpo, solenoide ou atuador elástico de chute de precisão e transmissor de rádio tático.
- S — Sensores: Câmeras digitais panorâmicas com detecção de padrões, sensor laser (LiDAR) para mapeamento de distância dos defensores, acelerômetro/giroscópio e receptor Wi-Fi para instruções de jogadas.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O campo de visão óptico das câmeras sofre interferência por oclusões físicas geradas pelo aglomerado de robôs marcadores ao redor da bola. |
| Número de agentes | Multiagente (misto) | Cooperativo ao triangular passes com atletas do próprio time e competitivo contra o sistema defensivo adversário. |
| Previsibilidade | Estocástico | Pequenas perdas de tração no piso, rebotes na bola e decisões autônomas imprevisíveis dos zagueiros introduzem forte componente probabilístico. |
| Dependência entre decisões | Sequencial | Uma escolha de corrida ou um drible errado no início de um ataque altera o posicionamento de todo o time e condiciona as jogadas posteriores. |
| Mudança durante a decisão | Dinâmico | Enquanto o robô delibera sobre a trajetória do chute, a bola segue em movimento e os marcadores continuam se aproximando ativamente. |
| Natureza dos elementos | Contínuo | Velocidade de deslocamento, torque de aceleração, ângulos de chute e tempo de resposta transcorrem em grandezas contínuas. |
| Conhecimento do funcionamento | Conhecido | As diretrizes de pontuação, as regras de impedimento/falta e a física da bola são conhecidas a priori pelo modelo do agente. |

### Caso 2 — Explorar os oceanos subterrâneos de Titã.

- Agente analisado: Sonda robótica submarina autônoma autossuficiente (cryobot/submarine).
- Objetivo e hipóteses: Navegar sob a carapaça de gelo de Titã em profundidades extremas, investigar formações geológicas no leito oceânico, coletar dados oceanográficos e preservar sua própria integridade energética sem controle manual terrestre.
- P — Medida de desempenho: Área e volume navegados e catalogados, volume e valor científico de amostras moleculares analisadas, autonomia de bateria e preservação da carcaça sob pressão.
- E — Ambiente: Oceano subsuperficial de água e hidrocarbonetos/amônia sob alta pressão hidrostática, leito rochoso fraturado, correntes convectivas escuras e placas inferiores de gelo.
- A — Atuadores: Propulsores direcionais de jato hidráulico, lemes de mergulho, tanques de lastro pneumático, braço robótico coletor e transmissor acústico de dados.
- S — Sensores: Sonar de varredura multifeixe, medidores de condutividade, pressão e temperatura (CTD), espectrômetro de fluorescência, altímetro de fundo e sensores de deformação do casco.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | A ausência total de luz solar e o alcance finito dos feixes acústicos impedem que a sonda veja além de seu raio sensorial imediato. |
| Número de agentes | Agente único | A sonda navega isolada; processos ambientais térmicos e geológicos do oceano extraterrestre são dinâmicas do meio físico, não decisões de outros agentes. |
| Previsibilidade | Estocástico | Variações locais de viscosidade do fluido, surgimento imprevisto de jatos térmicos e turbulências subaquáticas impõem incerteza aos movimentos. |
| Dependência entre decisões | Sequencial | Consumir energia para investigar uma fenda hidrotermal específica restringe o alcance geográfico das rotas disponíveis para os ciclos seguintes. |
| Mudança durante a decisão | Dinâmico | O fluxo de correntes marinhas e variações de temperatura circundante evoluem continuamente durante o cálculo de trajetória da sonda. |
| Natureza dos elementos | Contínuo | Pressão hidrostática, profundidade barométrica, velocidade do fluxo e coordenadas espaciais variam em escalas contínuas. |
| Conhecimento do funcionamento | Desconhecido | A composição precisa dos compostos químicos, os mapas topográficos e a dinâmica reológica do oceano de Titã precisam ser aprendidos com a exploração. |

### Caso 3 — Comprar livros usados de IA na Internet.

- Agente analisado: Crawler e bot comprador automatizado de livros para sebos virtuais.
- Objetivo e hipóteses: Rastrear marketplaces digitais em busca de edições específicas de livros didáticos de IA, comparando preços, condições físicas e fretes para executar a melhor compra dentro de um orçamento predeterminado.
- P — Medida de desempenho: Valor monetário economizado (diferença entre preço pago e teto autorizado), conservação física reportada da obra, pontuação de reputação da loja e tempo de entrega.
- E — Ambiente: Servidores de e-commerce e sebos online (Amazon, Estante Virtual, AbeBooks), APIs de pagamento, tabelas de frete, anúncios de terceiros e catálogo de inventário.
- A — Atuadores: Envio de requisições web HTTP/POST para inserção no carrinho, submissão de lances, preenchimento de endereço e disparo do token de pagamento bancário.
- S — Sensores: Leitura e parsing de código HTML, respostas REST/JSON de APIs, monitor de preços, caixas de diálogo de confirmação e feeds RSS de novas listagens.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente tem acesso aos metadados e às fotos expostas, mas não tem como certificar-se do real estado físico interno do papel nem sabe se há outros compradores simultâneos na página. |
| Número de agentes | Multiagente competitivo | Outros consumidores humanos e robôs compradores monitoram e disputam os mesmos volumes raros em estoque único. |
| Previsibilidade | Estocástico | O estoque pode sofrer baixa por venda externa no mesmo segundo do fechamento da compra, ou o vendedor pode ter cadastrado o item em duplicidade. |
| Dependência entre decisões | Sequencial | Comprometer o saldo financeiro em um título reduz o capital disponível para fechar uma oferta melhor postada minutos depois. |
| Mudança durante a decisão | Semidinâmico | As listagens nos servidores permanecem inalteradas nos milissegundos de processamento do algoritmo, embora possam expirar caso a deliberação demore muito. |
| Natureza dos elementos | Discreto | Títulos de livros, preços em unidades monetárias inteiras/centavos, pontuação em estrelas e links de catálogo são variáveis discretas. |
| Conhecimento do funcionamento | Conhecido | As regras de navegação na Web, os métodos de checkout eletrônico e as políticas de compras da plataforma são formalmente estipulados. |

### Caso 4 — Jogar uma partida de tênis.

- Agente analisado: Robô tenista competidor de alto rendimento.
- Objetivo e hipóteses: Enfrentar e vencer um adversário humano ou robótico, golpeando a bola de tênis com velocidade e colocação tática para que ela quique na quadra adversária sem retorno válido.
- P — Medida de desempenho: Saldo de pontos e sets vencidos, taxa de primeiros saques convertidos, velocidade média das devoluções e minimização de bolas na rede ou fora das linhas.
- E — Ambiente: Quadra regulamentar com superfície padronizada (saibro ou piso sintético), rede divisória central, bola de tênis, raquete, adversário em ação e vento.
- A — Atuadores: Base móvel omnidirecional de deslocamento rápido em quadra e braço manipulador antropomórfico para empunhadura e execução do movimento de rebatida (forehand/backhand).
- S — Sensores: Câmeras de visão tridimensional estéreo de alta frequência, encoders nos eixos do braço robótico, sensores inerciais na base e acelerômetros acoplados à raquete.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente rastreia a posição tridimensional da bola, mas a taxa de rotação angular (topspin/slice) e a postura tática oculta do oponente trazem incertezas. |
| Número de agentes | Multiagente competitivo | O adversário executa contramedidas ativas com o objetivo explícito de anular as ações do agente e provocar seu erro. |
| Previsibilidade | Estocástico | Microirregularidades no piso que afetam o rebote, turbulências aerodinâmicas da bola e vibrações no impacto com as cordas produzem saídas estocásticas. |
| Dependência entre decisões | Sequencial | Uma devolução curta força o robô a recuar e compromete totalmente o seu equilíbrio postural para responder ao golpe seguinte do rival. |
| Mudança durante a decisão | Dinâmico | A bola cruza a quadra a dezenas de metros por segundo enquanto o computador de bordo calcula a cinemática inversa do braço mecânico. |
| Natureza dos elementos | Contínuo | Posição espacial, velocidade linear e angular da bola, torque nos motores e tempo decorrido são grandezas contínuas. |
| Conhecimento do funcionamento | Conhecido | As regras oficiais de pontuação da ITF e os princípios da mecânica balística e de atrito são plenamente conhecidos pelo modelo do agente. |

### Caso 5 — Praticar tênis contra uma parede.

- Agente analisado: Robô praticante e aprimorador de rebatidas de treino em paredão.
- Objetivo e hipóteses: Manter uma sequência contínua de golpes e devoluções rítmicas contra a parede, treinando estabilidade mecânica, pontaria de retorno e consistência de rebatidas.
- P — Medida de desempenho: Quantidade consecutiva de rebatidas sem interrupção, precisão no envio da bola para a zona delimitada da parede e regularidade temporal entre impactos.
- E — Ambiente: Parede vertical plana de concreto, solo demarcado, raquete fixa ao atuador e bola de tênis em quique repetitivo.
- A — Atuadores: Servomotores de controle do ângulo de impacto da raquete e base articulada com amortecimento de recuo.
- S — Sensores: Câmera de captura ultrarrápida voltada para a trajetória do rebote e sensor piezoelétrico de choque no encordoamento da raquete.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | A trajetória no ar é registrada pelas câmeras, mas variações microscópicas na elasticidade do feltro da bola e atrito local na parede não são detectáveis. |
| Número de agentes | Agente único | O paredão não é um competidor; é um anteparo rígido passivo governado apenas pelas leis da conservação de momento linear e atrito. |
| Previsibilidade | Estocástico | Embora seja muito mais previsível que um ser humano, o acúmulo de deformações microscópicas na bola e no solo insere pequenas oscilações probabilísticas. |
| Dependência entre decisões | Sequencial | A calibragem de potência e ângulo aplicada na rebatida atual condiciona a trajetória, a altura e o tempo disponível para preparar o golpe seguinte. |
| Mudança durante a decisão | Dinâmico | A bola ricocheteia e voa em direção ao robô sem pausas; atrasos no processamento resultam em perda de tempo de bola e quebra da sequência. |
| Natureza dos elementos | Contínuo | Espaço tridimensional, velocidades cinemáticas de retorno e aceleração mecânica são contínuos. |
| Conhecimento do funcionamento | Conhecido | O coeficiente de restituição elástica e as leis newtonianas de reflexão de impacto são formalmente conhecidos pelo software. |

### Caso 6 — Realizar um salto de altura.

- Agente analisado: Robô atleta saltador antropomórfico (salto em altura com sarrafo).
- Objetivo e hipóteses: Executar corrida em curva de aproximação, impulsão vertical com rotação de dorso e transposição limpa do sarrafo suspenso, aterrissando com segurança sobre o colchão de espuma.
- P — Medida de desempenho: Altura máxima oficial transposta sem derrubar a barra, impulsão regulamentar dentro da área de salto e estabilidade estrutural na aterrissagem.
- E — Ambiente: Pista de corrida sintética semicircular, área de impulsão, dois suportes verticais graduados, sarrafo de fibra de vidro e colchão de queda.
- A — Atuadores: Servomotores de alto torque nos joelhos e quadris mecânicos, atuadores pneumáticos/elásticos nos tornozelos para propulsão vertical e articulações da coluna para arqueamento dorsal.
- S — Sensores: Telêmetro laser (LiDAR) para cálculo milimétrico da distância até o plano do sarrafo, sensores de pressão tátil na sola dos pés mecânicos e giroscópios de equilíbrio em voo.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Completamente observável | A posição exata do sarrafo, o traçado da pista e o alinhamento da área de impulsão estão inteiramente expostos e estáveis sob a leitura dos sensores. |
| Número de agentes | Agente único | A tentativa de salto é individual; não há adversários ou parceiros interagindo ou obstruindo fisicamente a pista naquele momento. |
| Previsibilidade | Determinístico | Em condições de ginásio fechado sem correntes de vento anômalas, a física da conversão de momento horizontal em impulsão vertical é totalmente determinística. |
| Dependência entre decisões | Sequencial | A modulação das passadas na curva de aproximação estabelece a energia cinética que será convertida no instante da chamada de impulsão. |
| Mudança durante a decisão | Dinâmico | Após o início do sprint de corrida, o robô precisa processar suas leituras e disparar a impulsão em milissegundos com o corpo em movimento acelerado. |
| Natureza dos elementos | Contínuo | Distâncias espaciais, velocidade de corrida, curvas de torque aplicadas e trajetórias no ar são grandezas contínuas. |
| Conhecimento do funcionamento | Conhecido | As leis balísticas gravitacionais e os princípios mecânicos corporais são descritos com exatidão por equações newtonianas conhecidas. |

### Caso 7 — Participar de um leilão de um item, realizando lances.

- Agente analisado: Softbot negociador de pregão eletrônico institucional.
- Objetivo e hipóteses: Vencer a licitação de um lote específico pelo menor desembolso possível, submetendo lances calculados que fiquem estritamente abaixo do valor teto autorizado.
- P — Medida de desempenho: Aquisição do item, margem de economia (teto orçamentário autorizado menos preço final arrematado) e não submissão a lances inflacionados de forma irracional.
- E — Ambiente: Plataforma web de leilões eletrônicos, relógio com contagem regressiva oficial de encerramento, quadro de lances correntes e outros participantes conectados.
- A — Atuadores: Envio de pacotes de dados contendo propostas financeiras de lance no valor exato desejado ou envio do sinal de desistência/saída da rodada.
- S — Sensores: Recepção via WebSockets/API dos eventos de lances concorrentes, identificação do valor corrente da melhor oferta, leitura do tempo restante do pregão e status de aceitação do lance.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente observa todas as ofertas aceitas no painel público, mas desconhece os limites financeiros de reserva e a disposição a pagar dos outros participantes. |
| Número de agentes | Multiagente competitivo | Outros agentes concorrem de forma antagônica pelo mesmo ativo indivisível, tentando forçar aumentos de preço ou esconder estratégias. |
| Previsibilidade | Estocástico | As ofertas que serão submetidas pelos rivais no último instante não são calculáveis com certeza absoluta, devendo ser tratadas por distribuições probabilísticas. |
| Dependência entre decisões | Sequencial | Um lance ofertado prematuramente pode elevar artificialmente o preço de corte e incentivar os concorrentes a recalibrarem suas próprias estratégias nas rodadas seguintes. |
| Mudança durante a decisão | Dinâmico | O cronômetro regressivo da plataforma decresce sem interrupção; a hesitação em responder a uma oferta antes do estouro do relógio resulta na perda do leilão. |
| Natureza dos elementos | Discreto | As quantias monetárias válidas sobem em passos de incremento fixo e os lances constituem transações numeráveis no tempo. |
| Conhecimento do funcionamento | Conhecido | As regras de incremento, os prazos de contagem regressiva e os critérios de validação de lances do pregão são formalmente definidos pelas normas do leilão. |

### Opções para classificação
- **Observabilidade:** Completamente observável, parcialmente observável ou não observável.
- **Número de agentes:** Agente único ou multiagente; indique cooperação ou competição quando pertinente.
- **Previsibilidade:** Determinístico ou estocástico; considere a influência estratégica de outros agentes.
- **Dependência entre decisões:** Episódico ou sequencial.
- **Mudança durante a decisão:** Estático, dinâmico ou semidinâmico.
- **Natureza dos elementos:** Discretos, contínuos ou combinação; considere estados, tempo, percepções e ações.
- **Conhecimento do funcionamento:** Conhecido ou desconhecido para o agente.

### Comparação final

**1. O que muda entre jogar tênis contra outra pessoa e praticar contra uma parede?**

A cisão principal entre os dois problemas reside no **Número de Agentes**. Na partida de tênis, o robô opera em um ambiente multiagente estritamente competitivo, no qual o oponente planeja jogadas deliberadas para contrapô-lo, exigindo que o agente incorpore modelagem psicológica e estratégica do rival. No treino contra o paredão, o contexto é de agente único: a parede é um obstáculo passivo, estático e previsível, cujos retornos de bola dependem puramente das ações do próprio robô projetadas sobre as leis da física reflexiva.

**2. Por que comprar livros usados pode exigir decisões com informações incompletas?**

O caráter parcialmente observável do ambiente de compra decorre tanto da assimetria na avaliação do produto (descrições textuais e fotos de catálogo podem ocultar defeitos estruturais internos, páginas soltas, riscos ou mofo) quanto da incerteza logística e transacional (desconhecimento do volume real em estoque, honestidade no despacho e pontualidade da entrega). Um agente racional contorna essa falta de dados inferindo índices de confiabilidade a partir da reputação histórica do vendedor e calculando descontos de prêmio de risco antes de fechar o pedido.

**3. Como outros agentes influenciam futebol e leilões?**

No futebol, a interação entre múltiplos agentes opera em uma dinâmica mista e física no espaço contínuo: companheiros cooperam para organizar a linha de passe e atacantes disputam contato corporal direto com os defensores, exigindo reações cinemáticas contínuas em frações de segundo. No leilão, por sua vez, a influência dos demais agentes é puramente estratégica, informativa e econômica: o impacto de um competidor não ocorre por choque motor, mas pela submissão de valores que estreitam a margem de utilidade do agente, forçando o cálculo de blefes, contenção emocional de lances e proteção contra a maldição do vencedor.

## Exercício 2.5
Defina cada termo com suas palavras em duas a quatro linhas e apresente um exemplo.

### Agente

- Definição: Qualquer estrutura física ou computacional que interage de maneira contínua com seu meio externo, captando dados brutos do ambiente por sensores e produzindo efeitos ou transformações sobre esse mesmo meio através de seus atuadores.
- Exemplo: Um sistema de irrigação automatizada que afere a umidade da terra por hastes condutivas e abre as válvulas solenoides de água quando o solo resseca.

### Função de agente

- Definição: Formulação matemática abstrata que determina o comportamento global de um agente ao estabelecer uma relação funcional direta entre qualquer sequência histórica de percepções já recebidas e a ação a ser tomada.
- Exemplo: A função que prescreve matematicamente que, após a sequência [Porta_Aberta, Sem_Objeto], a ação associada é Emitir_Sinal_Fechamento.

### Programa de agente

- Definição: A concretização em software do algoritmo decisório que executa sobre um computador ou hardware específico, recebendo exclusivamente o dado perceptual do ciclo atual e acionando os atuadores físicos em tempo real.
- Exemplo: O firmware em C++ compilado em um microcontrolador STM32 que lê os canais de um conversor analógico-digital e comuta pontes H de motores.

### Racionalidade

- Definição: A propriedade segundo a qual um agente seleciona, a cada instante, a linha de ação que gera o maior valor esperado de sucesso, tendo como balizadores sua métrica de desempenho, sua bagagem histórica de percepções e o conhecimento que possui sobre o ambiente.
- Exemplo: O sistema de um veículo autônomo que opta por frear e desacelerar gradualmente ao avistar luzes de alerta de obras na via, reduzindo o risco estatístico de colisão.

### Autonomia

- Definição: Grau de independência com que um agente guia suas escolhas, pautando-se predominantemente no aprendizado e na adaptação decorrentes de sua própria interação com o mundo, em vez de depender estritamente de dados e planos inseridos a priori pelo projetista.
- Exemplo: Um robô cortador de grama que redefine seus percursos ao perceber que áreas sombreadas do jardim crescem mais lentamente, dispensando ajustes manuais de cronograma.

### Agente reativo

- Definição: Arquitetura computacional direta que toma decisões com base exclusivamente no dado sensorial recebido no instante corrente, operando por regras imediatas de causa e efeito (se-então) sem reter histórico passado na memória.
- Exemplo: O mecanismo do airbag veicular que dispara os geradores de gás unicamente quando o acelerômetro acusa uma desaceleração instantânea superior a um limiar crítico de impacto.

### Agente baseado em modelo

- Definição: Agente dotado de um estado interno de memória que reproduz aspectos do ambiente que estão fora do alcance visual imediato, utilizando modelos sobre como o mundo se transforma por conta própria e como reage às ações do próprio agente.
- Exemplo: Um robô aspirador que memoriza em sua matriz interna a existência de uma mesa na sala ao lado e não colide com ela ao navegar na escuridão.

### Agente baseado em objetivos

- Definição: Modelo de controle que alia a representação do estado corrente a uma definição explícita de uma meta a ser atingida, orientando suas escolhas por meio de algoritmos de busca e planejamento encadeado para alcançar esse objetivo.
- Exemplo: Um programa planejador logístico que estrutura toda a cadeia de transbordo entre portos e rodovias visando entregar uma carga no destino contratado dentro de 48 horas.

### Agente baseado em utilidade

- Definição: Estrutura avançada que aplica uma função contínua de preferência (utilidade) para ranquear o grau de qualidade ou satisfação proporcionado por diferentes estados finais, permitindo escolher o melhor caminho em cenários de incerteza e múltiplos objetivos em conflito.
- Exemplo: Um roteador de redes inteligentes que pondera latência, custo de transmissão por link e perda percentual de pacotes ao eleger a rota para um pacote de dados de streaming.

### Agente com aprendizagem

- Definição: Concepção arquitetural composta por quatro módulos funcionais (desempenho, crítico, elemento de aprendizado e gerador de problemas) que capacita o sistema a refinar seus parâmetros decisórios e adquirir novas habilidades com a experiência empírica.
- Exemplo: Um algoritmo anti-fraude financeiro que reajusta seus limiares de bloqueio de cartões após analisar o histórico de transações que foram confirmadas ou contestadas pelos clientes ao longo do mês.

## Síntese com autômatos
Escolha um caso do item 2.4. Apresente três estados internos, três percepções, três ações e duas regras no formato estado atual + percepção → próximo estado e ação. Explique como estados internos representam informação passada e cite uma limitação da simplificação.

**Cenário Escolhido: Caso 2 — Explorar os Oceanos Subterrâneos de Titã (Sonda Robótica Submarina)**

**1. Elementos Formais do Autômato de Estados Finitos:**

**Conjunto de Estados Internos (Q):**
- q₀: *Navegacao_Cruzeiro* — sonda em deslocamento autônomo estável registrando métricas batimétricas basais.
- q₁: *Amostragem_Cientifica* — sonda estabilizada diante de uma fonte hidrotermal ativa coletando fluidos.
- q₂: *Manobra_Evasiva_Risco* — sonda em modo de autopreservação recuando de gradientes de pressão ou choques físicos.

**Alfabeto de Percepções de Entrada (Σ):**
- p₁: *Pluma_Hidrotermal_Detectada* — espectrômetro e sensores térmicos detectam anomalia química de grande interesse científico.
- p₂: *Obstaculo_Ou_Pressao_Critica* — sensores de deformação do casco acusam elevação perigosa de carga mecânica ou sonar aponta leito rochoso próximo.
- p₃: *Coleta_Amostra_Concluida* — indicador de preenchimento do compartimento de amostras confirma sucesso da operação.

**Alfabeto de Ações de Saída (A):**
- a₁: *Travar_Posicao_E_Acionar_Coletor* — acionar propulsores de contrapeso e estender o braço robótico de captura.
- a₂: *Inverter_Propulsores_E_Subir* — forçar empuxo reverso nos jatos d'água e despressurizar tanques de lastro para ganhar elevação.
- a₃: *Retomar_Propulsao_Cruzeiro* — fechar compartimentos, ligar os propulsores principais e prosseguir no plano de rota.

**2. Regras de Transição (δ: Q × Σ → Q × A):**

**Regra 1:** δ(q₀, p₁) = (q₁, a₁)
Se a sonda opera em *Navegacao_Cruzeiro* (q₀) e seu sensor detecta *Pluma_Hidrotermal_Detectada* (p₁), o agente executa a ação *Travar_Posicao_E_Acionar_Coletor* (a₁) e comuta seu estado para *Amostragem_Cientifica* (q₁).

**Regra 2:** δ(q₁, p₂) = (q₂, a₂)
Se a sonda está em *Amostragem_Cientifica* (q₁) e os sensores acusam *Obstaculo_Ou_Pressao_Critica* (p₂), ela interrompe a amostragem, executa a ação emergencial *Inverter_Propulsores_E_Subir* (a₂) e transita para o estado *Manobra_Evasiva_Risco* (q₂).

**3. Como o estado interno representa informação passada e limitações da simplificação:**

**Representação da informação passada:** O estado interno resume a sequência de eventos pretéritos vivenciada pela sonda sem a necessidade de reprocessar todo o log histórico de dados. Encontrar-se no estado q₁ sintetiza que, momentos atrás, a sonda navegava em cruzeiro, detectou compostos químicos valiosos no fluido e executou a manobra de aproximação com sucesso. É esse estado interno que confere coerência temporal ao comportamento do agente em um ambiente escuro e parcialmente observável.

**Limitação da simplificação por autômatos finitos:** A física submarina real é inerentemente contínua e complexa, envolvendo equações de mecânica dos fluidos, empuxo hidrostático e cinemática vetorial tridimensional (ℝ³). A modelagem por autômatos de estados finitos assume um universo atômico e quantizado: qualquer ajuste fino de estabilização em face de uma corrente submarina contínua exigiria uma explosão combinatória de milhares de estados discretos intermediários, tornando o autômato rígido e inviável para controlar o sistema dinâmico contínuo de propulsão e pressão de um veículo robótico real.


| Critério | Atividade avaliativa (1,0 ponto) A2 |
|---|---:|
| Item 2.3 — correção e argumentação | 30% |
| Item 2.4 — PEAS e classificação justificada | 40% |
| Item 2.5 — precisão conceitual e exemplos | 20% |
| Síntese, organização e referências | 10% |
