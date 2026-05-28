# Custo Real de Ambiente On-Premises

Este guia ajuda a estimar custo mensal de servidores, clusters e storage on-premises.

O objetivo é comparar capacidade contratada, uso real, desperdício e decisões de expansão ou rightsizing.

## Custos Que Devem Entrar

Considere:

- hardware amortizado;
- suporte ou garantia;
- energia;
- refrigeração;
- licenças;
- backup;
- storage;
- operação;
- espaço físico ou colocation;
- conectividade quando aplicável.

## Fórmula Simples

```text
Custo mensal total = hardware amortizado + suporte + energia + licenças + operação + storage + conectividade
```

Depois distribua o custo:

```text
Custo por vCPU = parcela de CPU / vCPU disponíveis
Custo por GB RAM = parcela de memória / GB RAM disponíveis
Custo por GB storage = custo mensal do storage / GB úteis
```

## Exemplo

Servidor ou cluster:

```text
Custo mensal total: R$ 4.800
Parcela CPU: 40%
Parcela RAM: 40%
Parcela storage/outros: 20%
vCPU disponíveis: 96
RAM disponível: 512 GB
```

CPU:

```text
R$ 4.800 x 40% = R$ 1.920
R$ 1.920 / 96 = R$ 20 por vCPU/mês
```

RAM:

```text
R$ 4.800 x 40% = R$ 1.920
R$ 1.920 / 512 = R$ 3,75 por GB RAM/mês
```

Storage:

```text
Custo mensal storage: R$ 3.000
Capacidade útil: 10.000 GB
R$ 3.000 / 10.000 = R$ 0,30 por GB/mês
```

## Como Usar na Plataforma

Quando disponível no plano, configure os custos unitários on-premises para apoiar:

- estimativa de custo por VM;
- comparação com cloud;
- análise de rightsizing;
- showback interno;
- decisão de expansão;
- relatório executivo.

## Boas Práticas

- Revise premissas com financeiro e infraestrutura.
- Não misture custo de compra com custo mensal sem amortização.
- Documente a origem dos valores.
- Atualize quando contrato, energia, suporte ou hardware mudar.
