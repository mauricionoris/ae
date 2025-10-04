Perfeito 👍 — aqui está a versão **sem ícones** (apenas texto puro), totalmente compatível com **GitHub Markdown**,
e com **todas as fórmulas renderizadas** como imagens (funcionam em qualquer README.md):

---

# Estratégias Evolutivas (Evolution Strategies — ES)

- **Família:** Algoritmos Evolutivos
- **Inspiração:** processo de seleção natural e mutação adaptativa em organismos biológicos.
- **Objetivo:** otimizar funções contínuas sem necessidade de gradiente.

---

## Conceito básico

Cada indivíduo representa uma solução candidata (vetor real).
A população evolui por reprodução, mutação e seleção.

As Estratégias Evolutivas (ES) enfatizam a mutação contínua e a auto-adaptação da variância (passo de busca).

---

## Representação de um indivíduo

Um indivíduo é descrito por:

![equation](https://render.githubusercontent.com/render/math?math=\(x%2C%20\sigma\))

onde:

* `x = (x₁, x₂, …, xₙ)` → vetor de variáveis (solução)
* `σ = (σ₁, σ₂, …, σₙ)` → desvios padrão (passos de mutação)

Esses `σᵢ` evoluem junto com a solução — são auto-adaptativos.

---

## Mecanismos principais

### 1. Recombinação (opcional)

Pode ser global ou local:

![equation](https://render.githubusercontent.com/render/math?math=x_i'%20=%20\frac{1}{p}%20\sum_{k=1}^{p}%20x_i^{\(k\)})

onde `p` é o número de pais.
Também pode-se recombinar os valores de `σᵢ`.

---

### 2. Mutação (núcleo do método)

A mutação é gaussiana, controlada por `σ`:

![equation](https://render.githubusercontent.com/render/math?math=\sigma_i'%20=%20\sigma_i%20\cdot%20e^{\tau'%20N\(0%2C1\)%20+%20\tau%20N_i\(0%2C1\)})

![equation](https://render.githubusercontent.com/render/math?math=x_i'%20=%20x_i%20+%20\sigma_i'%20\cdot%20N_i\(0%2C1\))

onde:

* `N(0,1)` é uma variável aleatória normal
* `τ' = 1 / √(2n)` e `τ = 1 / √(2√n)` são fatores de ajuste recomendados

A auto-adaptação permite que `σ` aumente a diversidade quando necessário e diminua ao se aproximar do ótimo.

---

### 3. Seleção

Dois esquemas clássicos:

#### a) (μ, λ)-ES

* Geram-se `λ` descendentes de `μ` pais.
* Apenas os descendentes competem.
* Fortemente seletivo (melhor para exploração).

![equation](https://render.githubusercontent.com/render/math?math=\text{Seleção%3A%20escolher%20os%20}%5Cmu%20\text{%20melhores%20de%20}%5Clambda)

#### b) (μ + λ)-ES

* Pais e filhos competem juntos.
* Mais estável, favorece convergência suave.

![equation]([https://render.githubusercontent.com/render/math?math=\text{Seleção%3A%20escolher%20os%20}%5Cmu%20\text{%20melhores%20de%20}(](https://render.githubusercontent.com/render/math?math=\text{Seleção%3A%20escolher%20os%20}%5Cmu%20\text{%20melhores%20de%20}%28) \mu%20+%20\lambda))

---

## Pseudocódigo

```text
Inicialize μ indivíduos (x, σ)
Avalie f(x) para todos

Repita até o critério de parada:
  Recombine pais (opcional)
  Aplique mutação gaussiana para gerar λ descendentes
  Avalie f(x') para os λ descendentes
  Selecione os μ melhores:
      (μ, λ)-ES → apenas descendentes
      (μ + λ)-ES → pais + descendentes

Retorne o melhor indivíduo
```

---

## Parâmetros típicos

| Parâmetro | Significado          | Valor sugerido                 |
| --------- | -------------------- | ------------------------------ |
| μ         | número de pais       | 10–50                          |
| λ         | número de filhos     | 5 × μ                          |
| τ', τ     | fatores de adaptação | 1/√(2n), 1/√(2√n)              |
| σ inicial | passo de mutação     | 0.1 a 0.3 do range da variável |

---

## Vantagens

* Adaptativo: ajusta a escala de busca automaticamente
* Eficiente para otimização contínua sem gradiente
* Bom equilíbrio entre exploração e refinamento local
* Fácil paralelização (avaliações independentes)

---

## Limitações

* Convergência lenta em funções altamente multimodais
* Menos eficiente em problemas discretos
* Sensível ao escalonamento das variáveis

---

## Aplicações típicas

* Ajuste de hiperparâmetros em modelos sem gradiente
* Otimização de parâmetros de controle e engenharia
* Funções objetivo ruidosas ou não diferenciáveis
* Treinamento de redes neurais evolutivas (ex.: NES, CMA-ES)

---

## Extensões modernas

### CMA-ES (Covariance Matrix Adaptation ES)

Atualiza a matriz de covariância das mutações — permitindo explorar correlações entre variáveis.
É o estado da arte em otimização sem gradiente contínua.

### NES (Natural Evolution Strategies)

Usa gradiente natural para atualizar uma distribuição de busca paramétrica.

---

## Resumo rápido

| Tipo       | Seleção                | Adaptação      | Melhor para                       |
| ---------- | ---------------------- | -------------- | --------------------------------- |
| (1+1)-ES   | elitista simples       | σ adaptativo   | problemas pequenos                |
| (μ, λ)-ES  | descendentes apenas    | auto-adaptação | exploração ampla                  |
| (μ + λ)-ES | pais + filhos          | auto-adaptação | estabilidade                      |
| CMA-ES     | covariância adaptativa | global         | alta dimensão / funções complexas |

---

Deseja que eu gere o mesmo estilo para **PSO** e **ACO** (com fórmulas em imagem compatíveis com GitHub também)?
Posso unificar tudo em um único documento Markdown técnico.
