# Sugestões de temas para o seu projeto

Abaixo seguem algumas sugestões organizaras em quatro blocos:

1) Focado em casos de caso de uso 
2) IA (NLP)
3) IA (Visão Computacional)
4) IA (Aprendizado por Reforço)


Entrega: 
1) código-fonte
2) Relatório 
3) Vídeo explicativo



---
************** **OBSERVAÇÃO: NÃO FIQUEM LIMITADOS A ESTES CASOS.... TRATA-SE APENAS DE IDEIAS** ***************
---


# Tabela Resumida – Casos de Uso de Algoritmos Evolutivos (de modo geral)


 **Área**                       | **Caso de Uso**                  | **Descrição Aplicável**                           | **Link p/ Pesquisa**                                                                                     |
| ------------------------------ | -------------------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Finanças**                   | Otimização de Portfólio          | Balancear risco e retorno em investimentos.       | [Yahoo Finance Datasets](https://finance.yahoo.com)                                                      |
| Finanças                       | Precificação de Derivativos      | Calibrar modelos de opções complexas.             | [Investopedia – Option Pricing](https://www.investopedia.com/terms/o/optionpricingtheory.asp)            |
| Finanças                       | Detecção de Fraudes              | Evoluir regras para flagrar transações suspeitas. | [Kaggle – Credit Card Fraud](https://www.kaggle.com/mlg-ulb/creditcardfraud)                             |
| **Gestão/Operações**           | Escalonamento de Produção        | Otimizar uso de máquinas e pessoas.               | [Job Shop Scheduling Data](https://people.brunel.ac.uk/~mastjjb/jeb/orlib/jobshopinfo.html)              |
| Gestão                         | Roteamento de Entregas           | Otimizar rotas de veículos (logística urbana).    | [VRP Instances](http://vrp.atd-lab.inf.puc-rio.br/index.php/en/)                                         |
| Gestão                         | Escalas de Trabalho (RH)         | Criar escalas de médicos, call centers, etc.      | [Nurse Rostering Benchmark](https://www.cs.nott.ac.uk/~pszqiu/nrp/)                                      |
| **Marketing**                  | Otimização de Campanhas Digitais | Distribuir orçamento maximizando ROI.             | [Kaggle – Marketing Campaign](https://www.kaggle.com/datasets/rodsaldanha/arketing-campaign)             |
| Marketing                      | Precificação Dinâmica            | Ajustar preços em e-commerce.                     | [Kaggle – Retail Pricing](https://www.kaggle.com/datasets/bananadiegos/retail-price-optimization)        |
| Marketing                      | Segmentação de Clientes          | Evoluir regras para agrupar clientes em perfis.   | [Kaggle – Customer Segmentation](https://www.kaggle.com/datasets/kaushiksuresh147/customer-segmentation) |
| **Tecnologia**                 | AutoML Evolutivo                 | Evoluir pipelines de ML.                          | [TPOT Library](https://epistasislab.github.io/tpot/)                                                     |
| Tecnologia                     | Neuroevolução (NEAT)             | Evoluir topologias de redes neurais.              | [NEAT-Python](https://neat-python.readthedocs.io/en/latest/)                                             |
| Tecnologia                     | Detecção de Anomalias em TI      | Evoluir regras p/ monitorar redes e servidores.   | [Kaggle – Network Intrusion](https://www.kaggle.com/datasets/deftech/intrusion-detection)                |
| Tecnologia                     | Robótica Industrial              | Evoluir trajetórias de robôs em fábricas.         | [OpenAI Gym Robotics](https://gym.openai.com/envs/#robotics)                                             |
| **Saúde**                      | Previsão de Doenças Crônicas     | Seleção de exames relevantes (diabetes, coração). | [UCI Diabetes Dataset](https://www.kaggle.com/datasets/mathchi/diabetes-data-set)                        |
| Saúde                          | Planejamento de Radioterapia     | Otimizar dose em tumores vs tecidos saudáveis.    | [ICRU Radiotherapy Resources](https://icru.org/home/)                                                    |
| Saúde                          | Agendamento Hospitalar           | Escalas de médicos/enfermeiros com restrições.    | [Nurse Rostering Benchmark](https://www.cs.nott.ac.uk/~pszqiu/nrp/)                                      |
| Saúde                          | Genômica & Biomarcadores         | Seleção de genes relevantes p/ diagnóstico.       | [NCBI Gene Expression Omnibus](https://www.ncbi.nlm.nih.gov/geo/)                                        |
| Saúde                          | Diagnóstico via Imagem Médica    | Evolução de parâmetros p/ segmentação de tumores. | [NIH Chest X-ray Dataset](https://www.kaggle.com/datasets/nih-chest-xrays/data)                          |
| Saúde                          | Modelagem Epidemiológica         | Ajuste de modelos de propagação de doenças.       | [COVID-19 Data](https://ourworldindata.org/covid-deaths)                                                 |
| **Energia & Sustentabilidade** | Planejamento de Parques Eólicos  | Otimizar posicionamento de turbinas.              | [Wind Energy Data](https://www.nrel.gov/grid/wind-toolkit.html)                                          |


---
# Em NLP

# **1. Seleção de Features / Palavras com Algoritmos Evolutivos**

* **Ideia**: em vez de usar todas as palavras ou embeddings, usar AE para selecionar subconjuntos que melhorem acurácia e reduzam custo.
* **Aplicação de mercado**: análise de sentimento (reviews, redes sociais), classificação de tickets de suporte, detecção de spam.
* **Dataset sugerido**:

  * [IMDb Reviews](https://ai.stanford.edu/~amaas/data/sentiment/) (positivo/negativo)
  * [20 Newsgroups](https://scikit-learn.org/0.19/datasets/twenty_newsgroups.html)
* **Fitness function**: acurácia (ou F1) do classificador treinado com as features selecionadas.

---

# **2. Geração de Regras Interpretáveis**

* **Ideia**: evoluir regras do tipo `SE (texto contém X) E (não contém Y) ENTÃO classe=Z`.
* **Aplicação de mercado**: compliance em documentos legais, triagem de e-mails corporativos, classificação em áreas reguladas (finanças/saúde) onde interpretabilidade é essencial.
* **Dataset sugerido**:

  * [Enron Email Dataset](https://www.cs.cmu.edu/~enron/) (classificação de e-mails por tema).
  * [SpamAssassin](https://spamassassin.apache.org/publiccorpus/) (spam/ham).
* **Fitness function**: acurácia + simplicidade da regra (multiobjetivo: performance x interpretabilidade).

---

# **3. Evolução de Prompts (Prompt Optimization)**

* **Ideia**: usar AE para evoluir instruções (prompts) que maximizem a performance de LLMs em tarefas específicas.
* **Aplicação de mercado**:

  * Otimização de **chatbots** para atendimento ao cliente.
  * Melhorar **resumos automáticos** de textos corporativos.
  * Otimizar **Q&A** em bases de conhecimento.
* **Dataset sugerido**:

  * [SQuAD v2](https://rajpurkar.github.io/SQuAD-explorer/) (Perguntas e Respostas).
  * [CNN/DailyMail Summarization](https://github.com/abisee/cnn-dailymail) (Resumos).
* **Fitness function**:

  * F1 ou BLEU (Q&A e tradução).
  * ROUGE (resumos).
  * Ou até métricas de “satisfação do usuário” simulada.





# **Em visão computacional**



## **1. Seleção de Features em Imagens**

**Descrição:**
Algoritmos evolutivos são usados para **escolher subconjuntos de características (features) de imagens** que maximizem a performance de modelos de CV, reduzindo dimensionalidade e custo computacional.

**Aplicações de Mercado:**

* Diagnóstico médico: selecionar os pixels/descritores mais importantes para detecção de lesões em radiografias ou tomografias.
* Inspeção industrial: identificar defeitos em peças sem analisar toda a imagem.

**Dataset Sugerido:**

* [MNIST](http://yann.lecun.com/exdb/mnist/) — dígitos manuscritos simples para testes iniciais.
* [ISIC](https://www.isic-archive.com/) — imagens de pele para classificação de lesões.

**Fitness Function:**

* Acurácia do classificador treinado usando apenas as features selecionadas.
* Pode incluir penalização para número de features (objetivo multiobjetivo: performance x simplicidade).

**Implementação Prática:**

* Representação: binária (1 = feature incluída, 0 = excluída).
* População inicial: conjunto de vetores binários aleatórios.
* Operadores: crossover e mutação binária.

---

## **2. Evolução de Arquiteturas de CNNs (Neuroevolution)**

**Descrição:**
Algoritmos evolutivos criam **topologias de redes neurais convolucionais (CNNs)**, definindo camadas, filtros e conexões automaticamente.

**Aplicações de Mercado:**

* Sistemas de vigilância: reconhecer objetos ou pessoas automaticamente.
* Agricultura: classificar frutas, plantas ou detectar pragas.
* Indústria: inspeção visual de produtos em linha de produção.

**Dataset Sugerido:**

* [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html) — 10 classes de imagens pequenas (aviação, automóveis, animais).
* [Fruit-360](https://www.kaggle.com/moltean/fruits) — frutas para classificação visual.

**Fitness Function:**

* Acurácia de validação da rede neural.
* Pode ser multiobjetivo: acurácia + número de parâmetros (para eficiência).

**Implementação Prática:**

* Representação: inteira ou real (número de filtros, tamanho do kernel, camadas).
* População inicial: redes simples aleatórias dentro de limites predefinidos.
* Operadores: mutação altera número de filtros/camadas, crossover combina partes de duas redes.


## **3. Segmentação de Imagens por Evolução de Regras**

**Descrição:**
AEs evoluem **regras ou expressões matemáticas** que definem regiões de interesse em imagens. Cada indivíduo representa uma estratégia de segmentação.

**Aplicações de Mercado:**

* Medicina: delimitar tumores em exames de imagem (MRI, CT).
* Satélites: identificar diferentes tipos de terreno (solo, água, vegetação).
* Agricultura de precisão: mapear áreas com diferentes tipos de plantas.

**Dataset Sugerido:**

* [DRIVE](https://drive.grand-challenge.org/) — segmentação de vasos sanguíneos em retina.
* [Cityscapes](https://www.cityscapes-dataset.com/) — segmentação urbana de ruas e objetos.

**Fitness Function:**

* Métricas de segmentação: Intersection over Union (IoU) ou Dice score.
* Pode incluir penalização por complexidade da regra.

**Implementação Prática:**

* Representação: árvore ou vetor de parâmetros definindo filtros e thresholds.
* População inicial: combinações aleatórias de filtros/thresholds.
* Operadores: mutação altera thresholds, crossover combina regras.

---

## **4. Evolução de Filtros / Pré-processamento de Imagens**

**Descrição:**
AEs evoluem **filtros ou pipelines de pré-processamento** para melhorar a qualidade das imagens antes da tarefa final de CV.

**Aplicações de Mercado:**

* Segurança: melhorar imagens de câmeras em baixa iluminação.
* Medicina: realce de exames (radiografias, microscopia).
* Dispositivos móveis: otimizar imagens para detecção em tempo real ou economia de energia.

**Dataset Sugerido:**

* [Low Light Image Enhancement](https://paperswithcode.com/task/low-light-image-enhancement) — imagens em baixa luminosidade para teste de filtros.

**Fitness Function:**

* Métricas de qualidade: SSIM (Structural Similarity Index), PSNR (Peak Signal-to-Noise Ratio).
* Pode incluir performance da tarefa final (ex.: detecção ou classificação).

**Implementação Prática:**

* Representação: real (parâmetros do filtro, intensidade, kernel size).
* População inicial: valores aleatórios dentro de limites plausíveis.
* Operadores: mutação altera parâmetros, crossover combina configurações de filtros.

---

**Resumo:**

| # | Projeto CV com AE     | Aplicação Real                                  | Dataset             | Fitness Function      | Representação  |
| - | --------------------- | ----------------------------------------------- | ------------------- | --------------------- | -------------- |
| 1 | Seleção de Features   | Diagnóstico médico, inspeção industrial         | MNIST, ISIC         | Acurácia / F1         | Binária        |
| 2 | Neuroevolution CNN    | Vigilância, agricultura, indústria              | CIFAR-10, Fruit-360 | Acurácia + parâmetros | Inteira / Real |
| 3 | Segmentação Evolutiva | Tumores, satélites, agricultura                 | DRIVE, Cityscapes   | IoU, Dice             | Vetor / árvore |
| 4 | Evolução de Filtros   | Baixa iluminação, medicina, dispositivos móveis | Low Light datasets  | SSIM + task final     | Real           |



---


# **Aplicações de Algoritmos Evolutivos em Reinforcement Learning**

Em RL, algoritmos evolutivos podem ser usados para **treinar agentes** ou **evoluir políticas de decisão** sem depender exclusivamente de gradientes. Isso é útil em ambientes complexos, parcialmente observáveis ou com recompensas escassas.

---

## **1. Treinamento de Agentes em Jogos e Simulações**

**Descrição:**

* Evoluir políticas (ações) de agentes para maximizar recompensas em ambientes de jogos ou simulações.
* Cada indivíduo = política ou conjunto de parâmetros do agente.

**Aplicações de Mercado:**

* Indústria de jogos → NPCs adaptativos.
* Simulação de treinamento de robôs ou drones.
* Teste de estratégias antes de deployment em ambientes reais.

**Ambiente / Dataset:**

* [OpenAI Gym – CartPole, LunarLander, Atari](https://gym.openai.com/)
* Simuladores de física: [PyBullet](https://pybullet.org/)

**Reward / Fitness Function:**

* Soma das recompensas obtidas em episódios de teste.
* Pode incluir penalização por ações não desejadas ou uso excessivo de recursos.

**Implementação Prática:**

* Representação: vetor de parâmetros da política (real ou binário, dependendo do caso).
* População inicial: políticas aleatórias.
* Operadores: crossover e mutação para gerar novas políticas.

---

## **2. Robótica e Controle de Movimentos**

**Descrição:**

* Evolução de **controladores de robôs** (trajetórias, posições, velocidade) para executar tarefas específicas.
* Algoritmos evolutivos encontram soluções que RL clássico com gradiente teria dificuldade devido à física complexa.

**Aplicações de Mercado:**

* Robôs industriais ajustando trajetórias para eficiência.
* Drones autônomos evitando obstáculos.
* Robôs de serviço (limpeza, entrega).

**Ambiente / Dataset:**

* [OpenAI Gym Robotics](https://gym.openai.com/envs/#robotics)
* [MuJoCo](http://www.mujoco.org/) (simulações físicas avançadas)

**Reward / Fitness Function:**

* Distância percorrida, tarefa completada, energia gasta, penalização por colisão.

**Implementação Prática:**

* Representação: vetor contínuo (parâmetros de controle do robô).
* População inicial: combinações aleatórias de trajetórias/valores de controle.
* Operadores: mutação + crossover nos parâmetros.

---

## **3. Otimização de Estratégias de Negócios**

**Descrição:**

* Agentes RL evoluem políticas para decisões em **estoque, marketing, trading**.
* Algoritmos evolutivos podem explorar rapidamente grandes espaços de estratégia sem exigir derivadas do modelo de negócio.

**Aplicações de Mercado:**

* Finanças: algoritmos de trading.
* Marketing: otimização de campanhas de retenção ou aquisição.
* Gestão de inventário: ajustar níveis de estoque e pedidos.

**Ambiente / Dataset:**

* Simulações de mercado financeiro: [OpenAI Gym – TradingEnv](https://github.com/AminHP/gym-anytrading)
* Dados de marketing: [Kaggle Marketing Campaign](https://www.kaggle.com/datasets/rodsaldanha/arketing-campaign)

**Reward / Fitness Function:**

* Lucro líquido, ROI, minimização de perdas ou penalização por recursos desperdiçados.

**Implementação Prática:**

* Representação: vetor de parâmetros de estratégia ou tabela de decisão discreta.
* População inicial: estratégias aleatórias.
* Operadores: crossover entre estratégias e mutação em decisões discretas.

---

## **4. Otimização de Hiperparâmetros de Agentes RL**

**Descrição:**

* Usar AEs para ajustar hiperparâmetros de agentes RL clássicos (ex.: learning rate, discount factor, tamanho de buffer).
* Permite acelerar o treinamento de agentes em ambientes complexos.

**Aplicações de Mercado:**

* Treinamento de bots em simuladores de logística.
* Otimização de sistemas de recomendação que usam RL.
* Ajuste de controladores inteligentes para robôs ou IoT.

**Ambiente / Dataset:**

* [OpenAI Gym](https://gym.openai.com/)
* [RLlib / Ray](https://docs.ray.io/en/latest/rllib.html)

**Reward / Fitness Function:**

* Performance do agente após N episódios.
* Pode incluir eficiência de computação ou estabilidade do aprendizado.

**Implementação Prática:**

* Representação: vetor real (hiperparâmetros contínuos).
* População inicial: amostras aleatórias de combinações de hiperparâmetros.
* Operadores: mutação contínua e crossover de parâmetros.

---

# ✅ **Resumo em Tabela**

| # | Projeto RL com AE      | Aplicação Real                    | Ambiente/Dataset            | Fitness / Reward                 | Representação                   |
| - | ---------------------- | --------------------------------- | --------------------------- | -------------------------------- | ------------------------------- |
| 1 | Agentes em Jogos       | NPCs, simulações                  | OpenAI Gym, PyBullet        | Soma de recompensas por episódio | Vetor real/binário              |
| 2 | Robótica               | Robôs industriais, drones         | Gym Robotics, MuJoCo        | Tarefa completada + penalização  | Vetor real (controle)           |
| 3 | Estratégias de Negócio | Trading, marketing, inventário    | TradingEnv, Kaggle Campaign | Lucro, ROI, eficiência           | Vetor de parâmetros ou discreto |
| 4 | Hiperparâmetros de RL  | Bots, controladores, recomendação | Gym, RLlib                  | Performance final do agente      | Vetor real                      |

