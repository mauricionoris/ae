

#  Estratégias Evolutivas (Evolution Strategies — ES)

**Família:** Algoritmos Evolutivos
**Inspiração:** processo de **seleção natural** e **mutação adaptativa** em organismos biológicos.
**Objetivo:** otimizar funções contínuas (sem necessidade de gradiente).

---

##  Conceito básico

Cada indivíduo representa uma **solução candidata** (vetor real).
A população evolui por **reprodução**, **mutação** e **seleção**.

Ao contrário dos Algoritmos Genéticos (GA), as **Estratégias Evolutivas** enfatizam a **mutação contínua** e a **adaptação automática da variância**.

---

## Representação de um indivíduo

Um indivíduo é descrito por:
$$
(x, \sigma)
$$
onde:

* $x = (x_1, x_2, \dots, x_n)$ → vetor de variáveis (solução)
* $\sigma = (\sigma_1, \sigma_2, \dots, \sigma_n)$ → desvios padrão (passos de mutação)

Esses $\sigma_i$ são **auto-adaptativos** — evoluem junto com a solução.

---

##  Mecanismos principais

### 1 Recombinação (opcional)

Pode ser **global** ou **local**:
$$
x_i' = \frac{1}{p} \sum_{k=1}^{p} x_i^{(k)}
$$
onde $p$ é o número de pais.
Pode-se aplicar recombinação também aos $\sigma_i$.

---

### 2️ Mutação (núcleo do método)

A mutação é **gaussiana**, controlada por $\sigma$:

$$
\sigma_i' = \sigma_i \cdot e^{\tau' N(0,1) + \tau N_i(0,1)}
$$

$$
x_i' = x_i + \sigma_i' \cdot N_i(0,1)
$$

onde:

* $N(0,1)$ = variável aleatória normal
* $\tau' = \frac{1}{\sqrt{2n}}$, $\tau = \frac{1}{\sqrt{2\sqrt{n}}}$ → fatores de ajuste recomendados

 **Auto-adaptação:** $\sigma$ se ajusta conforme a evolução progride — aumentando diversidade quando necessário, reduzindo ao se aproximar do ótimo.

---

### 3️ Seleção

Dois esquemas clássicos:

#### a) $(\mu, \lambda)$-ES

* Geram-se $\lambda$ descendentes de $\mu$ pais.
* Apenas os **descendentes** competem.
* Fortemente seletivo (melhor para exploração).

$$
\text{Seleção: } \text{escolher os } \mu \text{ melhores de } \lambda
$$

#### b) $(\mu + \lambda)$-ES

* Pais e filhos competem juntos.
* Mais estável, favorece convergência suave.

$$
\text{Seleção: } \text{escolher os } \mu \text{ melhores de } (\mu + \lambda)
$$

---

##  Pseudocódigo

```text
Inicialize μ indivíduos (x, σ)
Avalie f(x) para todos

repita até o critério de parada:
  Recombine pais (opcional)
  Mutação gaussiana para gerar λ descendentes
  Avalie f(x') para os λ descendentes
  Selecione os μ melhores:
      (μ, λ)-ES → apenas descendentes
      (μ + λ)-ES → pais + descendentes
retorne o melhor indivíduo
```

---

##  Parâmetros típicos

| Parâmetro        | Significado          | Valor sugerido                                    |
| ---------------- | -------------------- | ------------------------------------------------- |
| $\mu$            | número de pais       | 10–50                                             |
| $\lambda$        | número de filhos     | $5 \times \mu$                                    |
| $\tau', \tau$    | fatores de adaptação | $\frac{1}{\sqrt{2n}}, \frac{1}{\sqrt{2\sqrt{n}}}$ |
| $\sigma$ inicial | passo de mutação     | 0.1 a 0.3 do range da variável                    |

---

##  Vantagens

- Adaptativo: ajusta escala de busca automaticamente
- Eficiente para otimização contínua sem gradiente
- Bom equilíbrio entre exploração e exploração local
- Fácil paralelização (avaliações independentes)

---

##  Limitações

- Convergência lenta em funções altamente multimodais
- Menos eficiente em problemas discretos
- Sensível ao dimensionamento das variáveis

---

##  Aplicações típicas

* Ajuste de hiperparâmetros em modelos sem gradiente
* Otimização de parâmetros de controle e engenharia
* Funções objetivo ruidosas ou não diferenciáveis
* Treinamento de redes neurais evolutivas (ex.: NES, CMA-ES)

---

## Extensões modernas

###  CMA-ES (Covariance Matrix Adaptation ES)

Atualiza a **matriz de covariância** das mutações — permitindo explorar correlações entre variáveis.
É o **estado da arte** em otimização sem gradiente contínua.

###  NES (Natural Evolution Strategies)

Usa **gradiente natural** para atualizar uma distribuição de busca paramétrica.

---

## Resumo rápido

| Tipo                 | Seleção                | Adaptação           | Melhor para                       |
| -------------------- | ---------------------- | ------------------- | --------------------------------- |
| $(1+1)$-ES           | elitista simples       | $\sigma$ adaptativo | problemas pequenos                |
| $(\mu, \lambda)$-ES  | descendentes apenas    | auto-adaptação      | exploração ampla                  |
| $(\mu + \lambda)$-ES | pais + filhos          | auto-adaptação      | estabilidade                      |
| CMA-ES               | covariância adaptativa | global              | alta dimensão / funções complexas |

