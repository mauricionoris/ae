
## Métodos de Seleção Genética – Explicação e Aplicação

### 1. Seleção por Ranking (Ranking Selection)

**Como funciona:**
Os indivíduos são ordenados de acordo com sua aptidão, e as probabilidades de seleção são atribuídas com base na posição no ranking, e não no valor absoluto da aptidão. Assim, mesmo indivíduos menos aptos ainda têm alguma chance de serem escolhidos.

**Vantagens:**
Evita que indivíduos muito bons dominem a população logo no início (o que causaria convergência prematura).
Proporciona um controle mais equilibrado da pressão seletiva.

**Indicado quando:**
O problema apresenta diferenças muito grandes entre os valores de fitness, e se deseja **evitar elitismo excessivo** e **preservar a diversidade genética**.

---

### 2. Seleção por Elitismo (Elitist Selection)

**Como funciona:**
Os melhores indivíduos de uma geração são automaticamente preservados para a próxima, garantindo que o desempenho da população nunca piore de uma geração para outra. É normalmente usada em conjunto com outros métodos de seleção.

**Vantagens:**
Garante que as melhores soluções encontradas até o momento não sejam perdidas durante cruzamento ou mutação.

**Indicado quando:**
É importante **garantir progresso constante** e **preservar soluções ótimas**, como em problemas de otimização de alto custo computacional (por exemplo, otimização de parâmetros em engenharia).

---

### 3. Seleção Estocástica Universal (Stochastic Universal Sampling – SUS)

**Como funciona:**
É uma variação da seleção por roleta. Em vez de sortear indivíduos um por um, o método usa uma linha de seleção com vários “pontos” igualmente espaçados, garantindo que a amostragem seja mais uniforme e representativa da população.

**Vantagens:**
Reduz a variância no processo de seleção e assegura que a proporção de indivíduos escolhidos reflita fielmente a distribuição de fitness.

**Indicado quando:**
Se busca **amostragem mais estável** e **diversidade genética equilibrada**, como em problemas com populações pequenas ou sujeitos a flutuações aleatórias.

---

### 4. Seleção por Bolsa de Sobrevivência (Steady-State Selection)

**Como funciona:**
Em vez de substituir toda a população a cada geração, apenas alguns indivíduos são substituídos (geralmente os menos aptos). Os novos descendentes ocupam as posições desses indivíduos.

**Vantagens:**
Mantém maior estabilidade e diversidade genética, pois boas soluções permanecem na população por mais tempo.

**Indicado quando:**
Se deseja **evolução contínua e gradual**, típica de aplicações de aprendizado contínuo, controle adaptativo ou problemas que exigem convergência mais lenta e estável.

---

### 5. Seleção por Torneio Estocástico (Stochastic Tournament)

**Como funciona:**
Dois ou mais indivíduos são selecionados aleatoriamente para um “torneio”. Normalmente, o mais apto vence, mas com uma pequena probabilidade o menos apto também pode ser escolhido. Essa aleatoriedade reduz o risco de convergência precoce.

**Vantagens:**
Combina **pressão seletiva ajustável** (via probabilidade de vitória) e **diversidade controlada**, mantendo o equilíbrio entre exploração e intensificação.

**Indicado quando:**
É importante **evitar convergência prematura** e **preservar diversidade**, como em problemas com muitos ótimos locais ou funções multimodais.

---

### 6. Seleção por Idade (Age-Based Selection)

**Como funciona:**
A sobrevivência dos indivíduos depende não apenas da aptidão, mas também da idade. Indivíduos mais antigos são gradualmente removidos, permitindo a entrada constante de novos indivíduos na população.

**Vantagens:**
Promove renovação genética e evita que o algoritmo fique preso em soluções antigas.

**Indicado quando:**
Deseja-se **estimular inovação e diversidade**, especialmente em problemas complexos ou de longa duração, como evolução de arquiteturas de redes neurais, design de sistemas ou otimização dinâmica.

| Método                                          | Como funciona                                                                                                                 | Principais vantagens                                                                    | Quando é mais indicado                                                                             |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Ranking (Ranking Selection)**                 | Ordena os indivíduos pela aptidão e atribui probabilidade proporcional à posição no ranking.                                  | Controla a pressão seletiva e evita que poucos indivíduos dominem a população.          | Quando há grandes diferenças de fitness e se deseja preservar a diversidade genética.              |
| **Elitismo (Elitist Selection)**                | Mantém automaticamente os melhores indivíduos de uma geração para a próxima.                                                  | Garante que o desempenho da população não piore e preserva soluções de alta qualidade.  | Quando é necessário garantir progresso contínuo ou evitar perda de boas soluções.                  |
| **Estocástica Universal (SUS)**                 | Seleciona múltiplos indivíduos de forma uniforme, distribuindo pontos igualmente na roleta de seleção.                        | Reduz a variância e torna a seleção mais estável e representativa.                      | Quando se busca amostragem equilibrada e diversidade em populações pequenas.                       |
| **Bolsa de Sobrevivência (Steady-State)**       | Apenas alguns indivíduos menos aptos são substituídos por novos descendentes a cada geração.                                  | Mantém estabilidade e diversidade genética ao longo da execução.                        | Quando se deseja evolução contínua e gradual, com mudanças suaves na população.                    |
| **Torneio Estocástico (Stochastic Tournament)** | Realiza torneios entre indivíduos; o mais apto tende a vencer, mas o menos apto pode ser escolhido com pequena probabilidade. | Ajusta a pressão seletiva e reduz a chance de convergência prematura.                   | Quando o problema tem muitos ótimos locais ou requer equilíbrio entre exploração e intensificação. |
| **Por Idade (Age-Based Selection)**             | A sobrevivência depende também da idade; indivíduos mais velhos são substituídos por novos.                                   | Favorece a renovação genética e impede que a população fique presa em soluções antigas. | Quando se busca inovação constante e diversidade em problemas de longa duração ou dinâmicos.       |


