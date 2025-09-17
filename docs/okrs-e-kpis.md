# OKRs - Objetivos de análise

**Objetivo O1 — Observar a dinâmica da base de beneficiários**

- KR1: Observar **Net Adds** (quantidade de novos clientes) mensal por UF.
- KR2: Expor os **Churn** e **Retention** mensais por UF.
- KR3: Compreender o **Market Share** por UF/município.

**Objetivo O2 — Identificar riscos e oportunidades de crescimento**

- KR4: Ranquear **UF/municípios** com maior crescimento ou retração (MoM e YoY).
- KR5: Mapear **mix demográfico** (sexo/idade) e lacunas regionais de cobertura.

**Objetivo O3 — Embasar decisões regulatórias e de produto**

- KR6: Evidenciar **concentração de operadoras** por praça e possíveis áreas de **subatendimento**.

# KPIs

1. **Beneficiários Ativos (Base)**
    - **KPI:** `Base_Ativos_m = Σ(quantidade_beneficiario_ativo)`
2. **Aderidos (Novos Entrantes)**
    - **KPI:** `Aderidos_m = Σ(quantidade_beneficiario_aderido)`
3. **Cancelados (Saídas)**
    - **KPI:** `Cancelados_m = Σ(quantidade_beneficiario_cancelado)`
4. **Net Adds (Variação Líquida)**
    - **KPI:** `NetAdds_m = Aderidos_m − Cancelados_m`
5. **Crescimento MoM da Base**
    - `Growth_MoM = (Base_Ativos_m − Base_Ativos_{m−1}) / Base_Ativos_{m−1}`
    - Observação: quando houver mudança de cobertura/planos que alterem a composição, sinalizar no tooltip.
6. **Crescimento YoY da Base**
    - `Growth_YoY = (Base_Ativos_m − Base_Ativos_{m−12}) / Base_Ativos_{m−12}`
7. **Churn Rate Mensal** *(definição operacional)*
    - `Churn_m = Cancelados_m / Base_Ativos_{m−1}`
    - Alternativa conservadora: usar denominador `avg(Base_Ativos_{m−1}, Base_Ativos_m)` para suavizar.
8. **Retention Rate**
    - `Retention_m = 1 − Churn_m`
9. **Take-up / Adesão Relativa**
    - `TakeUp_m = Aderidos_m / Base_Ativos_{m−1}`
10. **Market Share por Região (UF/Município)**
    - `MS_operadora,região,m = Base_Ativos_operadora,região,m / Σ(Base_Ativos_todas_operadoras,região,m)`
11. **Mix Demográfico**
    - **% por Sexo:** `Base_Ativos_sexo / Base_Ativos_total`
    - **% por Faixa Etária:** `Base_Ativos_faixa / Base_Ativos_total`
12. **Mix de Produto**
    - Por `modalidade_operadora`, `segmentacao_beneficiario`, `contratacao_beneficiario`, `abrangencia_beneficiario`, `cobertura_assistencia_beneficiario`, `tipo_vinculo`:
        - `%_Mix = Base_Ativos_dim / Base_Ativos_total`

> KPIs “premium” opcionais (se você integrar dados externos):
> 
> - **Penetração** = `Base_Ativos_região / População_região (IBGE)`.
> - **Índice de Concentração (HHI)** por UF para avaliar concorrência.
> - **Sazonalidade** via decomposição (STL) de `NetAdds_m`.