# Dependências Open-Source

A Travassyx Platform usa tecnologias amplamente adotadas no ecossistema open-source.

Este documento é informativo e não substitui uma análise jurídica formal de licenças.

## Base Técnica

| Componente | Uso |
| --- | --- |
| Python | API e worker |
| FastAPI | API HTTP |
| Uvicorn | Servidor ASGI |
| PostgreSQL | Banco de dados |
| Nginx | Frontend estático e proxy |
| Node.js | Build do frontend |
| React | Interface web |
| Vite | Build frontend |
| Docker Engine | Execução em containers |
| Docker Compose | Orquestração local |

## Bibliotecas de Integração

| Componente | Uso |
| --- | --- |
| boto3 / botocore | APIs AWS |
| pyVmomi | APIs VMware vSphere |
| pypsrp | WinRM/PowerShell Remoting |
| paramiko | SFTP/SSH |
| cryptography | Criptografia e certificados |
| python-jose | JWT |
| passlib / bcrypt | Hash de senha |
| psycopg2-binary | Conexão PostgreSQL |

## Observações

- Docker Desktop não é empacotado pela Travassyx.
- Para Ubuntu, a recomendação é Docker Engine oficial.
- Imagens base e bibliotecas podem mudar por versão.
- Para auditoria formal, gere SBOM da versão entregue e valide licenças conforme política interna do cliente.
