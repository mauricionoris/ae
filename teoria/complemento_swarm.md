
# PSO — Particle Swarm Optimization

**Ideia:** cada “partícula” é uma solução. Elas “voam” pelo espaço de busca trocando informação sobre o melhor ponto já visto.

**Equações (contínuas):**

$$
v_i \leftarrow \omega v_i + c_1 r_1 (pbest_i - x_i) + c_2 r_2 (gbest - x_i)
$$

$$
x_i \leftarrow x_i + v_i
$$

**Parâmetros típicos:**

* $\omega$ (inércia): 0.4–0.9
* $c_1, c_2$ (cognitivo/social): ~2.0 cada
* Limites: restringir $||v||$ e manter $x$ dentro dos bounds

**Vantagens:** simples, poucas hiper-configs, ótimo para **variáveis contínuas** e funções sem gradiente.
**Limitações:** pode **estagnar**; requer adaptação para **variáveis discretas**.

---

# ACO — Ant Colony Optimization

**Ideia:** formigas constroem soluções passo a passo, guiadas por **feromônio** (memória coletiva) e **heurística local**; trilhas boas recebem mais feromônio, reforçando caminhos promissores.

**Probabilidade de escolher componente $j$ a partir de $i$:**

$$
P_{ij} = \frac{ \tau_{ij}^{\alpha} , \eta_{ij}^{\beta} }
{\sum_{k \in \text{vizinhos}(i)} \tau_{ik}^{\alpha} , \eta_{ik}^{\beta}}
$$

onde:

* $\tau_{ij}$ = quantidade de feromônio na aresta/decisão
* $\eta_{ij}$ = informação heurística (ex.: $1/\text{distância}$ no TSP)
* $\alpha$, $\beta$ = pesos (tipicamente 1–2)

**Atualização do feromônio (com evaporação $\rho$):**

$$
\tau_{ij} \leftarrow (1 - \rho),\tau_{ij} + \sum_{k} \Delta\tau_{ij}^{(k)}
$$

$$
\Delta\tau_{ij}^{(k)} =
\begin{cases}
\dfrac{Q}{\text{custo}_k}, & \text{se } (i,j) \in \text{solução de } k [6pt]
0, & \text{caso contrário}
\end{cases}
$$

**Vantagens:** ótimo para **problemas combinatórios/discretos** (TSP, roteamento).
**Limitações:** mais hiperparâmetros e custo computacional maior.

---

# Quando usar qual

| Situação                          | Melhor escolha     |
| --------------------------------- | ------------------ |
| Funções contínuas, sem gradiente  | **PSO**            |
| Problemas discretos/combinatórios | **ACO**            |
| Espaço multimodal pesado          | PSO ou ACO híbrido |

---

# Pseudocódigo

**PSO:**

```text
inicialize partículas x_i ~ Uniform(bounds), v_i = 0
avalie f(x_i); pbest_i = x_i; gbest = argmin f(x_i)
repita até parar:
  para cada partícula i:
    v_i = ω v_i + c1*r1*(pbest_i - x_i) + c2*r2*(gbest - x_i)
    x_i = clip(x_i + v_i, bounds)
    se f(x_i) < f(pbest_i): pbest_i = x_i
  gbest = melhor pbest
```

**ACO (exemplo TSP):**

```text
inicialize τ_ij = τ0
repita até parar:
  para cada formiga k:
    construa rota escolhendo próxima cidade por
      P_ij ∝ τ_ij^α * η_ij^β   (η_ij = 1 / distancia_ij)
  evapore τ_ij ← (1 - ρ) * τ_ij
  para as melhores soluções S:
    para cada aresta (i,j) ∈ S: τ_ij += Q / custo(S)
```

---

# Boas práticas

* Critérios de parada: iterações, convergência, orçamento.
* Normalizar variáveis contínuas (ex.: $[0,1]$).
* Rodar múltiplas execuções com diferentes sementes.
* Monitorar diversidade populacional.

---
