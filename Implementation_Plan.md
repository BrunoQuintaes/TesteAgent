---
title: Implementation_Plan
project: HRP-βdin Thesis Framework
author: Bruno Liblik Quintaes
repo_root: /
memory_strategy: dynamic-json
asset_format: md & json
version: 0.2
created: 2025-07-29
last_updated: 2025-07-29
---

# 1. Visão Geral

Este plano descreve as etapas, entregáveis, responsabilidades e checkpoints necessários
para entregar em 8 meses (~32 semanas) a tese “Algoritmos Adaptativos de Otimização de
Carteiras Multiclasse…”, conforme requisitos sintetizados.

# 2. Work Breakdown Structure (WBS)

| Fase | Marco | Entregáveis (principais) | Dependências | Duração (sem.) |
|------|-------|--------------------------|--------------|----------------|
| **F0** | Preparação | Estrutura repositório, env., CI básico | – | **2** |
| **F1** | M2 | Teste híbrido ADF-PP + Cap. 2 | F0 | **6** |
| **F2** | M3 | Scraping + Métrica Web (BTC/ETH) | F1 | **6** |
| **F3** | M4 | Pipeline ARIMA-GARCH-X | F2 | **4** |
| **F4** | M5 | VAR/SVAR + ICI | F3 | **3** |
| **F5** | M6 | HRP clássico + βdin | F4 | **4** |
| **F6** | M7 | Backtests 2008-2024 + relatório | F5 | **4** |
| **F7** | M8 | Dashboard Streamlit + Dockerfile | F6 | **3** |
| **F8** | M9 | Manuscrito LaTeX + README + licença | F7 | **3** |
| **F9** | M10 | Slides defesa + repo público | F8 | **2** |

> Buffer global: 2 semanas.

# 3. Dependências Críticas

* Dados históricos: Yahoo Finance / Quandl antes de F3
* Limite de tokens OpenAI controlado
* Twitter upgrade avaliado ao fim de F2
* Testes unitários antes de PR merge

# 4. Métricas de Sucesso & Validação

| Métrica | Meta HRP-βdin | Checkpoint |
|---------|---------------|------------|
| Sharpe / Sortino | ≥ +10 % vs HRP puro | F6 |
| Information Ratio | ≥ +10 % vs HRP puro | F6 |
| Omega Ratio | ≥ +10 % vs HRP puro | F6 |
| CVaR 5 % & Máx Drawdown | ≤ −10 % vs HRP puro | F6 |
| Turnover | ≤ 1.5 × benchmark | F6 |
| Cobertura de testes | ≥ 70 % linhas | F-fim |
| Lint (flake8) | zero erros críticos | CI |

# 5. Riscos & Mitigações

* APIs instáveis / quotas → cache local + fallback RSS
* Performance CPU em NLP → execução batelada ou Colab GPU
* Complexidade βdin → validar HRP base primeiro
* Sobrecarga GPT-4 tokens → otimização de prompts

# 6. Colaboração & CI/CD

* Branches: main, dev/<fase>, PR obrigatório
* GitHub Actions: lint, pytest, json-schema-validate, build-docker (F7+)
* Code owners: autor principal; orientador revisor em main

# 7. Memory System

* Estratégia: dynamic-json
* memory/dynamic.json – registros públicos estruturados
* memory/private/ – ignorado via .gitignore

# 8. Cronograma Gantt (resumido)

```
Sem  1–2 : F0
Sem  3–8 : F1
Sem  9–14: F2
Sem 15–18: F3
Sem 19–21: F4
Sem 22–25: F5
Sem 26–29: F6
Sem 30–32: F7
Sem 33–35: F8
Sem 36–37: F9 + buffer
```

# 9. Próximos Passos

* Aprovação do plano (já obtida)
* Iniciar F0: setup de pastas, env, CI
