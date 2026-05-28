# LDAP e Active Directory

Este guia descreve como habilitar login corporativo na Travassyx Platform usando LDAP ou Microsoft Active Directory.

## O Que a Integração Faz

- Mantém login local como contingência administrativa.
- Autentica usuários no LDAP/Active Directory.
- Cria usuários automaticamente no primeiro login quando habilitado.
- Mapeia perfis Admin, Manager e Viewer por grupos.
- Vincula Manager e Viewer ao cliente ou ambiente correto.
- Bloqueia recuperação de senha local para contas LDAP/AD.

## Recomendação no Active Directory

Crie uma conta de serviço somente leitura.

Exemplo de DN:

```text
CN=svc-travassyx,OU=Servicos,DC=empresa,DC=local
```

Permissões mínimas:

- ler usuários;
- ler grupos;
- ler atributos `sAMAccountName`, `userPrincipalName`, `mail`, `displayName` e `memberOf`.

Crie grupos por perfil:

```text
CN=Travassyx Admins,OU=Grupos,DC=empresa,DC=local
CN=Travassyx Managers,OU=Grupos,DC=empresa,DC=local
CN=Travassyx Viewers,OU=Grupos,DC=empresa,DC=local
```

## Configuração na Plataforma

Acesse:

```text
Administração > Configuração > LDAP e Active Directory
```

Campos principais:

- Host LDAP/AD.
- Porta: 389 com STARTTLS ou 636 com LDAPS.
- Segurança: prefira STARTTLS ou LDAPS.
- Bind DN.
- Senha bind.
- Base DN de usuários.
- Filtro de usuário.
- Base DN de grupos.
- Filtro de grupos.
- Grupos Admin, Manager e Viewer.
- Cliente/Ambiente padrão para Manager e Viewer.
- Criar usuário automaticamente.
- Exigir grupo mapeado.

Filtro recomendado para AD:

```text
(|(sAMAccountName={username})(userPrincipalName={username})(mail={username}))
```

## Teste

Use o botão **Testar conexão** no card LDAP/AD.

O teste valida:

- conexão;
- bind;
- busca de usuário;
- grupos encontrados;
- perfil calculado;
- autenticação real quando senha de teste é informada.

## Boas Práticas

- Use LDAPS ou STARTTLS.
- Use conta bind sem privilégio administrativo.
- Mantenha pelo menos um admin local.
- Use grupos separados por perfil.
- Em produção, prefira exigir grupo mapeado.
- Teste com usuário real antes de liberar.
