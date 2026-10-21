# Atividade sobre Agentes Inteligentes

Aula: 20/10/2026 | Professora: Kadidja Valéria | Inteligência Artificial

**Disciplina:** Linguagens Formais e Autômatos | Ciência da Computação / Engenharia de Software

**Estudante:** Deivid Cerqueira | **Turma:** Ciência da Computação / Engenharia de Software

Realize os exercícios 2.3, 2.4 e 2.5 do Capítulo 2 sobre agentes inteligentes. Analise a racionalidade, descreva ambientes de tarefa por meio do modelo PEAS e explique os conceitos com suas próprias palavras. Utilize o capítulo disponibilizado e justifique suas respostas.

**Modalidade sugerida:** individual com consulta. **Tempo estimado:** 2h30. **Prazo:** conforme orientação da professora.

## Preparação
Leia os tópicos sobre racionalidade, ambientes e estrutura dos agentes, especialmente a Seção 2.3.2.

## Exercício 2.3
Para cada afirmação, indique V ou F, justifique e forneça exemplo ou contraexemplo. Explicite as hipóteses utilizadas.

### a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.

- Julgamento: **Falso**
- Justificativa: Conforme a Seção 2.2, a racionalidade avalia a escolha da ação que maximiza o desempenho esperado com base nas evidências fornecidas pela sequência de percepções até o momento e no conhecimento prévio, não na onisciência ou no resultado real perfeito após o fato. A observabilidade parcial impõe incerteza, mas o agente ainda pode ser perfeitamente racional selecionando a melhor ação estatística e logicamente ótima perante essa incerteza.
- Exemplo / Contraexemplo: Um veículo autônomo na neblina ou um jogador de cartas que não vê a mão do adversário: ambos possuem apenas percepções parciais, mas continuam tomando decisões perfeitamente racionais calculando probabilidades para maximizar a utilidade esperada.

### b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.

- Julgamento: **Verdadeiro**
- Justificativa: Conforme demonstrado nas Seções 2.3.2 e 2.4.2, agentes reativos simples baseiam-se unicamente na percepção atual. Em ambientes parcialmente observáveis, perceptos idênticos podem exigir ações opostas dependendo do que ocorreu no passado (aliasing perceptual). Sem um estado interno para registrar esse histórico, agentes reativos determinísticos entram inevitavelmente em ciclos ou laços infinitos (loops).
- Exemplo / Contraexemplo: O aspirador de pó em um ambiente de dois cômodos (A e B) desprovido de sensor de posição (possuindo apenas sensor de sujeira: [Sujo] ou [Limpo]). Ao perceber [Limpo], se a regra for mover-se para a direita e ele já estiver no cômodo B, colidirá perpetuamente com a parede; para ser racional, precisaria manter um estado interno ou usar aleatorização.

### c. Existe um ambiente de tarefa em que todo agente é racional.

- Julgamento: **Verdadeiro**
- Justificativa: A racionalidade é avaliada em função de uma medida de desempenho (Seção 2.2.1). Se o ambiente for definido de tal forma que a medida de desempenho atribua a mesma pontuação invariável para qualquer sequência de estados gerada (por exemplo, pontuação constante igual a zero ou valor máximo fixo), toda e qualquer ação selecionada por qualquer agente será, por definição, ótima.
- Exemplo / Contraexemplo: Um ambiente em que a medida de desempenho concede 100 pontos para qualquer comportamento do agente (ou um ambiente passivo sem ações executáveis além de aguardar). Nele, todo agente atinge o desempenho máximo possível, sendo formalmente racional.

### d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.

- Julgamento: **Falso**
- Justificativa: A Seção 2.4.1 enfatiza explicitamente essa distinção: a função do agente é um mapeamento matemático abstrato que toma como entrada o histórico completo de tudo o que já foi percebido (a sequência de percepções P\*), enquanto o programa do agente é a implementação concreta que recebe fisicamente do hardware apenas a percepção imediatamente atual (p ∈ P).
- Exemplo / Contraexemplo: No código de controle de um robô, a função é executada a cada instante na forma `executar(percepcaoAtual)`. O agente não recebe toda a lista de milhões de leituras sensoriais anteriores como argumento; se precisar do histórico, ele próprio deve armazená-lo em variáveis de estado interno.

### e. Toda função de agente é implementável por uma combinação de programa/máquina.

- Julgamento: **Falso**
- Justificativa: Limitações fundamentais da teoria da computação (estabelecidas por Gödel e Turing) e restrições físicas de capacidade de armazenamento e tempo (Seção 2.4.1) impedem a implementação de todas as funções possíveis. O conjunto de funções matemáticas de agente em domínios contínuos é incontável, ao passo que o conjunto de programas de computador possíveis é enumerável. Ademais, funções que envolvam problemas formalmente indecidíveis não podem ser computadas por nenhuma arquitetura física.
- Exemplo / Contraexemplo: Uma função de agente teórica cuja especificação exigisse decidir, a cada ciclo perceptual, se um programa arbitrário fornecido via sensor irá parar ou entrar em loop infinito (o Problema da Parada de Alan Turing). Nenhuma combinação de programa e máquina pode implementá-la.

### f. Suponha que um agente selecione sua ação uniformemente ao acaso do conjunto de ações possíveis. Existe um ambiente de tarefa determinista em que esse agente é racional.

- Julgamento: **Verdadeiro**
- Justificativa: Um agente que sorteia ações aleatórias com distribuição uniforme será perfeitamente racional em qualquer ambiente determinista cujas ações disponíveis conduzam exatamente ao mesmo valor máximo da medida de desempenho (todas as ações são igualmente ótimas).
- Exemplo / Contraexemplo: Um ambiente determinista no qual o agente está diante de três portas e atrás de qualquer uma delas existe a mesma recompensa de 100 pontos (ou um cofre destrancado onde acionar a alavanca A ou a alavanca B concede o mesmo resultado ótimo). Sortear uniformemente entre A e B atinge a utilidade máxima esperada, satisfazendo a definição de agente racional.

### g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.

- Julgamento: **Verdadeiro**
- Justificativa: A racionalidade depende da relação entre percepções, ações e medida de desempenho em cada contexto. Se a política de tomada de decisão do agente for robusta ou se as distinções entre os ambientes não afetarem a eficácia das regras empregadas, ele será racional em ambos.
- Exemplo / Contraexemplo: O agente aspirador reativo com a política "se [Sujo], aspire; se [Limpo], mova-se para o outro quadrado". Ele é perfeitamente racional em um ambiente com 2 quadrados onde ambos começam sujos, e também em um ambiente com 2 quadrados onde o quadrado B nunca acumula sujeira (pois ele limpará A, irá para B, verificará que está limpo e retornará para A, mantendo ambos limpos).

### h. Todo agente é racional em um ambiente não observável.

- Julgamento: **Falso**
- Justificativa: Conforme a Seção 2.3.2, a ausência de percepções imediatas (ambiente inobservável) não anula o impacto das ações do agente sobre o estado do mundo nem suspende a medida de desempenho. Um agente racional em ambiente inobservável projeta um plano em malha aberta (plano conformante) baseado no conhecimento prévio do ambiente para atingir a meta, enquanto um agente mal projetado executará ações ineficazes ou destrutivas.
- Exemplo / Contraexemplo: Um agente aspirador em uma sala totalmente escura (sem sensores). O agente A executa a sequência fixa calculada [Aspirar, Direita, Aspirar], garantindo que ambos os cômodos fiquem limpos. O agente B executa repetidamente [Esquerda, Esquerda, Esquerda], batendo na parede sem aspirar nada. O agente B é irracional; logo, nem todo agente é racional nesse ambiente.

### i. Um agente jogador de pôquer perfeitamente racional nunca perde.

- Julgamento: **Falso**
- Justificativa: Conforme salientado na Seção 2.2.3, a racionalidade não se confunde com perfeição ou infalibilidade. O pôquer é um jogo estocástico (embaralhamento aleatório de cartas) e parcialmente observável (cartas dos oponentes ocultas). A racionalidade maximiza o ganho esperado a longo prazo, mas eventos aleatórios desfavoráveis podem levar à perda de mãos ou partidas individuais.
- Exemplo / Contraexemplo: Um agente faz uma aposta matematicamente correta segurando um par de Ases contra um par de 2 do oponente no pré-flop (tendo mais de 80% de chance teórica de vitória). Se o oponente acertar uma trinca improvável na última carta (river), o agente perderá a aposta, mesmo tendo agido com estrita racionalidade.

## Exercício 2.4
Para cada caso, delimite o agente, preencha o PEAS e justifique todas as classificações. Considere Titã como cenário hipotético do exercício.

### Caso 1 — Jogar futebol.

- Agente analisado: Robô futebolista autônomo (agente individual integrante da equipe).
- Objetivo e hipóteses: Marcar gols no time adversário, defender o próprio gol e cooperar taticamente com os companheiros de equipe em campo oficial sob as regras da FIFA/RoboCup.
- P — Medida de desempenho: Saldo de gols (gols a favor vs. contra), vitória na partida, índice de acerto em passes, posse de bola e obediência às regras (minimização de faltas/cartões).
- E — Ambiente: Campo de futebol gramado com demarcações, traves, bola, 10 companheiros de equipe, 11 adversários, arbitragem e intempéries climáticas.
- A — Atuadores: Servomotores de locomoção nas articulações/pernas ou rodas motrizes, mecanismo de chute/passe, rotação de cabeça/câmera e alto-falante/rádio para comunicação com a equipe.
- S — Sensores: Câmeras com visão computacional, sensor ultrassônico/LiDAR de proximidade, unidade de medição inercial (giroscópio e acelerômetro) e receptor de rádio/Wi-Fi tático.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente possui ângulo de visão limitado pelas câmeras e enfrenta oclusões geradas pelos corpos de outros jogadores em disputa. |
| Número de agentes | Multiagente (cooperativo e competitivo) | Cooperativo em relação aos companheiros da mesma equipe e estritamente competitivo em relação aos adversários. |
| Previsibilidade | Estocástico | As ações físicas sofrem interferência de atrito na grama, ventos e, primordialmente, do comportamento não determinístico dos outros 21 jogadores. |
| Dependência entre decisões | Sequencial | Um passe mal calculado no primeiro minuto altera o posicionamento tático e condiciona as jogadas subsequentes da partida. |
| Mudança durante a decisão | Dinâmico | A bola e os adversários continuam se deslocando pelo campo continuamente enquanto o algoritmo do agente calcula sua próxima ação. |
| Natureza dos elementos | Contínuo | Posição espacial, velocidade de corrida, ângulo de chute e passagem do tempo variam de forma contínua. |
| Conhecimento do funcionamento | Conhecido | As regras formais do jogo de futebol e as leis da cinemática física são previamente programadas e conhecidas pelo agente. |

### Caso 2 — Explorar os oceanos subterrâneos de Titã.

- Agente analisado: Sonda robótica submarina autônoma de exploração planetária.
- Objetivo e hipóteses: Mapear a bacia oceânica sob a crosta de gelo de Titã (lua de Saturno), recolher amostras hidrotermais e sobreviver a ambientes de alta pressão e temperaturas extremas sem controle em tempo real da Terra.
- P — Medida de desempenho: Volume de área mapeada, diversidade e relevância das amostras coletadas, integridade estrutural/autopreservação do veículo e quantidade de dados transmitidos.
- E — Ambiente: Oceano subsuperficial alienígena líquido (água/amônia), fendas e fontes hidrotermais, crosta superior de gelo, correntes de convecção e leito rochoso.
- A — Atuadores: Hélices e propulsores direcionais de navegação, braço articulado coletor de amostras, lastros de controle de flutuabilidade e antena transmissora acústica/RF.
- S — Sensores: Sonar ativo/passivo 3D, espectrômetro de massa químico, termômetros, manômetros de pressão hidrostática, altímetro batimétrico e sensores de tensão no casco.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | A propagação do sonar tem alcance finito e o fluido oceânico denso impõe limitações visuais e de detecção a longas distâncias. |
| Número de agentes | Agente único | A sonda opera sozinha no ambiente oceânico (possíveis microrganismos seriam propriedades bioquímicas do meio ambiente, não agentes estratégicos). |
| Previsibilidade | Estocástico | Correntes térmicas submarinas turbulentas e desprendimentos de placas de gelo produzem efeitos físicos não determinísticos. |
| Dependência entre decisões | Sequencial | O gerenciamento do consumo de bateria e as rotas exploratórias escolhidas determinam quais regiões poderão ser alcançadas no futuro. |
| Mudança durante a decisão | Dinâmico | O fluxo hidrotermal e as correntes submarinas movem a sonda e o ambiente circundante enquanto seu computador processa os planos. |
| Natureza dos elementos | Contínuo | Pressão, temperatura, vetor de aceleração, coordenadas tridimensionais e tempo são grandezas físicas contínuas. |
| Conhecimento do funcionamento | Desconhecido | As propriedades geológicas locais, a composição química precisa e a topografia do oceano extraterrestre precisam ser descobertas na prática. |

### Caso 3 — Comprar livros usados de IA na Internet.

- Agente analisado: Softbot (agente de software) comprador em plataformas de e-commerce e sebos online.
- Objetivo e hipóteses: Localizar e efetivar a compra de títulos específicos de Inteligência Artificial pelo menor custo total (preço + frete) e no melhor estado de conservação possível, respeitando o teto orçamentário.
- P — Medida de desempenho: Economia financeira obtida em relação ao orçamento limite, integridade/estado de conservação do exemplar recebido, velocidade da entrega e confiabilidade do vendedor.
- E — Ambiente: Plataformas de venda online (Amazon, eBay, Estante Virtual), servidores web com bancos de dados de ofertas, correios/APIs de frete e múltiplos vendedores/compradores.
- A — Atuadores: Envio de requisições de rede HTTP/HTTPS (preenchimento de formulários de compra, envio de lances/ofertas de preço, autorização de pagamento via cartão/PIX).
- S — Sensores: Leitura de respostas HTTP/código HTML e dados JSON das páginas de resultados, índices de preço, avaliações dos vendedores e confirmações de transação por e-mail/API.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente tem acesso aos dados textuais e fotos da oferta, mas não consegue inspecionar o livro fisicamente nem conhecer os lances máximos de concorrentes ou estoques ocultos. |
| Número de agentes | Multiagente competitivo | Outros usuários e robôs concorrem ativamente pelos mesmos exemplares com estoques limitados. |
| Previsibilidade | Estocástico | Uma oferta pode ser arrematada por outro comprador no milissegundo anterior à finalização, ou o vendedor pode cancelar o anúncio por falta de estoque. |
| Dependência entre decisões | Sequencial | Efetivar a compra de um livro gasta o saldo financeiro disponível e impede a compra de outra oportunidade melhor que venha a surgir em seguida. |
| Mudança durante a decisão | Semidinâmico | As listagens nos servidores podem sofrer alterações ou esgotar enquanto o agente avalia se deve fechar o pedido (no escopo da transação web imediata, comporta-se frequentemente como semidinâmico). |
| Natureza dos elementos | Discreto | Páginas, preços quantizados em centavos, unidades inteiras de livros e botões/links de interface compõem estados e ações discretos. |
| Conhecimento do funcionamento | Conhecido | As regras formais de navegação, carrinho de compras e protocolos de pagamento de e-commerce são previamente estabelecidos. |

### Caso 4 — Jogar uma partida de tênis.

- Agente analisado: Robô tenista autônomo competidor.
- Objetivo e hipóteses: Vencer a partida contra um oponente humano ou robótico, rebatendo a bola de modo a colocá-la dentro da quadra adversária e fora do alcance de devolução do oponente.
- P — Medida de desempenho: Vitórias em sets e games, pontos marcados, percentual de acerto de primeiro saque, minimização de erros não forçados e tempo de reação.
- E — Ambiente: Quadra oficial de tênis (piso rápido ou saibro), rede, bola regulamentar, raquete, adversário em disputa e condições de vento/luminosidade.
- A — Atuadores: Mecanismo robótico de movimentação na base (rodas de alta tração ou pernas articuladas) e manipulador mecânico para empunhar e desferir golpes com a raquete.
- S — Sensores: Câmeras estereoscópicas de alta taxa de quadros (rastreamento 3D da bola e do rival), encoders de rotação nas articulações mecânicas e sensor de impacto na raquete.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente enxerga a quadra e a bola, mas o efeito de rotação (spin) impresso na bola, microirregularidades no piso e as intenções táticas imediatas do oponente são incertos. |
| Número de agentes | Multiagente competitivo | O adversário executa ações deliberadas para explorar as fraquezas do robô e fazê-lo errar. |
| Previsibilidade | Estocástico | O quique da bola no solo, variações aerodinâmicas de vento e microdesvios na corda da raquete inserem variações probabilísticas. |
| Dependência entre decisões | Sequencial | A profundidade e a velocidade com que o robô rebate uma bola determinam se ele terá tempo hábil de se posicionar para a bola seguinte. |
| Mudança durante a decisão | Dinâmico | A bola cruza a rede em milissegundos; qualquer hesitação do algoritmo enquanto a bola se aproxima acarreta ponto perdido. |
| Natureza dos elementos | Contínuo | Posição e velocidade da bola, ângulos articulares do braço mecânico e intervalos de tempo são contínuos. |
| Conhecimento do funcionamento | Conhecido | As regras de pontuação da ITF e as equações da mecânica clássica balística são pré-estabelecidas e conhecidas. |

### Caso 5 — Praticar tênis contra uma parede.

- Agente analisado: Robô praticante de golpes contínuos contra parede de treino.
- Objetivo e hipóteses: Sustentar uma sequência prolongada de rebatidas consecutivas na parede, mantendo a bola em jogo com regularidade técnica e equilíbrio postural.
- P — Medida de desempenho: Quantidade ininterrupta de devoluções bem-sucedidas contra a parede, centralização dos golpes na faixa-alvo e regularidade temporal do ritmo de treino.
- E — Ambiente: Parede lisa de rebote, quadra de treino delimitada, bola de tênis e raquete acoplada.
- A — Atuadores: Base motora de reposicionamento lateral/frontal e atuador articulado para armação e desfecho do golpe da raquete.
- S — Sensores: Câmeras visuais de alta frequência para interceptação da trajetória da bola e sensores táteis no encordoamento da raquete.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | A trajetória no ar é visível, mas a deformação milimétrica da borracha da bola e microrugosidades na superfície da parede não são percebidas diretamente. |
| Número de agentes | Agente único | A parede é um componente puramente físico e estático do ambiente; não há agente antagônico operando contra o robô. |
| Previsibilidade | Estocástico | Embora altamente regular se comparado a um adversário vivo, pequenas imperfeições no rebote da parede ou desgaste da bola mantêm o ambiente estocástico na realidade física. |
| Dependência entre decisões | Sequencial | A potência e o ângulo do golpe atual impactam diretamente o tempo de reação e a posição em que a bola retornará para a próxima batida. |
| Mudança durante a decisão | Dinâmico | A bola volta em voo direto para o robô enquanto ele ajusta sua postura de impacto. |
| Natureza dos elementos | Contínuo | Trajetórias tridimensionais, forças de aceleração e coordenadas espaciais variam em intervalos contínuos. |
| Conhecimento do funcionamento | Conhecido | As leis da física de reflexão de impacto elástico e mecânica de corpos rígidos são conhecidas. |

### Caso 6 — Realizar um salto de altura.

- Agente analisado: Robô saltador atleta (executante da técnica Fosbury Flop).
- Objetivo e hipóteses: Transpor com sucesso o sarrafo horizontal apoiado na maior altura permitida sem derrubá-lo, aterrissando adequadamente no colchão regulamentar.
- P — Medida de desempenho: Altura máxima superada em metros sem derrubar a barra, validade da chamada de impulsão (sem queima da linha de salto) e segurança no pouso.
- E — Ambiente: Pista sintética de salto, área de decolagem, barra/sarrafo apoiada sobre postes milimetrados e colchão de amortecimento.
- A — Atuadores: Pistões hidráulicos/elétricos e servomotores nas pernas para impulsão vertical e nos membros superiores para flexão de coluna dorsal.
- S — Sensores: Câmeras e sensor LiDAR frontal para medição da distância até o obstáculo, sensores inerciais (IMU) para controle de rotação no ar e sensores de pressão nos pés mecânicos.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Completamente observável | A posição e altura da barra, a distância até o ponto de impulsão e as condições da pista estão inteiramente ao alcance dos sensores antes e durante o salto. |
| Número de agentes | Agente único | A tentativa de salto é individual; não há outros concorrentes interferindo na pista no momento da execução. |
| Previsibilidade | Determinístico | Desprezando rajadas residuais de microvento em ginásio coberto, o movimento é regido rigorosamente pelas equações de balística e gravidade a partir do impulso gerado. |
| Dependência entre decisões | Sequencial | A velocidade da passada na corrida em curva determina com precisão o momento e a transferência de força no instante da decolagem. |
| Mudança durante a decisão | Dinâmico | Uma vez iniciada a corrida e o salto, o corpo do robô desloca-se a grande velocidade, demandando controle contínuo durante a fase de voo. |
| Natureza dos elementos | Contínuo | Posição, velocidade, torques articulares e aceleração variam de maneira contínua no espaço e no tempo. |
| Conhecimento do funcionamento | Conhecido | As leis da gravidade e dinâmica corporal newtoniana são inteiramente descritas por equações físicas consolidadas. |

### Caso 7 — Participar de um leilão de um item, realizando lances.

- Agente analisado: Softbot licitante em pregão eletrônico.
- Objetivo e hipóteses: Arrematar um lote/item pelo menor valor final possível, assegurando que o lance nunca ultrapasse o limite máximo estipulado pelo usuário proprietário.
- P — Medida de desempenho: Vitória no leilão, margem de economia (valor de reserva do usuário menos o valor efetivamente pago) e prevenção do fenômeno da maldição do vencedor (winner's curse).
- E — Ambiente: Servidor web da casa de leilões, cronômetro de contagem regressiva, histórico de lances e concorrentes online.
- A — Atuadores: Envio de requisições de submissão de lance financeiro via rede ou comando de desistência da disputa.
- S — Sensores: Leitura dos dados da página/API do pregão (lance mais alto no momento, tempo restante no relógio, valor mínimo de incremento e estado do pregão).

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente visualiza os lances tornados públicos, mas desconhece os limites financeiros de reserva e as estratégias confidenciais dos concorrentes. |
| Número de agentes | Multiagente competitivo | Múltiplos licitantes disputam o mesmo lote e agem ativamente para tentar arrematar o item ou elevar o custo. |
| Previsibilidade | Estocástico | As decisões de lances de concorrentes externos (humanos ou outros robôs) introduzem incerteza probabilística quanto ao próximo valor a ser superado. |
| Dependência entre decisões | Sequencial | Um lance ofertado agora força uma reação dos competidores e fixa o valor mínimo para a rodada seguinte. |
| Mudança durante a decisão | Dinâmico | O cronômetro de encerramento do leilão diminui continuamente enquanto o agente calcula sua oferta; se o tempo esgotar sem ação, a oportunidade é perdida. |
| Natureza dos elementos | Discreto | Os lances avançam em intervalos monetários quantizados e as rodadas/turnos de lance formam eventos discretos bem definidos. |
| Conhecimento do funcionamento | Conhecido | O regulamento formal do leilão (leilão inglês, holandês, de segundo preço ou envelope fechado) é completamente explícito e padronizado. |

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

A diferença essencial entre os dois cenários é o **Número de Agentes**. Na partida competitiva, o robô atua em um ambiente multiagente competitivo, onde o adversário toma ações calculadas para desestabilizá-lo, obrigando o agente a incorporar raciocínio estratégico sobre as intenções alheias (teoria dos jogos). No treino contra a parede, o ambiente é de agente único: a parede é um obstáculo físico passivo governado apenas pelas leis mecânicas de reflexão elástica, sem vontade própria nem comportamento estratégico.

**2. Por que comprar livros usados pode exigir decisões com informações incompletas?**

A observabilidade parcial na compra de livros decorre de dois fatores principais: assimetria na avaliação do objeto (fotos e descrições textuais podem ocultar danos físicos, mofo, grifos ou páginas rasgadas) e incerteza no canal de fornecimento (falta de acesso ao estoque real do vendedor, idoneidade na postagem e riscos logísticos nos correios). Por isso, o agente racional precisa ponderar a reputação do vendedor e embutir margens de segurança no preço para cobrir possíveis discrepâncias.

**3. Como outros agentes influenciam futebol e leilões?**

No futebol, a influência dos outros agentes se manifesta de forma mista (cooperação em equipe e competição física direta) em um ambiente contínuo e altamente sincronizado no espaço físico real, exigindo respostas reflexivas e planejamento tático espacial em milissegundos. No leilão, a interação é puramente competitiva e informacional/estratégica, em que o agente adversário não disputa contato físico, mas sim utilidade econômica: cada oferta submetida altera o patamar de preço e o estado financeiro de todos os envolvidos, desencadeando táticas de blefe, desistência e ofertas no último instante (sniping).

## Exercício 2.5
Defina cada termo com suas palavras em duas a quatro linhas e apresente um exemplo.

### Agente

- Definição: Qualquer entidade capaz de perceber seu ambiente circundante por meio de sensores e de agir sobre esse ambiente por intermédio de atuadores, direcionando seu comportamento de forma a atender a determinado propósito ou projeto.
- Exemplo: Um termostato digital que detecta a temperatura ambiente por um termistor e aciona o relé que liga o compressor do ar-condicionado.

### Função de agente

- Definição: Mapeamento puramente matemático e abstrato que formaliza a conduta do agente ao associar qualquer sequência histórica completa de percepções (P\*) a uma ação específica do conjunto de ações (A).
- Exemplo: A relação formal que dita que, se a sequência de leituras recebidas pelo aspirador for [(A, Limpo), (B, Sujo)], a ação mapeada será Aspirar.

### Programa de agente

- Definição: A implementação concreta em código de software que executa sobre uma arquitetura física para realizar na prática a computação da função de agente, recebendo apenas a percepção imediatamente atual e gerando um comando para os atuadores.
- Exemplo: Um script em linguagem Python executado em um microcontrolador que lê dados da porta serial e emite comandos via pinos GPIO para motores de passo.

### Racionalidade

- Definição: A propriedade do agente de escolher, a cada instante, a ação que maximiza o valor esperado de sua medida de desempenho, considerando a sequência de percepções recebida até o momento e o conhecimento prévio incorporado sobre o ambiente.
- Exemplo: Um aplicativo de navegação por GPS que recalcula dinamicamente a rota do veículo ao identificar uma via obstruída, minimizando o tempo total de viagem até o destino.

### Autonomia

- Definição: A característica do agente cujo comportamento decorre primordialmente de sua própria experiência e aprendizado com o ambiente, compensando conhecimentos iniciais parciais ou desatualizados fornecidos originalmente por seu projetista.
- Exemplo: Um robô aspirador que constrói e atualiza dinamicamente o mapa geométrico dos cômodos da residência ao longo dos dias, em vez de depender de uma planta fixa pré-carregada na memória.

### Agente reativo

- Definição: Arquitetura de agente que seleciona ações com base unicamente na percepção sensorial imediata atual, operando por regras diretas do tipo condição-ação (se-então), sem depender do histórico de percepções ou manter memória interna de estados anteriores.
- Exemplo: Um sensor automático de porta deslizante de loja que emite o comando de abertura no instante em que o feixe infravermelho registra presença de um cliente.

### Agente baseado em modelo

- Definição: Agente que sustenta uma representação interna de memória (estado interno) para rastrear aspectos do mundo que não são visíveis no momento atual, valendo-se de conhecimentos sobre a evolução do mundo e os efeitos das próprias ações.
- Exemplo: Um sistema de direção autônoma que memoriza a presença de uma moto no ponto cego do retrovisor e evita mudar de faixa, mesmo quando ela fica encoberta pelo ângulo morto da câmera.

### Agente baseado em objetivos

- Definição: Agente que alia o estado interno a uma descrição explícita de uma meta ou situação desejada, selecionando e combinando sequências futuras de ações por meio de algoritmos de busca e planejamento com o propósito expresso de alcançar essa meta.
- Exemplo: Um robô explorador de depósito que traça um trajeto de curvas e corredores para alcançar a prateleira específica indicada na ordem de separação de pedidos.

### Agente baseado em utilidade

- Definição: Agente que utiliza uma função contínua de utilidade para quantificar numericamente a qualidade ou preferência entre múltiplos estados possíveis, permitindo mediar equilíbrios entre objetivos conflitantes sob condições de incerteza.
- Exemplo: O sistema de controle de voo de um avião que pondera continuamente consumo de combustível, tempo de voo e nível de turbulência dos passageiros para definir a altitude de cruzeiro ideal.

### Agente com aprendizagem

- Definição: Estrutura organizada em quatro componentes (elemento de desempenho, crítico, elemento de aprendizado e gerador de problemas) que permite ao agente modificar seus componentes internos e melhorar seu rendimento a partir da experiência prática.
- Exemplo: Um software de xadrez que ajusta os pesos de avaliação das peças após cada partida concluída e testa novas aberturas para expandir seu repertório tático.

## Síntese com autômatos
Escolha um caso do item 2.4. Apresente três estados internos, três percepções, três ações e duas regras no formato estado atual + percepção → próximo estado e ação. Explique como estados internos representam informação passada e cite uma limitação da simplificação.

**Cenário Escolhido: Caso 5 — Praticar Tênis contra uma Parede (Robô Praticante)**

**1. Elementos Formais do Autômato de Estados Finitos:**

**Conjunto de Estados Internos (Q):**
- q₀: *Aguardando_Rebote* — robô na posição-base central acompanhando a aproximação da bola vinda da parede.
- q₁: *Armando_Golpe* — robô posicionando o braço mecânico e ajustando a passada em direção à trajetória de impacto.
- q₂: *Recuperando_Posicao* — golpe concluído; robô retornando à posição neutra da quadra para restabelecer o equilíbrio.

**Alfabeto de Percepções de Entrada (Σ):**
- p₁: *Bola_Na_Trajetoria_Alvo* — sistema de visão detecta a bola retornando em rota favorável para devolução.
- p₂: *Impacto_Confirmado* — sensor piezoelétrico do encordoamento da raquete acusa contato mecânico com a bola.
- p₃: *Falha_Ou_Dois_Quiques* — bola ultrapassa o limite da quadra ou toca o solo duas vezes consecutivas.

**Alfabeto de Ações de Saída (A):**
- a₁: *Posicionar_Base_E_Armar_Raquete*
- a₂: *Desferir_Swing_Rebatida*
- a₃: *Recuar_Centro_E_Resetar_Postura*

**2. Regras de Transição (δ: Q × Σ → Q × A):**

**Regra 1:** δ(q₀, p₁) = (q₁, a₁)
Se o robô está em *Aguardando_Rebote* (q₀) e a percepção acusa *Bola_Na_Trajetoria_Alvo* (p₁), o agente executa a ação de *Posicionar_Base_E_Armar_Raquete* (a₁) e transita para o estado *Armando_Golpe* (q₁).

**Regra 2:** δ(q₁, p₂) = (q₂, a₂)
Se o robô está em *Armando_Golpe* (q₁) e percebe o *Impacto_Confirmado* (p₂), ele conclui o movimento com a ação *Desferir_Swing_Rebatida* (a₂) e migra para o estado *Recuperando_Posicao* (q₂).

**3. Como o estado interno representa informação passada e limitações da simplificação:**

**Representação da informação passada:** O estado interno funciona como uma síntese compacta do histórico anterior de percepções recebidas pelo agente. O robô não precisa manter na memória todos os milhares de quadros de vídeo capturados pelas câmeras nos últimos segundos: estar no estado interno q₁ sintetiza que, instantes atrás, a bola já foi lançada contra a parede, já ricocheteou e já alcançou a faixa de abordagem correta. É essa retenção de estado que viabiliza a execução de ações coordenadas em cadeia temporal em ambientes parcialmente observáveis.

**Limitação da simplificação por autômatos de estados finitos:** A dinâmica física do tênis envolve grandezas cinemáticas contínuas no espaço e no tempo (ângulos infinitesimais na articulação do pulso, velocidade angular de spin, milissegundos exatos de impacto e resistência do ar). A abstração por autômatos de estados finitos e discretos sofre de perda de sensibilidade aos parâmetros contínuos e, conforme exposto na Seção 2.4.7 do livro, acarreta uma severa explosão combinatória: discretizar cada variação de trajetória exigiria uma quantidade proibitiva de estados finitos (na ordem de 10³⁸ páginas de regras), tornando a modelagem atômica rígida e inadequada para o controle cinemático fino em tempo real.

## Entrega e avaliação
Confira: identificação; nove análises no item 2.3; sete casos completos no item 2.4; dez conceitos no item 2.5; síntese; referências.
Nome sugerido: `DeividCerqueira_Atividade_AgentesInteligentes`. Prazo e envio conforme orientação da professora.

| Critério | Atividade avaliativa (1,0 ponto) A2 |
|---|---:|
| Item 2.3 — correção e argumentação | 30% |
| Item 2.4 — PEAS e classificação justificada | 40% |
| Item 2.5 — precisão conceitual e exemplos | 20% |
| Síntese, organização e referências | 10% |

## Referências
Material-base: Capítulo 2 — Agentes inteligentes, disponibilizado para a aula de 19/10/2026.

1. RUSSELL, Stuart; NORVIG, Peter. *Inteligência Artificial: Uma Abordagem Moderna*. 3. ed. Rio de Janeiro: Elsevier, 2013 / 4. ed. Rio de Janeiro: GEN LTC, 2022. Capítulo 2: Agentes Inteligentes.
2. HOPCROFT, John E.; MOTWANI, Rajeev; ULLMAN, Jeffrey D. *Introdução à Teoria de Autômatos, Linguagens e Computação*. Rio de Janeiro: Elsevier, 2002.
3. SUTTON, Richard S.; BARTO, Andrew G. *Reinforcement Learning: An Introduction*. 2. ed. Cambridge: MIT Press, 2018.
