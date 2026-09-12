# 📊 Conciliação — Data Analytics aplicado à Controladoria

## 📌 Sobre o projeto

Este projeto apresenta uma solução de **conciliação e validação de dados desenvolvida em Excel**, com foco na análise de informações provenientes de duas fontes distintas:

* **Base Contábil**
* **Base Operacional**

A solução foi construída para automatizar o cruzamento das informações, identificar divergências e transformar diferenças numéricas em **diagnósticos que direcionam a análise**.

Mais do que uma planilha de conferência, o projeto busca aplicar conceitos de **Data Analytics dentro de um contexto de Controladoria**.

---

## 🎯 Objetivo

O objetivo da solução é responder de forma automatizada:

> **As informações das duas fontes estão conciliadas?**

E, caso exista uma divergência:

> **Onde está essa divergência?**

Para isso, a estrutura realiza o cruzamento das informações e classifica cada registro de acordo com o resultado da validação.

---

## 🔄 Estrutura da solução

O processo pode ser representado da seguinte forma:

```text
        BASE CONTÁBIL
            │
            │
            ├──────────────┐
            │              │
            ▼              ▼
      Tratamento      Tratamento
            │              │
            └──────┬───────┘
                   ▼
             Cruzamento
                   │
                   ▼
             Comparação
                   │
                   ▼
          Regras de negócio
                   │
                   ▼
            ┌─────────────┐
            │   SITUAÇÃO  │
            └─────────────┘
                   │
                   ▼
            ┌─────────────┐
            │ DIAGNÓSTICO │
            └─────────────┘
                   │
                   ▼
          Análise da divergência
```

---

## 🔎 Fontes de dados

### Base Contábil

Fonte utilizada para obtenção das informações contábeis que serão confrontadas na conciliação.

### Base Operacional

Fonte utilizada para comparação das informações relacionadas aos registros analisados.

As duas bases são cruzadas para verificar a consistência das informações e identificar diferenças.

---

## ⚙️ Como funciona a Conciliação

A aba **Conciliação** consolida os registros das duas fontes e realiza diferentes validações.

Entre os elementos analisados estão:

* Venda;
* Custo;
* PIS;
* COFINS;
* ICMS;
* Impostos;
* Devoluções;
* Diferenças entre as fontes.

A partir dessas comparações, a solução determina automaticamente a situação de cada registro.

---

## 🏷️ Identificação de divergências de Centro de Custo

Além da comparação dos valores financeiros, a solução também verifica a **classificação por Centro de Custo**.

Essa validação é importante porque duas fontes podem apresentar o mesmo valor financeiro, mas estar associadas a **Centros de Custo diferentes**.

Nesse cenário, uma conciliação baseada somente no valor poderia indicar que as informações estão corretas, quando existe uma inconsistência na classificação gerencial.

A solução, portanto, amplia a validação:

```text
Valor
  +
Centro de Custo
  +
Existência do registro
  +
Demais campos analisados
        ↓
    Validação
        ↓
    Situação
        ↓
    Diagnóstico
```

Dessa forma, é possível identificar situações em que o valor está presente, mas a **classificação do Centro de Custo diverge entre as fontes**.

Essa abordagem aproxima a conciliação de uma análise de **qualidade e consistência dos dados**, e não apenas de uma conferência matemática.


---

## 🚦 Coluna "Situação"

A coluna **Situação** transforma o resultado das validações em uma classificação objetiva.

Ela permite identificar rapidamente se determinado registro:

* está conciliado;
* possui divergência;
* está presente apenas no Base Contábil;
* está presente apenas na Base Operacional;
* ou se enquadra em outra condição definida pelas regras da solução.

Isso permite passar de uma análise baseada em milhares de números para uma análise baseada em **exceções**.

Em vez de verificar manualmente cada registro, o usuário consegue direcionar sua atenção para aquilo que realmente necessita de investigação.

---

## 🔍 Coluna "Diagnóstico"

A coluna **Diagnóstico** representa uma segunda camada de análise.

Enquanto a coluna **Situação** responde:

> **"Existe uma divergência?"**

A coluna **Diagnóstico** procura responder:

> **"Onde está a divergência?"**

A solução analisa as diferenças encontradas e identifica o ponto que precisa ser investigado.

Dessa forma, a ferramenta não apenas sinaliza uma inconsistência, mas fornece uma indicação para **direcionar a análise**.

### Exemplo conceitual

```text
Situação:
DIVERGENTE

Diagnóstico:
Diferença identificada na Venda
```

Isso reduz o tempo necessário para localizar a origem do problema.

---

## ⚡ Automação das fórmulas

Um dos principais aspectos da construção foi evitar o preenchimento manual das fórmulas para cada registro.

As fórmulas da estrutura de análise são inseridas **apenas na linha 10**.

A partir dessa linha, a utilização de fórmulas dinâmicas permite que a estrutura **se expanda automaticamente para baixo**, acompanhando os registros retornados pela análise.

### Conceito

```text
Linha 10
   │
   ▼
Fórmula principal
   │
   ▼
Expansão automática
   │
   ├── Registro 1
   ├── Registro 2
   ├── Registro 3
   ├── Registro 4
   ├── ...
   └── Registro N
```

Com isso, não é necessário copiar manualmente a fórmula para centenas de linhas.

Essa abordagem contribui para:

* redução de tarefas repetitivas;
* menor risco de erro manual;
* maior escalabilidade;
* facilidade de atualização;
* padronização do processo.

---

## 🧠 Fórmulas e recursos utilizados

A solução utiliza recursos avançados do Excel, incluindo funções de matrizes dinâmicas e funções para tratamento e análise dos dados.

Entre os principais recursos utilizados estão:

```text
LET
FILTER
UNIQUE
VSTACK
SORT
MAP
LAMBDA
COUNTIFS
SUMIFS
```

A utilização dessas funções permite construir uma lógica mais próxima de um **processo de transformação e análise de dados**, em vez de simplesmente realizar cálculos isolados em células.

---

## 📊 Visão analítica

A solução também permite transformar o resultado da conciliação em indicadores gerenciais.

Exemplos:

```text
NFs analisadas
        ↓
NFs conciliadas
        ↓
NFs divergentes
        ↓
Registros presentes somente em uma fonte
        ↓
% de conciliação
```

Essa estrutura permite começar pela visão geral e posteriormente aprofundar a análise até o registro individual.

### Visão macro → exceção → detalhe

```text
Indicadores
     ↓
Identificação das exceções
     ↓
Registro específico
     ↓
Diagnóstico
     ↓
Investigação
```

---

# 📈 Relação com Data Analytics

Embora a solução tenha sido desenvolvida em **Excel**, sua lógica se aproxima de um processo de **Data Analytics**.

O fluxo pode ser resumido em:

```text
Dados
  ↓
Tratamento
  ↓
Integração
  ↓
Cruzamento
  ↓
Validação
  ↓
Regras de negócio
  ↓
Identificação de exceções
  ↓
Diagnóstico
  ↓
Tomada de decisão
```

Esse mesmo raciocínio poderia ser implementado utilizando diferentes tecnologias, como:

* SQL;
* Python;
* Power Query;
* Power BI;
* ferramentas de ETL/ELT.

A ferramenta muda, mas o **raciocínio analítico permanece**.

---

## 💼 Controladoria + Dados

Este projeto representa a aplicação de conceitos de **Data Analytics em um problema real de Controladoria**.

A Controladoria fornece o contexto de negócio e as regras necessárias para interpretar os dados.

A análise de dados fornece as ferramentas e técnicas para:

* integrar informações;
* automatizar validações;
* identificar padrões;
* detectar exceções;
* localizar divergências;
* gerar diagnósticos;
* apoiar decisões.

O resultado é uma solução que busca ir além da simples conferência de números:

> **transformar dados em informação analisável e acionável.**

---

## 🛠️ Tecnologias e ferramentas

**Principal:**

* Microsoft Excel

**Recursos utilizados:**

* Fórmulas avançadas;
* Matrizes dinâmicas;
* Funções de busca e agregação;
* Regras de negócio;
* Validação e conciliação de dados;
* Automação de análises.

**Possíveis evoluções:**

* Power Query;
* SQL;
* Python;
* Power BI.

---

## 🔐 Observação sobre os dados

Para publicação e demonstração pública, será utilizado **dados fictícios ou devidamente anonimizados**.

A estrutura, lógica de tratamento, regras de negócio e metodologia serão demonstradas sem expor informações confidenciais ou dados corporativos.

---

## 🚀 Próximos passos

Uma evolução natural desta solução seria transportar a mesma lógica para uma arquitetura de dados mais robusta:

```text
Excel
  ↓
Power Query
  ↓
SQL / Banco de Dados
  ↓
Python
  ↓
Power BI
```

O objetivo seria transformar a solução em um processo ainda mais automatizado, reutilizável e escalável.

---

## 👩‍💻 Sobre o projeto

Este projeto foi desenvolvido com o objetivo de explorar a interseção entre **Controladoria, Automação e Data Analytics**, utilizando o Excel como ferramenta para construir uma solução de validação e análise de dados.

A principal aprendizagem não está apenas nas fórmulas utilizadas, mas na construção do processo:

> **Como transformar duas fontes de dados em uma análise estruturada, identificar exceções automaticamente e direcionar a investigação para o ponto da divergência.**

---

### 💡 Principais conceitos demonstrados

`Data Analytics` `Controladoria` `Excel Avançado` `Data Validation` `Data Reconciliation` `Business Rules` `Automation` `Financial Data` `Exception Analysis`

