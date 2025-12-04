# BI-Portfolio
Business Intelligence Portfolio (Power BI, SQL, Dashboards, Figma)
```mermaid
flowchart LR
  Client -->|HTTP| API_GW[API Gateway]
  API_GW --> QuoteSvc[Quote-Service]
  QuoteSvc --> CustomerSvc[Customer-Service\n(PostgreSQL)]
  QuoteSvc --> ClaimSvc[Claim-Service\n(PostgreSQL)]
  QuoteSvc --> RiskSvc[Risk-Scoring-Service\n(Elasticsearch)]
  QuoteSvc --> PricingSvc[Pricing-Service\n(REST API)]
  QuoteSvc --> QuoteDB[(PostgreSQL: quotes)]
  QuoteSvc --> ESIndex[(Elasticsearch: quotes_index)]
  PricingSvc -->|calls actuarial models| Actuary[Actuary Engine]
  RiskSvc --> ESCluster[Elasticsearch Cluster]
  subgraph Observability
    QuoteSvc -->|metrics/traces| Prometheus
    QuoteSvc -->|traces| Jaeger
  end
```
