# Políticas IAM AWS

Esta pasta contém modelos de policies IAM para conectar contas AWS à Travassyx Platform.

## Arquivos

- `aws-travassyx-policy-basic.json`: inventário e métricas básicas.
- `aws-travassyx-policy-finops-essential.json`: inventário + Cost Explorer e tags.
- `aws-travassyx-policy-smart-optimization.json`: FinOps essencial + Compute Optimizer e Trusted Advisor.
- `aws-travassyx-policy-enterprise-multiconta.json`: nível enterprise com Organizations, Cost Categories, Forecast, Anomaly Detection e CUR detectado.
- `aws-travassyx-remediation-policy.json`: permissões opcionais para remediação assistida.

## Recomendação

Use sempre o menor nível que atende o objetivo do cliente.

Anexe a policy de remediação somente quando a empresa aprovar ações assistidas. Ela possui permissões de escrita controladas, como tags, stop de instância e ajustes específicos.

## Trust Policy

A trust policy depende do Account ID autorizado e do External ID gerado na plataforma. Veja [Onboarding AWS e FinOps](../aws-onboarding.md).
