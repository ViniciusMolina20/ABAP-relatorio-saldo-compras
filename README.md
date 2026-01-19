
# Relatório SAP ABAP – Saldo de Compras (Procure to Pay)

## 📌 Visão Geral

Este projeto consiste em um **relatório ABAP completo para acompanhamento do ciclo de compras**, cobrindo todas as etapas do processo **Procure to Pay (P2P)**:

- Requisição de Compra
- Pedido de Compra
- Nota Fiscal
- Pagamento Financeiro

O objetivo principal é oferecer **visão gerencial e operacional** sobre valores pendentes, realizados e pagos, permitindo maior controle financeiro e apoio à tomada de decisão.

---

## 🧠 Conceito de Negócio

Nas empresas, é comum existir dificuldade para responder perguntas como:

- Quanto tenho em requisições ainda não convertidas em pedido?
- Quais pedidos foram criados mas ainda não possuem nota fiscal?
- Quais notas já foram lançadas, mas ainda não foram pagas?
- Qual o valor financeiro real comprometido no processo de compras?
- Onde existem gargalos com fornecedores?

Este relatório resolve exatamente esse problema.

Ele entrega **visão consolidada e confiável do fluxo financeiro de compras**.

---

## 🔁 Fluxo do Processo (Procure to Pay)

```
Requisição (EBAN)
        ↓
Pedido de Compra (EKKO / EKPO)
        ↓
Histórico do Pedido (EKBE)
        ↓
Financeiro / Pagamento (BSEG)
```

---

## 📊 Tipos de Relatórios Disponíveis

O programa permite selecionar quatro visões:

### 1️⃣ Saldo de Requisição
Exibe requisições que:

- Não possuem pedido de compra
- Não estão canceladas
- Não estão concluídas

Tabela principal:
- **EBAN**

---

### 2️⃣ Saldo de Pedido
Exibe pedidos que:

- Foram criados
- Não possuem nota fiscal lançada

Tabelas envolvidas:
- **EKKO**
- **EKPO**
- **EKBE (LEFT JOIN)**

---

### 3️⃣ Saldo de Nota Fiscal
Exibe notas fiscais já lançadas no sistema.

Inclui:
- Débito e crédito tratados corretamente
- Quantidade e valor por item

Tabelas envolvidas:
- **EKBE**
- **EKKO**
- **EKPO**

---

### 4️⃣ Saldo Final Consolidado
Relatório completo que consolida:

- Valor do pedido
- Valor faturado (NF)
- Valor pago no financeiro
- Diferença financeira (saldo)

Tabelas envolvidas:
- **EKKO**
- **EKPO**
- **EKBE**
- **BSEG**

---

## 🔍 Filtros Disponíveis

O relatório possui filtros de negócio completos:

- Data do pedido
- Fornecedor
- Número do pedido
- Material
- Centro
- Grupo de compras
- Organização de compras
- Tipo de documento
- Grupo de mercadorias

Esses filtros permitem análises operacionais, financeiras e gerenciais.

---

## ⚙️ Recursos Técnicos Utilizados

- ABAP Open SQL
- JOIN e LEFT JOIN
- CASE WHEN para cálculos financeiros
- SELECT-OPTIONS dinâmicos
- CL_SALV_TABLE (ALV)
- Consolidação financeira no banco de dados
- Separação do código em INCLUDEs
- Compatível com ECC e S/4HANA

---

## 🧩 Estrutura do Programa

```
ZMM_REL_SALDO_COMPRAS
│
├── ZMM_REL_SALDO_COMPRAS_TOP   (Types e Dados Globais)
├── ZMM_REL_SALDO_COMPRAS_SEL   (Tela de Seleção)
├── ZMM_REL_SALDO_COMPRAS_EVT   (Eventos)
├── ZMM_REL_SALDO_COMPRAS_F01   (Regras de Negócio)
└── ZMM_REL_SALDO_COMPRAS_ALV   (Exibição ALV)
```

---

## 🧠 Boas Práticas Aplicadas

- Fornecedor sempre obtido via **EKKO**
- Uso correto de LEFT JOIN para identificar ausência de dados
- Evita duplicidade de valores financeiros
- Tratamento adequado de campos CHAR em Open SQL
- Código preparado para grandes volumes de dados
- Separação clara entre regra de negócio e exibição

---

## ⚠️ Observações Técnicas

- A tabela **BSEG** possui grande volume de dados.
- Em ambientes S/4HANA, recomenda-se uso da **ACDOCA**.
- Para fins didáticos e conceituais, o uso de BSEG é totalmente válido.

---

## 🎯 Benefícios para o Negócio

- Controle do fluxo de caixa
- Redução de backlog de compras
- Visão clara de pendências com fornecedores
- Apoio à controladoria
- Aumento da transparência financeira
- Melhor tomada de decisão

---

## 🚀 Conclusão

Este relatório demonstra:

- Forte entendimento do processo de compras SAP
- Integração entre negócio, financeiro e tecnologia
- Conhecimento funcional de MM
- Domínio técnico de ABAP Open SQL
- Capacidade de modelar soluções reais de mercado

---

## 🏷️ Tecnologias

- SAP ECC / S/4HANA
- ABAP
- SAP MM
- Open SQL
- ALV

---

**Autor:** Vinicius Molina  
**Área:** SAP ABAP / MM  
**Projeto:** Relatório Gerencial de Compras – Procure to Pay

