# Matriz de Compatibilidade

Esta matriz resume versões e cenários suportados pela Travassyx Platform para coleta operacional, inventário, alertas e FinOps.

## Status

- **Homologado**: alvo principal para produção.
- **Compatível com validação**: deve passar por teste de coleta antes de produção.
- **Legado / best effort**: pode funcionar com limitações, não recomendado para novos projetos.
- **Não suportado**: fora do escopo atual.

## VMware vCenter

Método: API vSphere via pyVmomi, sem agente nas VMs.

| Produto | Versão | Status |
| --- | --- | --- |
| VMware vCenter Server | 8.0.x | Homologado |
| VMware vCenter Server | 7.0 U3+ | Homologado |
| VMware vCenter Server | 7.0 antes de U3 | Compatível com validação |
| VMware vCenter Server | 6.7 U3 | Legado / best effort |
| VMware vCenter Server | 6.5 ou anterior | Não suportado |
| ESXi standalone sem vCenter | Compatível com validação |

Requisitos mínimos:

- HTTPS ao vCenter na porta 443.
- Usuário de leitura com acesso a datacenter, cluster, hosts, VMs, datastores, eventos e performance.
- Performance counters habilitados.

## Microsoft Hyper-V

Método: WinRM/PowerShell Remoting.

| Produto | Versão | Status |
| --- | --- | --- |
| Windows Server com Hyper-V | 2022 | Homologado |
| Windows Server com Hyper-V | 2019 | Homologado |
| Windows Server com Hyper-V | 2025 | Compatível com validação |
| Windows Server com Hyper-V | 2016 | Legado / best effort |
| Hyper-V em Windows desktop | Não suportado |
| SCVMM como fonte primária | Não suportado nesta fase |

Requisitos mínimos:

- WinRM habilitado.
- Porta 5985 ou 5986.
- Usuário com permissão de consulta em Hyper-V, volumes, eventos e métricas.

## Proxmox VE

Método: API REST na porta 8006.

| Produto | Versão | Status |
| --- | --- | --- |
| Proxmox VE | 8.x | Homologado |
| Proxmox VE | 7.4 | Homologado |
| Proxmox VE | 7.0 a 7.3 | Compatível com validação |
| Proxmox VE | 6.x | Legado / best effort |
| Proxmox VE | 9.x ou superior | Compatível com validação |

Requisitos mínimos:

- HTTPS ao Proxmox na porta 8006.
- Usuário ou API Token com permissão de leitura.
- Papel recomendado: PVEAuditor ou equivalente.

## AWS

Método: APIs oficiais AWS.

| Fonte | Status |
| --- | --- |
| Conta AWS individual | Homologado |
| Múltiplas contas por cliente | Homologado |
| AWS Organizations / conta pagadora | Compatível com validação |
| GovCloud, China ou partições especiais | Não suportado nesta versão |

Serviços previstos:

- EC2, EBS, RDS, S3, ELB, VPC;
- CloudWatch;
- Cost Explorer;
- Trusted Advisor;
- Compute Optimizer;
- Savings Plans e Reserved Instances;
- CUR quando configurado.

## Azure, Google Cloud e Kubernetes

Esses providers possuem coleta read-only inicial ou assistida conforme contrato e permissões.

| Provider | Status |
| --- | --- |
| Microsoft Azure | Compatível com validação |
| Google Cloud | Compatível com validação |
| Kubernetes 1.24+ | Compatível com validação |
| EKS, AKS e GKE | Compatível com validação |

Para Kubernetes, a API server precisa estar acessível e o token/kubeconfig deve permitir leitura de nodes, namespaces, pods, deployments, services, volumes e ingress. Metrics API é recomendada para métricas operacionais.

## Validação Antes de Produção

Confirme:

- teste de conexão bem-sucedido;
- primeira coleta sem erro;
- Dashboard com dados reais;
- Inventário coerente com a origem;
- Histórico & Logs recebendo eventos;
- alertas sem falso positivo crítico;
- relatório executivo com dados do cliente.
