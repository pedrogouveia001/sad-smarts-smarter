# Nexus SMARTS/SMARTER — Elicitação Direta e Ordinal

Este repositório é o módulo independente do ecossistema **NEXUS MCDM**, configurado para operar exclusivamente com os métodos **SMARTS** e **SMARTER**.

---

## 🎨 Identidade Visual e Branding
- **Nome Oficial:** Nexus SMARTS/SMARTER
- **Cores Oficiais:** Teal (`#0D9488`) e Prata/Slate (`#94A3B8`)
- **Conceito Visual:** Balança de pesos equilibrada simbolizando a elicitação simplificada e precisa de pesos de critérios.
- **Copyright:** Direitos Reservados © 2026 NEXUS-MCDM.

---

## 🌟 Recursos e Matemática

- **SMARTS (Swing Weighting):** Permite ao decisor atribuir notas de 0 a 100 baseadas no impacto do swing (variação da pior para a melhor consequência). A normalização dos critérios é linear:
  - *Benefício:* `r_ij = (x_ij - min_j) / (max_j - min_j)`
  - *Custo:* `r_ij = (max_j - x_ij) / (max_j - min_j)`
- **SMARTER (ROC Weights):** O decisor apenas ordena os critérios por importância ordinal. Os pesos são calculados pela fórmula centróide:
  - `w_j = (1 / n) * Sum_{k=r_j}^n (1 / k)`
- **Simulador Monte Carlo & Relatório PDF:** Exporta relatórios técnicos completos e simula perturbações de peso.

---

## 🚀 Instalação e Execução
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```
