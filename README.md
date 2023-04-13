
# Observatório Social Indaial | SC

O projeto traz a visualização das principais métricas sobre as proposições:

- Total de proposições, proposições aprovadas e a porcentagem de aprovadas de 1996 até o final de 2021

- Contagem do total de proposições agrupadas pela situação

- Visualização gráfica do número de proposições realizadas mês a mês

- Top 3 autores (proposições realizadas) do período selecionado

- Quantidade de proposições por assunto

Este projeto foi desenvolvido pelo [Joviano Silveira](https://www.youtube.com/@JovianoSilveira) nesta [playlist](). O projeto consiste em realizar um **webscrapping** nas proposições publicadas no site da prefeitura de Indaial - Santa Catarina, armazená-las em um **SQL Server** e construir a visualização dos dados com o **Power BI**.

- Proposições: propostas feitas pelos vereadores da cidade de, predominantemente, manutenções na cidade.


## Tech Stack

**ETL:** Python 3.6.6

**Database:** SQL server 19

**Data Viz:** Power BI


## Documentação

### Geral
[Página inicial das proposições](https://www.camaraindaial.sc.gov.br/pg/proposicoes)

[Proposição exemplo](https://www.legislador.com.br//LegisladorWEB.ASP?WCI=ProposicaoTexto&ID=3&TPProposicao=1&nrProposicao=806&aaProposicao=2021)

### Bibliotecas utilizadas

O projeto foi desenvolvido utilizando o **python 3.6.6**

Por questões de boas práticas na máquina local, é interessante utilizar um ambiente virtual para isolamento das bibliotecas

```bash
python -m venv venv

# ativando o ambiente virtual
source ./venv/Scripts/activate 
```

```bash
# gerais
pip install jupyterlab=2.9.9 numpy==1.18.3 pandas==1.1.5 matplotlib==3.3.3 seaborn 0.11.0 openpyxl==3.0.5 xlrd==1.2.0

# webscrapping
pip install beautifulsoup4==4.9.3 html5lib==1.1 requests==2.25.1 lxml==4.6.2
```

### Database
SQL Server table schema

``` sql
    CREATE TABLE Proposicoes (
    DataReuniao DATE,
    DataDeliberacao DATE,
    Situacao VARCHAR(200),
    Assunto VARCHAR(1000),
    Autor VARCHAR(1000),
    Proposicao INT,
    Ano INT,
    Texto VARCHAR(MAX)
);
```

## TO-DO

1. Provavelmente houve uma reestruturação do html das páginas de proposições e o código está considerando a seção de "Aceite de cookies" como texto da proposição. Para finalização do projeto, eu utilizei o backup do banco de dados disponibilizado em "bkp/bkp_dbo/IndaialBackup.bak"

2. Há mais proposições nas páginas do que as mostradas no vídeo. Ex: no ano de 1996, nos vídeos é lido até a proposição 24/1996, mas podemos verificar que existem mais do que 24 proposições neste ano. **Evidência [346/1996](https://www.legislador.com.br//LegisladorWEB.ASP?WCI=ProposicaoTexto&ID=3&TPProposicao=1&nrProposicao=346&aaProposicao=1996)**