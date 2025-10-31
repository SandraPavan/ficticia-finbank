# 💡 1. Objetivo da Apresentação

Demonstrar o retorno sobre investimento (ROI) da automação dos testes dos principais endpoints do Core Banking da FinBank, destacando:

- Redução de custos com testes manuais e retrabalho.
- Diminuição de falhas em produção e incidentes financeiros.
- Aceleração das releases com qualidade assegurada.

---

# 📊 2. Cálculo do ROI

**Fórmula base:**

$$
\text{ROI} = \frac{\text{Benefício líquido da automação} - \text{Custo de implementação}}{\text{Custo de implementação}} \times 100
$$

**Exemplo prático (para o conjunto de 8 endpoints):**

| Item                        | Descrição                                               | Valor estimado (R$) |
|-----------------------------|---------------------------------------------------------|---------------------|
| 💰 Custo de automação       | Desenvolvimento dos scripts, setup CI/CD, manutenção trimestral | 40.000              |
| 💵 Custo manual (antes)     | Testes manuais recorrentes em cada release (4 releases/ano)    | 80.000              |
| ⚙️ Economia anual com automação | 80.000 – 40.000 = 40.000                              |                     |
| ⚡ Benefício adicional       | Menor retrabalho, incidentes evitados, etc.             | +20.000             |
| 📈 ROI final                | ((60.000 – 40.000) / 40.000) × 100 = +50%               |                     |

---

# 🧩 3. Métricas de Valor por Endpoint

| Endpoint                  | Tipo de Teste           | Risco / Impacto                | Frequência de Execução | Economia (%) | Benefício específico                                      |
|--------------------------|-------------------------|-------------------------------|-----------------------|--------------|-----------------------------------------------------------|
| POST /accounts           | Regressão + Contrato    | Alto (duplicidade e idempotência) | 4x/dia (CI/CD)        | 30%          | Evita contas duplicadas sob carga e falhas de criação.     |
| POST /transactions       | Performance + Concorrência | Muito alto (race conditions) | 6x/dia                | 45%          | Detecção precoce de falhas de rollback sob carga.          |
| GET /balance/{id}        | Smoke + Regressão       | Médio (sincronização)          | 10x/dia               | 20%          | Garantia de saldo correto pós-transação.                   |
| GET /transactions        | Performance             | Alto                          | 2x/dia                | 35%          | Detecta falhas de paginação e lentidão sob volume.         |
| POST /billing            | Contrato + Negócio      | Alto                          | 2x/dia                | 40%          | Previne boletos inválidos e perdas financeiras.            |
| POST /auth/login         | Segurança + Regressão   | Muito alto                    | 12x/dia               | 50%          | Evita acessos indevidos e tokens inválidos.                |
| PATCH /accounts/{id}/limit | Regressão + Segurança | Alto                          | 3x/dia                | 25%          | Evita falhas de permissão e versionamento.                 |
| GET /reports/summary     | Validação de dados      | Alto                          | 1x/dia                | 40%          | Evita inconsistência de dados financeiros e erros em dashboards. |

---

# 📉 4. Indicadores de Eficiência e Impacto

| Indicador                        | Antes da Automação | Depois da Automação | 
|----------------------------------|--------------------|---------------------|
| ⏱ Tempo de execução de testes    | 10h por ciclo      | 1h (automatizado)   | 
| 💼 Esforço de QA manual          | 4 QAs x 2 dias     | 1 QA x 2h           | 
| 🧠 Defeitos detectados antes da release | 60%         | 95%                 | 
| 🚨 Incidentes em produção        | 10/mês             | 2/mês               | 
| 💸 Retrabalho pós-deploy         | R$ 20.000/mês      | R$ 3.000/mês         | 
| 🔄 Tempo de ciclo (build → deploy) | 3 dias           | 1 dia               | 
