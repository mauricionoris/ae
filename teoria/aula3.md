# Métodos Básicos



### **1. Seleção por Roleta (Roulette Wheel Selection)**

**Ideia principal:** cada indivíduo recebe uma "fatia" da roleta proporcional ao seu valor de **fitness** (quanto melhor ele é, maior a fatia).
Ao girar a roleta, a probabilidade de ser escolhido é proporcional ao desempenho.

**Como funciona:**

1. Calcula-se o fitness total da população.
2. Cada indivíduo tem uma probabilidade:
   
$$
P(i) = \frac{fitness(i)}{\sum fitness(j)}
$$

3. A roleta é girada (gerando um número aleatório entre 0 e 1), e o indivíduo correspondente é selecionado.

**Vantagem:**

* Mantém diversidade, pois mesmo indivíduos medianos têm alguma chance.
  **Desvantagem:**
* Se um indivíduo tiver fitness muito alto, ele pode dominar a seleção (perda de diversidade).

**Analogia:**
Como uma roleta de cassino, mas as “fatias” são maiores para indivíduos mais aptos.

---

### **2. Seleção por Torneio (Tournament Selection)**

**Ideia principal:** escolher aleatoriamente um pequeno grupo de indivíduos (por exemplo, 3 ou 5) e selecionar o **melhor** entre eles.

**Como funciona:**

1. Escolhe-se aleatoriamente *k* indivíduos da população (por exemplo, k = 3).
2. Compara-se o fitness dos participantes.
3. O melhor deles é selecionado para reprodução.
4. Repete-se o processo até formar o conjunto de pais.

**Vantagem:**

* Simples e rápido.
* Controla a **pressão seletiva** ajustando o tamanho do torneio (*k*): quanto maior *k*, maior a chance dos melhores dominarem.
  **Desvantagem:**
* Pode reduzir a diversidade se *k* for muito grande.

**Analogia:**
Como um campeonato: quem vence o “mini torneio” é o escolhido.

---

📘 **Resumo Comparativo:**

| Método  | Base da Escolha               | Controle de Seleção | Diversidade | Complexidade |
| ------- | ----------------------------- | ------------------- | ----------- | ------------ |
| Roleta  | Proporcional ao fitness       | Difícil ajustar     | Boa         | Moderada     |
| Torneio | Competição local entre poucos | Fácil (via k)       | Controlável | Baixa        |



---
# Métodos avançados


### 1. **Seleção por Ranking (Ranking Selection)**

* **Como funciona:** Ordena os indivíduos de acordo com sua aptidão e atribui probabilidades de seleção proporcional à posição no ranking, e não ao valor absoluto da aptidão. Isso evita que indivíduos muito fortes dominem a população precocemente (elitismo extremo).
* **Vantagem:** Controla melhor a pressão seletiva e evita convergência prematura.
* **Fonte:** Baker, J.E. (1985). *Adaptive Selection Methods for Genetic Algorithms*. In Proceedings of the First International Conference on Genetic Algorithms.

---

### 2. **Seleção por Elitismo (Elitist Selection)**

* **Como funciona:** Mantém automaticamente os melhores indivíduos de uma geração para a próxima sem risco de serem perdidos durante a recombinação ou mutação.
* **Vantagem:** Garante que a qualidade da população nunca diminua de uma geração para a outra. Geralmente é combinada com outros métodos de seleção.
* **Fonte:** Goldberg, D.E. (1989). *Genetic Algorithms in Search, Optimization, and Machine Learning*. Addison-Wesley.

---

### 3. **Seleção Estocástica Universal (Stochastic Universal Sampling - SUS)**

* **Como funciona:** Uma variação da roleta, mas ao invés de selecionar indivíduos um por um, distribui múltiplos "pontos" uniformemente na roda da roleta, garantindo uma amostragem mais uniforme da população.
* **Vantagem:** Reduz a variância do processo de seleção e melhora a diversidade genética.
* **Fonte:** Baker, J.E. (1987). *Reducing Bias and Inefficiency in the Selection Algorithm*. In Proceedings of the Second International Conference on Genetic Algorithms.

---

### 4. **Seleção por Bolsa de Sobrevivência (Steady-State Selection)**

* **Como funciona:** Apenas alguns indivíduos da população são substituídos por descendentes em cada geração, em vez de substituir toda a população. Normalmente, os indivíduos menos aptos são os que saem.
* **Vantagem:** Mantém maior diversidade genética e evita perda brusca de bons indivíduos.
* **Fonte:** Whitley, D. (1994). *A Genetic Algorithm Tutorial*. Statistics and Computing, 4(2), 65–85.

---

### 5. **Seleção por Torneio Estocástico (Stochastic Tournament)**

* **Como funciona:** Semelhante ao torneio clássico, mas mesmo o indivíduo "menos apto" do torneio pode ser selecionado com uma pequena probabilidade. Isso adiciona aleatoriedade e mantém diversidade.
* **Vantagem:** Reduz a chance de convergência prematura e permite explorar soluções variadas.
* **Fonte:** Miller, B.L., & Goldberg, D.E. (1996). *Genetic Algorithms, Tournament Selection, and the Effects of Noise*. Complex Systems, 9(3), 193–212.

---

### 6. **Seleção por Sobrevivência por Idade (Age-Based Selection)**

* **Como funciona:** A sobrevivência não depende somente da aptidão, mas também da idade do indivíduo. Indivíduos mais velhos são gradualmente substituídos por novos, independentemente de sua aptidão.
* **Vantagem:** Incentiva a introdução constante de novas soluções, aumentando a diversidade genética da população.
* **Fonte:** Hornby, G.S., & Pollack, J.B. (2001). *The Advantages of Age-Layered Populations for Evolving Complex Systems*. Proceedings of GECCO 2001.

# Resumo

##  **1. Métodos Proporcionais à Aptidão**

Selecionam indivíduos com probabilidade **proporcional à sua aptidão absoluta**.

| Método                                                          | Descrição                                                                                                                                  | Referência                                                                                 |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Roleta (Fitness Proportionate Selection)**                    | A probabilidade de cada indivíduo ser escolhido é proporcional à sua aptidão.                                                              | Holland, J.H. (1975). *Adaptation in Natural and Artificial Systems*.                      |
| **Estocástico Universal (Stochastic Universal Sampling - SUS)** | Seleciona vários indivíduos de forma equidistante na “roda da roleta”, reduzindo variância.                                                | Baker, J.E. (1987). *Reducing Bias and Inefficiency in the Selection Algorithm*.           |
| **Seleção por Restos (Remainder Stochastic Sampling)**          | Usa a parte inteira da proporção de aptidão para garantir seleção de bons indivíduos, e a parte fracionária é tratada probabilisticamente. | Goldberg, D.E. (1989). *Genetic Algorithms in Search, Optimization, and Machine Learning*. |

---

##  **2. Métodos Baseados em Ranking**

Selecionam com base **na posição ordenada da aptidão**, não em seus valores absolutos.

| Método                                                  | Descrição                                                               | Referência                                                                                        |
| ------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Ranking Linear (Linear Ranking Selection)**           | Atribui probabilidades linearmente conforme a posição no ranking.       | Baker, J.E. (1985). *Adaptive Selection Methods for Genetic Algorithms*.                          |
| **Ranking Exponencial (Exponential Ranking Selection)** | Indivíduos com maior rank recebem probabilidade exponencialmente maior. | Blickle, T., & Thiele, L. (1996). *A Comparison of Selection Schemes Used in Genetic Algorithms*. |

---

##  **3. Métodos de Torneio**

Baseiam-se em **competições locais** entre subconjuntos de indivíduos.

| Método                     | Descrição                                                                                     | Referência                                                                              |
| -------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| **Torneio Determinístico** | Escolhe o melhor indivíduo de um grupo aleatório (por ex., de 2 ou 3).                        | Goldberg, D.E., & Deb, K. (1991). *A Comparative Analysis of Selection Schemes*.        |
| **Torneio Estocástico**    | Mesmo o perdedor pode ser escolhido com pequena probabilidade (controle da pressão seletiva). | Miller, B.L., & Goldberg, D.E. (1996). *Tournament Selection and the Effects of Noise*. |

---

##  **4. Métodos Baseados em Elitismo e Sobrevivência**

Conservam os melhores indivíduos ou impõem restrições de substituição.

| Método                     | Descrição                                                                             | Referência                                                       |
| -------------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **Elitismo Puro**          | Mantém automaticamente os melhores indivíduos na próxima geração.                     | Goldberg, D.E. (1989).                                           |
| **Steady-State Selection** | Substitui apenas alguns indivíduos por geração, mantendo o restante da população.     | Whitley, D. (1994). *A Genetic Algorithm Tutorial*.              |
| **Age-Based Selection**    | A seleção é influenciada pela idade — indivíduos antigos são removidos mesmo se bons. | Hornby, G.S., & Pollack, J.B. (2001). *Age-Layered Populations*. |

---

##  **5. Métodos Baseados em Estruturas Populacionais**

A seleção é influenciada pela **proximidade ou subpopulações**.

| Método                                                | Descrição                                                                                       | Referência                                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Seleção por Vizinhança (Neighborhood Selection)**   | Indivíduos competem apenas com vizinhos próximos (em grid, anel etc.).                          | Whitley, D. (1993). *Cellular Genetic Algorithms*.                         |
| **Seleção por Ilhas (Island Model / Distributed GA)** | A população é dividida em subpopulações (ilhas) que evoluem e trocam indivíduos ocasionalmente. | Tanese, R. (1989). *Distributed Genetic Algorithms*.                       |
| **Seleção por Demes (Coarse-Grained)**                | Variante do modelo de ilhas, com migração rara e populações semi-isoladas.                      | Cohoon, J.P. et al. (1987). *Punctuated Equilibria in Genetic Algorithms*. |

---

##  **6. Métodos Híbridos e Específicos**

Combinam estratégias de diferentes categorias ou introduzem critérios adicionais.

| Método                                                             | Descrição                                                                                   | Referência                                                                                |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **Seleção por Aptidão Normalizada (Normalized Fitness Selection)** | A aptidão é reescalada (por exemplo, entre 0 e 1) antes da roleta.                          | Goldberg, D.E. (1989).                                                                    |
| **Seleção por Competição Local (Local Competition)**               | Indivíduos são comparados apenas dentro de uma pequena vizinhança definida topologicamente. | Sarma, J., & De Jong, K.A. (1996). *An Analysis of Local Selection Algorithms*.           |
| **Seleção por Probabilidade Adaptativa (Adaptive Selection)**      | A pressão seletiva é ajustada dinamicamente conforme o progresso evolutivo.                 | Srinivas, M., & Patnaik, L.M. (1994). *Adaptive Probabilities of Crossover and Mutation*. |

---

##  **Principais Fontes Gerais**

1. Holland, J.H. (1975). *Adaptation in Natural and Artificial Systems*. University of Michigan Press.
2. Goldberg, D.E. (1989). *Genetic Algorithms in Search, Optimization, and Machine Learning*. Addison-Wesley.
3. Whitley, D. (1994). *A Genetic Algorithm Tutorial*. *Statistics and Computing*, 4(2), 65–85.
4. Blickle, T., & Thiele, L. (1996). *A Comparison of Selection Schemes Used in Genetic Algorithms*.
5. Miller, B.L., & Goldberg, D.E. (1996). *Genetic Algorithms, Tournament Selection, and the Effects of Noise*.


