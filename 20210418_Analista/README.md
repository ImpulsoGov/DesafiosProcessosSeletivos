# Processo Seletivo Analista

## Pasta `Registro de Vacinação`
Dados de vacinação agrupados por "estabelecimento_codigo_ibge_municipio", "numero_dose", "paciente_subgrupo", "data_aplicacao" (categorias) somados "paciente_uuid" como quantidade de pacientes que receberam a dose de cada linha de categoria. Filtrados pelo Estado do RS.

- **estabelecimento_codigo_ibge_municipio** <- código do municipio do estabelecimento.
- **city_name** <- nome da municipio do estabelecimento.
- **state_id** <- sigla do estado do estabelecimento.
- **numero_dose** <- categoria da dose (1° ou 2° dose).
- **paciente_subgrupo** <- código do grupo de atendimento dos vacinados.
- **data_aplicacao** <- data de aplicação.
- **paciente_uuid** <- contagem de pacientes que receberam a dose na devida categoria.

Saiba mais [aqui](https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao/resource/ef3bd0b8-b605-474b-9ae5-c97390c197a8).

## Pasta `SIVEP-GRIPE`
Óbitos Banco de Dados de Síndrome Respiratória Aguda Grave, cuja descrição se encontra [aqui](https://opendatasus.saude.gov.br/dataset/bd-srag-2021).

[Dicionário de Dados 2021](https://opendatasus.saude.gov.br/dataset/9f76e80f-a2f1-4662-9e37-71084eae23e3/resource/b3321e55-24e9-49ab-8651-29cf5c8f3179/download/dicionario-de-dados-srag-hospitalizado-27.07.2020-final.pdf)


## Pasta `Registro Civil`
Número de óbitos do Registro Civil, cuja as informações sobre os dados se encontra [aqui](https://transparencia.registrocivil.org.br/especial-covid).
