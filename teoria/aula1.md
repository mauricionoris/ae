# Introdução

## O que são **Algoritmos Evolutivos (AEs)?**

**Definição simples**:
Algoritmos Evolutivos são técnicas de **Inteligência Artificial inspiradas na evolução natural**.
Eles simulam o processo de **seleção natural**, onde indivíduos mais adaptados têm maior chance de sobreviver e se reproduzir, gerando novas soluções cada vez melhores para um problema.

---

# Como funcionam? (visão geral)

1. **População inicial**

   * Começamos com várias soluções possíveis (indivíduos).
   * Exemplo: diferentes rotas para um entregador, diferentes combinações de variáveis em um modelo de IA.

2. **Avaliação (fitness)**

   * Cada indivíduo é avaliado com base em uma **função de aptidão** (fitness function).
   * Exemplo: tempo total da rota, acurácia de um modelo, custo de um plano de produção.

3. **Seleção**

   * As melhores soluções têm mais chance de serem escolhidas para “reproduzir”.

4. **Cruzamento (crossover)**

   * Combinar duas soluções para gerar uma nova.
   * Exemplo: misturar parte de uma rota com parte de outra.

5. **Mutação**

   * Alterar aleatoriamente partes da solução para explorar novas possibilidades.

6. **Iteração (gerações)**

   * Repetir os passos até que surjam soluções boas o suficiente.

---

# Principais Tipos de Algoritmos Evolutivos

* **Algoritmos Genéticos (GA)** → mais conhecidos, trabalham com cadeias (como cromossomos).
* **Programação Genética (GP)** → evoluem programas ou expressões matemáticas inteiras.
* **Estrategias Evolutivas (ES)** → focam em parâmetros numéricos contínuos.
* **Algoritmos de Colônia (PSO, ACO)** → inspirados em comportamento coletivo (formigas, pássaros).

*(muitas vezes agrupamos tudo sob o nome “computação evolutiva”)*

---

# Por que usar algoritmos evolutivos?

**Não precisam de derivadas** → funcionam mesmo em problemas não lineares e sem fórmulas claras.

**São flexíveis** → aplicam-se em otimização, busca, ajuste de parâmetros, geração de regras.

**São robustos** → lidam bem com problemas com múltiplos objetivos e restrições.

**Mercado real** → usados em **finanças, logística, saúde, marketing, energia, IA moderna** (AutoML, evolução de redes neurais, otimização de prompts).

---

# Exemplo rápido (intuitivo)

Imagine que você quer encontrar a **melhor dieta possível** dentro de restrições de calorias, custo e nutrientes.

* Cada dieta = **um indivíduo**.
* O quão saudável/barata é = **fitness**.
* Cruzamento = combinar itens de duas dietas diferentes.
* Mutação = trocar um alimento por outro.
* Ao longo das gerações, surgem dietas **mais equilibradas**.

---

*RESUMINDO*: **Algoritmos Evolutivos são métodos de otimização inspirados na natureza, capazes de encontrar boas soluções para problemas difíceis onde métodos tradicionais falham.**


## 4. Aplicações reais.


## **Exemplos Reais de Aplicação de Algoritmos Evolutivos**

### 1. **Otimização de Rotas de Transporte e Logística**

* Empresas de logística usam AEs para resolver **problemas de roteamento de veículos (VRP)**, encontrando a rota mais rápida e barata para entregas.
* Exemplo: caminhões de frota que precisam visitar vários pontos sem gastar combustível em excesso.
  🔗 [Vehicle Routing Problem with Genetic Algorithms](https://scholar.google.com.br/scholar?as_ylo=2021&q=Vehicle+Routing+Problem+with+Genetic+Algorithms&hl=pt-BR&as_sdt=0,5)

---

### 2. **Design de Antenas pela NASA**

* A NASA usou **algoritmos genéticos** para projetar antenas de espaçonaves.
* O processo evolutivo gerou formatos inovadores que engenheiros humanos dificilmente criariam sozinhos.
  🔗 [Antenna Design by Genetic Algorithm](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=NASA+Antenna+Evolved+by+Genetic+Algorithms&btnG=)

---

### 3. **Descoberta de Novos Medicamentos**

* AEs são aplicados em **química computacional** para buscar moléculas candidatas a medicamentos.
* Eles exploram milhões de combinações químicas e evoluem as mais promissoras.
  🔗 [Evolutionary Algorithms in Drug Discovery](https://scholar.google.com.br/scholar?hl=pt-BR&as_sdt=0%2C5&as_ylo=2021&q=Evolutionary+Algorithms+in+Drug+Discovery&btnG=)

---

### 4. **Otimização de Hiperparâmetros em Redes Neurais / NLP**

* Em **IA moderna**, AEs são usados para ajustar automaticamente parâmetros de redes neurais (learning rate, número de camadas, funções de ativação).
* Também já foram aplicados para **evoluir prompts em LLMs**, aumentando desempenho em tarefas de NLP.
  🔗 [Evolutionary Algorithms for Neural Architecture Search (arXiv)](https://arxiv.org/abs/1808.05377)

---
