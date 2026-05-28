# Instalação da Travassyx Community Edition

Este guia instala a Travassyx Community Edition em uma instância in-loco.

## Requisitos

- Ubuntu 22.04 LTS ou 24.04 LTS.
- Acesso HTTPS ao Docker Hub.
- Acesso HTTPS ao registry oficial da Travassyx.
- Acesso HTTPS ao servidor central de licenças `https://console.travassyx.com`.
- Serial Community recebido por e-mail.

## Instalação

No servidor Ubuntu, envie o arquivo ZIP recebido por e-mail e execute:

```bash
unzip travassyx-instance-community-1.0.0-test.zip
cd travassyx-instance-community-1.0.0-test
sudo ./install.sh
```

O nome do ZIP pode mudar conforme a versão publicada. Use o nome exato do arquivo recebido.

## O Que o Instalador Faz

1. Valida se o Ubuntu é suportado.
2. Instala Docker oficial quando necessário.
3. Cria `/opt/travassyx/runtime-community`.
4. Gera segredos locais fortes.
5. Solicita ou grava o serial Community recebido por e-mail.
6. Baixa imagens oficiais da Travassyx.
7. Inicia API, worker, frontend e Postgres.

## Primeiro Acesso

Ao final, o instalador mostra a URL de acesso. Entre com o usuário administrador criado durante a instalação e conclua a ativação quando solicitado.

Depois da ativação, a plataforma pode solicitar aceite dos documentos obrigatórios aplicáveis.

## Limites da Community

- Uso gratuito apenas em instância in-loco.
- Limite fixo de 20 recursos monitorados.
- Uma ativação.
- Revalidação obrigatória com o SaaS central.
- Não inclui SaaS hospedado, NOC/MSP, multiambiente, AWS/FinOps avançado ou automações pagas.

## Validação

Depois de instalar, confira:

- a tela abre no navegador;
- a licença está ativa;
- o worker está rodando;
- o Dashboard abre sem erro;
- o ambiente monitorado foi cadastrado corretamente;
- a primeira coleta foi concluída.

## Integridade do Pacote

Valide o checksum antes da instalação:

```bash
sha256sum -c checksums.txt
```

Se `signature.sig` estiver presente, valide também a assinatura com a chave pública oficial da Travassyx.
