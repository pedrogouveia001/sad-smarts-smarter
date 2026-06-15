# Nexus SMARTS/SMARTER — Elicitação Direta e Ordinal

Este repositório é o módulo independente do ecossistema **NEXUS MCDM**, configurado para operar exclusivamente com os métodos **SMARTS** e **SMARTER**.

---

## 🎨 Identidade Visual e Branding
- **Nome Oficial:** Nexus SMARTS/SMARTER
- **Cores Oficiais:** Teal (`#0D9488`) e Prata/Slate (`#94A3B8`)
- **Conceito Visual:** Balança de pesos equilibrada simbolizando a elicitação simplificada e precisa de pesos de critérios.
- **Copyright:** Direitos Reservados © 2026 NEXUS-MCDM. Todos os direitos reservados.

---

## 🧠 Formulação Matemática e Funcionamento

### 1. SMARTS (Simple Multi-Attribute Rating Technique with Swing)
O método SMARTS utiliza a elicitação direta baseada em swings. O decisor classifica a variação da pior para a melhor situação física em cada critério.

#### Passos do Algoritmo:
1. Identifica-se o critério onde a melhoria do pior para o melhor estado físico é a mais desejada pelo decisor. A esse critério atribui-se uma nota de $100$ (swing de referência).
2. O decisor atribui notas de $0$ a $100$ para os swings dos demais critérios, proporcionalmente ao swing de referência.
3. Os pesos normalizados dos critérios ($w_j$) são calculados como:
   $$w_j = \frac{p_j}{\sum_{k=1}^n p_k}$$
   Onde $p_j$ é a pontuação direta (swing) atribuída ao critério $j$.

#### Normalização Unidimensional das Consequências:
As consequências físicas de cada alternativa $i$ no critério $j$ ($x_{ij}$) são normalizadas linearmente em utilidades $u_{ij} \in [0, 1]$:
* **Para Critérios de Maximização (Benefício):**
  $$u_{ij} = \frac{x_{ij} - x_j^{\min}}{x_j^{\max} - x_j^{\min}}$$
* **Para Critérios de Minimização (Custo):**
  $$u_{ij} = \frac{x_j^{\max} - x_{ij}}{x_j^{\max} - x_j^{\min}}$$

#### Agregação de Utilidade:
A utilidade global da alternativa $A_i$ é calculada de forma aditiva:
  $$V(A_i) = \sum_{j=1}^n w_j \cdot u_{ij}$$

---

### 2. SMARTER (Simple Multi-Attribute Rating Technique Exploiting Ranks)
O SMARTER simplifica o processo de elicitação reduzindo a carga cognitiva do decisor. Ele requer apenas a ordenação dos critérios em ordem de importância.

#### Pesos ROC (Rank Order Centroid):
Os pesos são extraídos da geometria de um simplex n-dimensional, gerando os centróides geométricos:
  $$w_j = \frac{1}{n} \sum_{k=j}^n \frac{1}{k}$$
Onde:
* $n$ é o número de critérios.
* $j$ é a posição de importância do critério (1º, 2º, ...).

#### Tabela de Pesos ROC Exemplos:
* Para $n = 3$:
  * $w_1 = \frac{1}{3} \cdot (1 + \frac{1}{2} + \frac{1}{3}) = 0.6111$
  * $w_2 = \frac{1}{3} \cdot (\frac{1}{2} + \frac{1}{3}) = 0.2778$
  * $w_3 = \frac{1}{3} \cdot (\frac{1}{3}) = 0.1111$

A normalização e agregação de utilidades do SMARTER seguem as mesmas equações lineares e aditivas do SMARTS.

---

## 🚀 Instalação e Execução
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```
Acesse: `http://127.0.0.1:5000`
