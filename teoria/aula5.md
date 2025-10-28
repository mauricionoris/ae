# Aula 5 — Mutação, Parâmetros, Elitismo e Critérios de Parada

## 1. O que é Mutação?

Nos **Algoritmos Genéticos (AGs)**, a **mutação** é o operador responsável por **introduzir pequenas variações aleatórias nos indivíduos**.
Ela atua sobre os **genes** do cromossomo, alterando seus valores com uma **pequena probabilidade**, geralmente chamada de **probabilidade de mutação (Pm)**.

O objetivo da mutação é **manter a diversidade genética** da população, evitando que todas as soluções se tornem muito semelhantes (o que pode levar à **convergência prematura**).

Enquanto o **crossover** combina informações existentes entre indivíduos, a **mutação cria novas informações** — ela é, portanto, o principal mecanismo de **exploração aleatória**.

---

## 2. Papel da Mutação no Algoritmo Genético

A mutação tem três papéis fundamentais:

1. **Prevenir estagnação:** impede que a população fique presa em um ótimo local.
2. **Introduzir variabilidade:** gera novas soluções que não existiam antes.
3. **Complementar o crossover:** atua como um mecanismo secundário de exploração.

A mutação deve ser **rara**, pois mudanças excessivas podem **destruir soluções boas** obtidas via crossover.
Por outro lado, mutações muito raras fazem o algoritmo **perder capacidade de inovação**.

Portanto, o segredo está no **equilíbrio entre estabilidade e diversidade**.

---

## 3. Principais Tipos de Mutação

A escolha do tipo de mutação depende da **representação dos indivíduos** (binária, inteira, real, permutação, etc.).
A seguir, estão os três tipos mais usados na prática.

---

### 3.1 Mutação Bit Flip (ou Mutação Binária)

Utilizada quando o cromossomo é representado por **cadeias binárias** (0s e 1s).

Cada gene tem uma chance **Pm** de ter seu valor invertido:

* 0 → 1
* 1 → 0

**Exemplo:**

```
Indivíduo antes: [1 0 0 1 1 0]
Posição sorteada: 3
Indivíduo após mutação: [1 0 1 1 1 0]
```

**Características:**

* Simples e eficiente.
* Ideal para problemas com codificação binária.
* A intensidade da mutação depende diretamente da probabilidade Pm.

**Parâmetro típico:**
Pm entre **0.001 e 0.05**, dependendo do tamanho do cromossomo.

---

### 3.2 Mutação Gaussiana (para Representação Real)

Usada quando os genes são **números reais** (variáveis contínuas).
Em vez de trocar um valor por outro, a mutação adiciona **um pequeno ruído aleatório** seguindo uma **distribuição normal (gaussiana)**:

$$
x' = x + N(0, \sigma)
$$

onde:

* ( x ) é o valor original do gene,
* ( N(0, $\sigma$) ) é um número aleatório com média 0 e desvio padrão σ,
* σ controla a intensidade da mutação.

**Exemplo:**

```
Gene original: 4.2
Ruído gaussiano (σ = 0.3): +0.12
Gene após mutação: 4.32
```

**Características:**

* Preserva a continuidade das soluções.
* Controla a magnitude da perturbação por σ.
* Usada em problemas de otimização de parâmetros contínuos.

**Boas práticas:**

* Começar com σ alto (exploração ampla) e reduzi-lo ao longo das gerações (exploração fina).

---

### 3.3 Mutação por Troca (Swap Mutation)

Comum em **problemas de permutação**, como o **Problema do Caixeiro Viajante (TSP)**.
A mutação escolhe **duas posições aleatórias** e **troca os genes entre elas**.

**Exemplo:**

```
Indivíduo antes: [A B C D E F]
Posições sorteadas: 2 e 5
Indivíduo após mutação: [A E C D B F]
```

**Características:**

* Mantém a validade da permutação (sem duplicar ou perder elementos).
* Gera pequenas perturbações sem destruir a estrutura global.
* Ideal para problemas combinatórios e de ordenação.

---

## 4. Parâmetros do Algoritmo Genético

O desempenho de um AG depende fortemente de seus **parâmetros de configuração**.
Os principais são:

| Parâmetro                           | Significado                                   | Efeito Prático                                                                              |
| ----------------------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------- |
| **Tamanho da população (N)**        | Número de indivíduos por geração              | Populações grandes aumentam a diversidade, mas exigem mais tempo de execução                |
| **Probabilidade de crossover (Pc)** | Chance de realizar cruzamento entre dois pais | Alta Pc (0.6–0.9) promove mistura genética; baixa Pc reduz a exploração                     |
| **Probabilidade de mutação (Pm)**   | Chance de mutar um gene                       | Alta Pm aumenta diversidade, mas pode desestabilizar o algoritmo; baixa Pm reduz exploração |

### Diretrizes gerais:

* População pequena → rápida convergência, mas risco de ótimos locais.
* População grande → melhor cobertura do espaço, porém mais custo computacional.
* Ajuste fino deve ser feito **experimentalmente** conforme o problema.

---

## 5. Elitismo

O **elitismo** é uma estratégia usada para **preservar as melhores soluções** de uma geração para a próxima.
Em vez de substituir completamente a população, o algoritmo **mantém os indivíduos com maior fitness** (ou uma fração deles).

### Como funciona:

1. Avalia-se toda a população.
2. Os **melhores indivíduos (elite)** são copiados diretamente para a próxima geração.
3. O restante da população é preenchido pelos novos filhos gerados por crossover e mutação.

**Vantagens:**

* Garante que a qualidade da população **nunca piore** de uma geração para outra.
* Acelera a convergência, pois as melhores soluções não são perdidas por acaso.

**Desvantagens:**

* Pode contribuir para **convergência prematura**, se a elite for grande demais (a população se torna homogênea muito rápido).

**Recomendação prática:**

* Preservar de **1 a 5% dos melhores indivíduos**, dependendo do tamanho da população.

---

## 6. Convergência Prematura

A **convergência prematura** ocorre quando o algoritmo **chega rapidamente a uma solução subótima** e perde diversidade genética.
Todos os indivíduos acabam se tornando semelhantes, impedindo que novas soluções sejam exploradas.

### Causas comuns:

* Probabilidade de crossover ou mutação mal calibradas.
* Elite muito grande.
* Seleção excessivamente “dura” (foco exagerado nos melhores indivíduos).
* População muito pequena.

### Sintomas:

* O melhor fitness não melhora por várias gerações.
* A média da população se aproxima rapidamente do melhor valor.
* Todos os indivíduos possuem cromossomos muito parecidos.

### Estratégias de mitigação:

* Aumentar a taxa de mutação.
* Reduzir o elitismo.
* Adotar métodos de seleção menos agressivos (ex.: torneio pequeno, roleta).
* Introduzir indivíduos aleatórios periodicamente.

O equilíbrio entre **exploração (diversidade)** e **exploração dirigida (seleção)** é essencial para evitar esse problema.

---

## 7. Critérios de Parada

Um AG é um processo iterativo, e por isso é preciso definir **quando parar** a evolução.
Os critérios de parada determinam **quando o algoritmo deve encerrar a execução** e retornar a melhor solução encontrada.

### Critérios mais comuns:

| Critério                      | Descrição                                                         | Vantagens                              | Desvantagens                                       |
| ----------------------------- | ----------------------------------------------------------------- | -------------------------------------- | -------------------------------------------------- |
| **Número máximo de gerações** | Executa o AG por um número fixo de iterações                      | Simples e previsível                   | Pode parar cedo demais ou rodar desnecessariamente |
| **Fitness alvo**              | Encerra quando o melhor indivíduo atinge um valor desejado        | Ideal para problemas com meta definida | Exige conhecimento prévio do valor ótimo           |
| **Estagnação**                | Para se o melhor fitness não melhora após X gerações consecutivas | Evita desperdício de processamento     | Pode parar antes de explorar uma nova região       |
| **Tempo máximo de execução**  | Interrompe após um tempo limite                                   | Útil em aplicações de tempo real       | Pode encerrar antes da convergência                |

### Recomendações:

* Em experimentos iniciais, usar **número fixo de gerações**.
* Em versões mais maduras, combinar **dois ou mais critérios** (por exemplo, “100 gerações ou estagnação de 20 iterações”).

---

## 8. Relação entre Mutação, Elitismo e Convergência

Esses três conceitos estão intimamente ligados:

* **Mutação** aumenta a **diversidade** e evita a **convergência prematura**.
* **Elitismo** preserva o **melhor conhecimento** adquirido.
* **Convergência** é o equilíbrio entre **exploração (mutação)** e **exploração dirigida (elitismo e seleção)**.

Um bom algoritmo genético deve encontrar **um ponto de equilíbrio dinâmico**:

* Muita mutação → comportamento quase aleatório.
* Muito elitismo → perda de diversidade.
* Ausência de mutação → estagnação.

A sintonia fina desses fatores é parte essencial do **projeto experimental** de um AG robusto.

---

## 9. Conclusão

Nesta parte da aula, vimos que:

* A **mutação** é o mecanismo de inovação genética nos algoritmos genéticos.
* Existem várias formas de mutação, adequadas a diferentes tipos de representação.
* A calibração dos **parâmetros** (população, Pc, Pm) é determinante para o sucesso.
* O **elitismo** é importante, mas deve ser usado com cuidado para evitar convergência prematura.
* **Critérios de parada** bem definidos garantem eficiência e controle sobre o processo evolutivo.




