# Aula 4 — Crossover em Algoritmos Genéticos


## 1. O que é Crossover?

O **crossover**, também conhecido como **recombinação genética**, é uma das operações fundamentais dos **Algoritmos Genéticos (AGs)**.
Seu papel é **gerar novos indivíduos (descendentes)** a partir da **combinação de dois indivíduos (pais)** da população atual.

A ideia é inspirada na **reprodução biológica**: assim como no processo natural de hereditariedade, o crossover permite que os filhos recebam **características genéticas de ambos os pais**, potencialmente herdando as partes mais vantajosas de cada um.

No contexto computacional:

* Cada indivíduo representa uma **solução candidata** a um problema.
* O **cromossomo** é uma sequência de genes (por exemplo, uma lista de números binários, inteiros ou reais).
* O crossover atua sobre esses cromossomos, trocando partes entre dois pais para formar novos filhos.

O principal **objetivo do crossover** é **explorar novas regiões do espaço de busca** — ou seja, criar soluções que talvez não estivessem presentes anteriormente na população.

---

## 2. Por que o Crossover é Importante?

Em um algoritmo genético, o crossover cumpre a função de **exploração**.
Enquanto a **mutação** introduz pequenas alterações aleatórias (mantendo a diversidade genética), o crossover **combina estruturas já existentes** para potencialmente criar indivíduos superiores.

### Benefícios principais:

1. **Combinação de boas soluções:** permite unir partes vantajosas de diferentes indivíduos.
2. **Maior velocidade de convergência:** soluções promissoras são recombinadas rapidamente.
3. **Diversificação controlada:** mantém a variabilidade da população sem depender apenas da mutação.

### Sem o crossover:

* O algoritmo tenderia a funcionar como uma **busca aleatória guiada por mutações**.
* O processo de evolução seria **muito mais lento**, pois as boas combinações de genes dependeriam apenas do acaso.

Assim, o crossover atua como uma **ponte entre exploração e exploração dirigida**, sendo crucial para o equilíbrio de um AG eficiente.

---

## 3. Como o Crossover Funciona

O processo de crossover pode ser descrito em quatro etapas:

1. **Seleção dos pais:**
   Dois indivíduos são escolhidos (geralmente pelos métodos de seleção estudados anteriormente, como torneio ou roleta).

2. **Verificação da probabilidade de crossover:**
   Um número aleatório é sorteado.

   * Se for menor que a **probabilidade de crossover (Pc)**, o cruzamento é realizado.
   * Caso contrário, os filhos são cópias diretas dos pais.

3. **Aplicação do operador de crossover:**
   O tipo de crossover escolhido (1 ponto, 2 pontos, uniforme, etc.) define **como os genes serão trocados**.

4. **Geração dos filhos:**
   Os novos indivíduos substituem ou complementam os pais na população.

---

## 4. Tipos de Crossover

Existem diversos tipos de crossover. A escolha do tipo depende da **representação do cromossomo** e do **problema** a ser resolvido.
A seguir estão os quatro métodos mais comuns.

---

### 4.1 Crossover de 1 Ponto

O **crossover de um ponto** é o mais clássico e simples.
Um **ponto de corte** é escolhido aleatoriamente dentro do cromossomo, e as partes dos pais são trocadas a partir desse ponto.

**Etapas:**

1. Escolher um ponto de corte aleatório.
2. Trocar os genes após esse ponto entre os dois pais.

**Exemplo:**

```
Pai 1: [1 1 0 0 | 1 0 0]
Pai 2: [0 0 1 1 | 0 1 1]
Corte: após o 4º gene
Filho 1: [1 1 0 0 | 0 1 1]
Filho 2: [0 0 1 1 | 1 0 0]
```

**Características:**

* Preserva blocos contínuos de genes (estruturas locais).
* É eficiente quando genes próximos possuem relação (dependência).
* Pode ser limitante se o ponto de corte fixo não explorar bem todas as combinações.

---

### 4.2 Crossover de 2 Pontos

É uma extensão do método anterior.
Dois pontos de corte são escolhidos, e a **região entre eles é trocada** entre os pais.

**Exemplo:**

```
Pai 1: [1 | 1 0 0 | 1 0 0]
Pai 2: [0 | 0 1 1 | 0 1 1]
Cortes: após os genes 1 e 4
Filho 1: [1 | 0 1 1 | 1 0 0]
Filho 2: [0 | 1 0 0 | 0 1 1]
```

**Características:**

* Mantém mais partes dos cromossomos originais.
* Gera maior variabilidade que o crossover de um ponto.
* Recomendado para cromossomos longos.

---

### 4.3 Crossover Uniforme

No **crossover uniforme**, cada gene é avaliado individualmente:

* Com 50% de chance (ou outro valor definido), o gene vem do **Pai 1**.
* Caso contrário, vem do **Pai 2**.

**Exemplo:**

```
Máscara: [1 0 1 1 0 0 1]  (1 = gene do Pai 1, 0 = gene do Pai 2)
Pai 1:   [1 1 0 0 1 0 0]
Pai 2:   [0 0 1 1 0 1 1]
Filho 1: [1 0 0 0 0 1 0]
```

**Características:**

* A mistura é totalmente aleatória e equilibrada.
* Mantém alta diversidade genética.
* Pode quebrar estruturas de genes importantes (epistasia), dificultando a preservação de bons blocos.

---

### 4.4 Crossover Aritmético

Usado principalmente em **representações reais** (variáveis contínuas).
Em vez de trocar genes diretamente, os valores são **combinados por média ponderada**.

A fórmula geral é:

$$
Filho = \alpha \cdot Pai_1 + (1 - \alpha) \cdot Pai_2
$$

onde $\alpha \in [0,1]$

**Exemplo:**

```
Pai 1: [2.0, 4.0]
Pai 2: [6.0, 8.0]
α = 0.5
Filho: [4.0, 6.0]
```

**Variações:**

* Pode-se usar valores de α aleatórios a cada cruzamento.
* Também é possível gerar dois filhos:

  * Filho 1 = α * Pai1 + (1 - α) * Pai2
  * Filho 2 = (1 - α) * Pai1 + α * Pai2

**Características:**

* Mantém a coerência entre genes contínuos.
* Suaviza o processo de busca (sem saltos bruscos).
* Ideal para otimização de parâmetros reais (ex.: pesos, coeficientes, posições).

---

## 5. Probabilidade de Crossover (Pc)

A **probabilidade de crossover** determina com que frequência dois pais **efetivamente se cruzam**.
Em cada geração, para cada par de pais selecionados:

* Gera-se um número aleatório entre 0 e 1.
* Se esse número ≤ Pc, o crossover é realizado.
* Caso contrário, os filhos são cópias dos pais.

### Valores típicos

* Pc entre **0.6 e 0.9** é comum na literatura.
* Pc = 1.0 significa que **todos os pares cruzam** (muita exploração).
* Pc muito baixa (ex.: 0.3) pode **reduzir a diversidade** e **atrasar a convergência**.

### Efeitos Práticos

* **Pc alta:** maior variação de soluções, mas risco de perder boas combinações.
* **Pc moderada:** equilíbrio entre exploração e estabilidade.
* **Pc baixa:** o algoritmo se comporta quase como uma busca local.

Em experimentos, o ideal é **ajustar Pc empiricamente**, observando o impacto na qualidade e velocidade de convergência das soluções.

---

## 6. Comparação Resumida dos Tipos de Crossover

| Tipo de Crossover | Representação Ideal | Preserva Estrutura | Introduz Diversidade | Complexidade | Indicado Para                    |
| ----------------- | ------------------- | ------------------ | -------------------- | ------------ | -------------------------------- |
| 1 ponto           | Binária, inteira    | Alta               | Média                | Baixa        | Problemas discretos simples      |
| 2 pontos          | Binária, inteira    | Média              | Alta                 | Média        | Cromossomos longos               |
| Uniforme          | Binária             | Baixa              | Alta                 | Média        | Quando se deseja alta exploração |
| Aritmético        | Real                | Alta               | Média                | Baixa        | Problemas contínuos              |

---

## 7. Considerações Finais

* O crossover é o **principal mecanismo de exploração** em um AG.
* Diferentes tipos de crossover **alteram a forma de explorar o espaço de soluções**.
* A escolha correta depende:

  * Da **codificação** (binária, inteira, real).
  * Da **natureza do problema** (discreto ou contínuo).
  * Da **interação entre genes** (se há blocos dependentes ou não).
* É importante **experimentar múltiplos tipos e probabilidades de crossover** para identificar o equilíbrio ideal entre **exploração e preservação**.

