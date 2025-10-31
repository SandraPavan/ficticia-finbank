# 🧩 Mapa de Causas e Ações de Qualidade – FinBank

**Linha lógica:** Problema → Causa → Ação de Qualidade → Indicador de Sucesso  
**Objetivo:** Consolidar percepções e definir ações práticas de melhoria.

---

| 🧠 Categoria        | ❌ Problema (Sintoma)                  | ⚙️ Causa Raiz Identificada                | 💡 Ação de Qualidade Proposta                                              | 📊 Indicador / Meta de Sucesso                  |
|---------------------|----------------------------------------|-------------------------------------------|----------------------------------------------------------------------------|-------------------------------------------------|
| Processo            | Testes manuais demorados e inconsistentes | Falta de automação e critérios de aceite claros | Implementar smoke tests e regressões automatizadas em cada PR              | Reduzir tempo de testes de 5 dias → 1,5 dia     |
| Técnica             | Falhas intermitentes em /transactions  | Endpoint instável e sem mocks para dados  | Criar mocks locais via JSON Server e simular picos de carga no pipeline    | 95% de estabilidade nos testes                  |
| Comunicação         | QA e Dev trabalham em silos            | QA entra apenas no final da sprint         | Introduzir pair review QA–Dev e check de qualidade antes do merge          | Retrabalho < 10% das histórias                  |
| Infraestrutura      | Testes falham por ambiente indisponível | Falta de pipeline de provisionamento e ambientes efêmeros | Automatizar subida de ambiente de teste via Docker Compose no CI           | Menos falhas por ambiente                           |
| Negócio             | Retrabalho alto e bugs caros em produção | Falta de priorização de risco e ausência de KPIs de qualidade | Criar matriz de risco (impacto × probabilidade) e dashboard de automação   | Falhas críticas ↓ 70% em 3 sprints              |
| Governança          | Falta de visibilidade do progresso da automação | Execuções sem report consolidado         | Integrar Allure Reports + pipeline YAML + dashboards Grafana               | Tempo de feedback CI/CD ≤ 30 min                |
| Cultura / Pessoas   | Qualidade vista como “tarefa do QA”    | Falta de cultura de ownership e visibilidade dos ganhos | Workshop interno “Qualidade é de Todos” + rotação de papéis QA/Dev        | Times com 100% de participação no plano de testes|

---
