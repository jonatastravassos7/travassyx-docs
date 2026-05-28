# Onboarding AWS e FinOps

Este guia ajuda a conectar contas AWS à Travassyx Platform usando permissões oficiais da AWS.

## Níveis de Funcionamento

| Nível | Objetivo | Policy |
| --- | --- | --- |
| Básico | Inventário AWS, regiões, EC2, EBS, RDS, S3, ELB, VPC e CloudWatch | `aws-policies/aws-travassyx-policy-basic.json` |
| FinOps essencial | Básico + Cost Explorer e tags de alocação de custo | `aws-policies/aws-travassyx-policy-finops-essential.json` |
| Otimização inteligente | FinOps essencial + Compute Optimizer e Trusted Advisor | `aws-policies/aws-travassyx-policy-smart-optimization.json` |
| Enterprise multi-conta | Otimização + Organizations, Cost Categories, CUR, Forecast e Anomaly Detection | `aws-policies/aws-travassyx-policy-enterprise-multiconta.json` |

Existe também uma policy opcional de remediação assistida:

- `aws-policies/aws-travassyx-remediation-policy.json`

Use remediação apenas se a empresa permitir ações controladas como tags, stop de instância ou ajustes assistidos.

## Modelo Recomendado

Use Cross-Account Role com External ID.

Vantagens:

- evita guardar Access Key permanente;
- permite rotação e revogação centralizada;
- reduz risco de credencial exposta;
- facilita multi-conta.

## Trust Policy

No cliente AWS, crie uma role confiando na conta AWS da Travassyx ou na conta informada pela equipe responsável pela implantação.

Modelo:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::<ACCOUNT_ID_TRAVASSYX>:root"
      },
      "Action": "sts:AssumeRole",
      "Condition": {
        "StringEquals": {
          "sts:ExternalId": "<EXTERNAL_ID_GERADO_NO_TRAVASSYX>"
        }
      }
    }
  ]
}
```

Substitua:

- `<ACCOUNT_ID_TRAVASSYX>` pela conta autorizada a assumir a role.
- `<EXTERNAL_ID_GERADO_NO_TRAVASSYX>` pelo External ID exibido no onboarding AWS da plataforma.

## Configuração na Travassyx

Acesse:

```text
Administração > Operação > Contas AWS
```

Informe:

- nome da conta;
- Account ID;
- Role ARN ou Access Key conforme política aprovada;
- External ID;
- regiões;
- nível de funcionamento desejado.

Depois clique em **Testar conexão**.

## Recursos Coletados

Dependendo das permissões, a plataforma pode coletar:

- EC2;
- EBS;
- RDS;
- S3;
- ELB;
- VPC;
- métricas CloudWatch;
- custos por serviço;
- custos por tag;
- custos por região;
- Forecast;
- anomalias financeiras;
- recomendações nativas.

## Tags Recomendadas

Para FinOps, padronize:

- `Environment`
- `Application`
- `Owner`
- `CostCenter`

Ative as tags necessárias como Cost Allocation Tags na AWS para que o Cost Explorer retorne custo por tag.

## Boas Práticas

- Comece pelo menor nível de permissão que atende o objetivo.
- Use Cross-Account Role sempre que possível.
- Não compartilhe Access Key por e-mail.
- Revise permissões antes de habilitar remediação.
- Em conta pagadora, valide acesso a Cost Explorer, Cost Categories, Forecast e CUR.
- Compute Optimizer precisa estar habilitado para retornar recomendações.
