# Instalação em Modo Instância

Use o modo instância quando a Travassyx Platform precisar rodar dentro do ambiente do cliente, em servidor próprio ou dedicado.

## Requisitos

- Ubuntu 22.04 LTS ou 24.04 LTS.
- Docker Engine e Docker Compose.
- Acesso HTTPS ao servidor central de licenças `https://console.travassyx.com`.
- Serial válido para instância.
- Acesso de rede aos provedores que serão monitorados, como vCenter, Hyper-V, Proxmox, AWS, Azure, Google Cloud ou Kubernetes.

## Instalação

Na pasta entregue para a instalação:

```bash
cd /opt/travassyx/versao-instancia
sudo ./install.sh
```

O instalador pergunta dados básicos do ambiente, cria configuração local, sobe os containers e orienta o primeiro acesso.

## Ativação da Licença

Depois do primeiro acesso:

```text
Administração > Configuração > Licenciamento
```

Informe o serial recebido e valide com o servidor central.

Na instância, o aceite de documentos obrigatórios acontece depois da ativação da licença. Isso evita bloquear a instalação antes de o cliente conseguir informar o serial.

## Configuração Inicial Recomendada

1. Ativar licença.
2. Preencher cadastro do ambiente.
3. Configurar SMTP, se for usar alertas, relatórios ou recuperação de senha.
4. Cadastrar o provider principal.
5. Rodar teste de conexão.
6. Aguardar primeira coleta.
7. Conferir Dashboard, Inventário e Histórico & Logs.
8. Revisar alertas, backup e usuários.

## Atualizações

A versão instância possui atualização assistida no painel:

```text
Administração > Configuração > Atualizações da Plataforma
```

Fluxo recomendado:

1. Gerar ou confirmar backup recente.
2. Rodar preflight.
3. Ler changelog.
4. Baixar e atualizar pela opção oficial ou enviar ZIP manual quando permitido.
5. Aguardar pós-check.
6. Confirmar que a página recarregou e a versão instalada mudou.

## Backup

Configure backup local e, quando possível, destino externo como NFS ou SFTP. Antes de atualização ou mudança crítica, confirme que existe backup recente e restaurável.

## Observações de Segurança

- Guarde senhas e chaves locais com segurança.
- Use HTTPS sempre que possível.
- Restrinja acesso administrativo.
- Mantenha pelo menos um admin local de contingência.
- Não compartilhe serial em canais públicos.
