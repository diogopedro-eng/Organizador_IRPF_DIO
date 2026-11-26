# Organizador IRPF - DIO

## DESCRIÇÃO
O projeto consiste na criação de uma planilha de controle de dados para facilitar a organização de informações necessárias para a declaração de imposto de renda. A ferramenta será desenvolvida no Excel, utilizando validações de dados, navegação facilitada e funções interativas. Este projeto é ideal para quem busca uma solução prática e profissional para organização de dados fiscais e pode ser um excelente diferencial em seu portfólio.

## Subtitulo
Pasta de trabalho do Excel (`Organizador IRPF - DIO.xlsx`) para **organizar, em um só lugar, as informações necessárias para a declaração do Imposto de Renda Pessoa Física (IRPF)**: dados do titular, rendimentos bancários, entradas/saídas mensais e resumos.

> **Aviso:** este é um organizador pessoal de apoio. Não substitui o programa oficial da Receita Federal nem orientação de um contador.

---

## Estrutura da pasta

A pasta possui **5 planilhas** (4 visíveis e 1 oculta), numeradas na ordem sugerida de preenchimento:

| Ordem | Planilha | Visível | Finalidade |
|:-----:|----------|:-------:|------------|
| 1 | `Titular` | Sim | Dados cadastrais da pessoa física |
| 2 | `Informes` | Sim | Informes de rendimentos bancários (até 3 bancos) e total |
| 3 | `Notas` | Sim | Registro de entradas e saídas (notas bancárias / extrato de holerite) |
| 4 | `Resumos` | Sim | Totais por categoria e gráficos |
| - | `bancos` | Não (oculta) | Base de consulta com instituições financeiras |

---

## Detalhamento por planilha

### 1. `Titular` - Dados do titular
Formulário de preenchimento (coluna D) com os campos:

- Nome, CPF, nascimento e título de eleitor
- Cônjuge
- Endereço: rua, rua abreviada e CEP
- Contatos: telefone, celular e e-mail
- Indicadores (Sim/Não): *houve alterações da entrega anterior*, *dependente cônjuge* e *residente no exterior*

### 2. `Informes` - Informes de rendimentos bancários
Formulário com **três blocos** (1º, 2º e 3º Banco). Cada bloco contém:

| Campo | Descrição |
|-------|-----------|
| `BANCO` | Nome da instituição financeira |
| `VALOR ATUAL` | Saldo/valor informado no informe de rendimentos (R$) |
| `ANEXO` | Nome do arquivo PDF do informe (campo de referência, ex.: `BANCO X.PDF`) |

**Fórmula principal:** o campo **TOTAL** (célula `C6`/`D6`) soma os três valores:

```excel
=SUM(D10,D15,D20)
```

> Se precisar incluir mais bancos, copie um bloco e inclua a nova célula de valor na fórmula do TOTAL.

### 3. `Notas` - Notas bancárias ou extrato de holerite
Contém duas **tabelas do Excel** lado a lado, que crescem automaticamente ao digitar novas linhas:

| Tabela | Intervalo | Colunas |
|--------|-----------|---------|
| `entradas` | `C6:E19` | `DATA`, `CATEGORIA`, `VALOR` |
| `saidas` | `G6:I9` | `DATA`, `CATEGORIA`, `VALOR` |

Categorias usadas atualmente:
- **Entradas:** `HOLERITE`, `CNPJ`, `FREE LANCE`
- **Saídas:** `AGUA`, `ALUGUEL`, `LUZ`

### 4. `Resumos` - Resumos e gráficos
- Duas **Tabelas Dinâmicas** (`Tabela dinâmica3` para entradas e `Tabela dinâmica4` para saídas) que somam `VALOR` por categoria, com filtro por `DATA`.
- Dois **gráficos de colunas agrupadas** (`Chart 12` e `Chart 13`) alimentados por essas tabelas dinâmicas.

Situação atual dos dados de exemplo: **Entradas R$ 1.400,00** | **Saídas R$ 800,00**.

### `bancos` - Base de instituições (oculta)
Lista com ~128 instituições financeiras, com as colunas `ORDEM`, `CNPJ`, `NOME INSTITUIÇÃO`, `CÓDIGO DA INSTITUIÇÃO` e `SEGMENTO` (ex.: Itaú Unibanco, Banco do Brasil, Caixa, Bradesco, Santander, BTG Pactual, Safra). Serve de consulta para padronizar os nomes dos bancos usados em `Informes`.

---

## Como usar

1. Preencha `Titular` com seus dados pessoais.
2. Em `Informes`, informe banco, valor atual e o nome do PDF do informe de rendimentos de cada instituição; confira o TOTAL.
3. Em `Notas`, lance cada entrada e saída (data, categoria e valor) nas tabelas `entradas` e `saidas`.
4. Em `Resumos`, atualize as tabelas dinâmicas: **Dados > Atualizar Tudo** (`Ctrl + Alt + F5`). Os totais e os gráficos são recalculados.

---

