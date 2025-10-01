
# Representações de soluções 

A representação da solução (ou codificação) define como cada indivíduo da população será modelado dentro do algoritmo. A escolha da representação depende do problema a ser resolvido.

## 1. Representação Binária


Descrição: cada indivíduo é representado como uma sequência de bits (0s e 1s).

Exemplo: 1011010 pode representar um conjunto de variáveis escolhidas (1 = selecionado, 0 = não selecionado).

# Aplicações:

- [Problemas de seleção de features em IA.](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=binary+representation+in+ev+algorithms+for+features+selection&btnG=) 

- [Problema da mochila *knapsack problem*](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=binary+representation+in+ev+algorithms+knapsack+problem&btnG=)

- [Planejamento onde variáveis só podem estar "ligadas/desligadas".](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=binary+representation+in+ev+algorithms+with+variables+only+on%2Foff&btnG=)

### Vantagens: simples de implementar; operadores de crossover e mutação são diretos

### Limitações: pouco eficiente para problemas com valores contínuos ou de grande escala.

## 2. Inteira 

Descrição: indivíduos são vetores de números inteiros.

Exemplo: [3, 1, 5, 2] pode indicar a ordem de execução de tarefas ou rotas.

**Aplicações:**

- [Problemas de roteamento (ex.: caixeiro viajante → cada inteiro representa uma cidade).](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=complete+representation+in+evolutive+algorithms+for+routing+problems&btnG=)

- [Escalonamento de tarefas (inteiros representam ordem de processos).](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=representation+in+evolutive+algorithms+for+escaling+tasks&btnG=)

- [Design de circuitos, codificação de regras discretas.](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=representation+in+evolutive+algorithms+for+circuit+design&btnG=)

### Vantagens: adequado para problemas combinatórios.

### Limitações: operadores de crossover/mutação precisam ser ajustados para não gerar soluções inválidas.


## 3. Real (ou contínua)

Descrição: indivíduos são vetores de números reais (ponto flutuante).

Exemplo: [0.23, -1.57, 3.14] pode representar pesos de uma rede neural.


**Aplicações:**

- [Ajuste de parâmetros contínuos (ex.: otimização de funções matemáticas).](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=continuos+representation+in+evolutive+algorithms+for+parameters+adjustment&btnG=&oq=continuos+representation+in+evolutive+algorithms+for+parameters+ad)

- [Treinamento e ajuste fino de modelos de Machine Learning.](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=continuos+representation+in+evolutive+algorithms+for+fine-tunning+machine+learning+models&btnG=)

- [Engenharia (design de estruturas, parâmetros físicos).](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=continuos+representation+in+evolutive+algorithms+for+structures+design+with+physical+parameters&btnG=)

### Vantagens: mais natural e eficiente em problemas contínuos; evita conversões binárias.

### Limitações: definição de operadores de mutação pode ser mais complexa (ex.: perturbações gaussianas).

## Função de fitness

A função de fitness mede a qualidade de cada indivíduo.
É o critério que guia o processo evolutivo.

*Objetivo:* quantificar quão boa é a solução para o problema.

*Características importantes:*

- Deve refletir fielmente o objetivo real.

- Pode ser maximização ou minimização (normalmente convertida para maximização).

**Exemplos:**

- Em logística: distância total da rota (quanto menor, melhor).

- Em IA: acurácia ou F1-score de um classificador.

- Em finanças: retorno esperado do portfólio menos risco.

- Fitness multiobjetivo: quando há mais de um critério (ex.: minimizar custo e tempo → algoritmos como [NSGA-II](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=NSGA-II&btnG=)).



## População inicial

É o conjunto inicial de soluções a partir do qual o algoritmo começa a evoluir.

- Tamanho da população:

    - População pequena → converge rápido, mas pode perder diversidade.

    - População grande → maior diversidade, mas maior custo computacional.

### Formas de gerar:

- Aleatória: valores gerados de forma totalmente randômica (mais comum).

- Heurística / Informada: usar conhecimento prévio para criar soluções iniciais melhores. Ex.: começar uma parte da população com rotas do algoritmo greedy.

- Híbrida: mistura de aleatória e heurística.


---

# Resumo Final

Representação: define como o problema é “traduzido” para dentro do algoritmo (binária, inteira, real).

Fitness: avalia a qualidade das soluções.

População inicial: fornece diversidade e ponto de partida para a evolução.