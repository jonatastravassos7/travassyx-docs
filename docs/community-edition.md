# Travassyx Community Edition

A Community Edition é a edição gratuita da Travassyx Platform para empresas e profissionais que querem testar a plataforma em uma instância própria.

Ela é exclusiva para instalação in-loco e não libera uso SaaS hospedado.

## Limites

- Até 20 recursos monitorados.
- Uma ativação por licença.
- Uso gratuito em instância própria.
- Revalidação obrigatória com o servidor central `https://console.travassyx.com`.
- Não inclui NOC/MSP, multiambiente, AWS/FinOps avançado ou automações pagas.

## Como Obter

1. Acesse o site oficial da Travassyx.
2. Abra a área **Community Edition**.
3. Preencha nome, empresa, e-mail e telefone.
4. Aceite os termos aplicáveis.
5. Aguarde o e-mail com serial e link de download do pacote runtime.

Cada e-mail pode solicitar apenas uma licença Community. Se o mesmo e-mail solicitar novamente, o sistema reutiliza a licença existente e reenvia os dados de ativação.

## Como Instalar

Depois de receber o pacote por e-mail, siga o guia:

- [Instalação da Community Edition](instalacao-community.md)

## O Que Você Deve Ter em Mãos

- Servidor Ubuntu 22.04 LTS ou 24.04 LTS.
- Acesso HTTPS ao Docker Hub.
- Acesso HTTPS ao registry oficial da Travassyx.
- Acesso HTTPS ao servidor central `https://console.travassyx.com`.
- Serial recebido por e-mail.

## Segurança do Pacote

Antes de instalar, valide o checksum:

```bash
sha256sum -c checksums.txt
```

Quando houver assinatura publicada junto do pacote, valide também a assinatura com a chave pública oficial da Travassyx.

## Upgrade

Se a empresa desejar mais recursos, AWS/FinOps avançado, NOC/MSP, multiambiente ou automações, solicite migração para um plano pago. A licença técnica define os módulos habilitados e a franquia de recursos.
