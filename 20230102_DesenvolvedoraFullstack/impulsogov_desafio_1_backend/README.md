# Desafio 1 - *Backend*

## Contexto

Como organização que trabalha com saúde pública, com frequência desenvolvemos
plataformas que precisam consultar dados básicos da rede de atendimento do
Sistema Único de Saúde brasileiro.

Neste desafio, você deverá implementar um *webservice* semelhante ao que
usuaríamos em uma de nossas plataformas, para **retornar dados dos
estabelecimentos de saúde** vinculados ao SUS, tais como nome e localização.

Para isso, você deve consultar a tabela `estabelecimentos` que se encontra
armazenada no arquivo [`dados.db`](./dados.db). Esse arquivo é um banco de
dados [SQLite](https://www.sqlite.org/index.html). *Se desejar*, você pode
inspecionar o conteúdo da tabela com um programa gratuito como o
[DB Browser for SQLite](https://sqlitebrowser.org/) ou o
[DBeaver Community](https://dbeaver.io/download/).

## Descrição dos dados

A tabela `estabelecimentos` contém as seguintes colunas:

| Coluna | Tipo | Descricao |
| ------ | ---- | --------- |
| `uf_sigla` | char(2) | Sigla da Unidade Federativa onde se localiza o estabelecimento |
| `municipio_id_sus` | char(6) | Código identificador do município onde se localiza o estabelecimento nos sistemas do SUS |
| `id_cnes` | char(7) | Código identificador do estabelecimento no Cadastro Nacional de Estabelecimentos de Saúde |
| `nome` | text | Nome do estabelecimento de saúde |
| `latitude` | float4 | Latitude da posição do estabelecimento de saúde, em graus decimais |
| `longitude` | float4 | Latitude da posição do estabelecimento de saúde, em graus decimais |

## O que você precisa entregar

A partir dos dados fornecidos,
**crie uma API *web* com os seguintes *endpoints***:

- *Endpoint* `listarEstabelecimentosPorMunicipio` (GET): recebe como parâmetro
um valor correspondente à coluna `municipio_id_sus`, e retorna um JSON com
uma lista de objetos, em que cada objeto contém as informações
(*código CNES, nome, localização*) de um estabelecimeto de saúde localizado no
município solicitado.
- *Endpoint* `obterEstabelecimentoPorId` (GET): recebe como parâmetro um valor
correspondente à coluna `id_cnes` e retorna um JSON contendo unicamente um
objeto com as informações (*código CNES, nome, localização*) do estabelecimento
solicitado.

Incentivamos *fortemente* você a tentar construir a sua API usando Python e a
biblioteca [FastAPI](https://fastapi.tiangolo.com/). Porém, se isso for um
problema, **não deixe de entregar o desafio**. Você também pode construir sua
API com outras bibliotecas/frameworks Python ou NodeJS.

A API deve rodar localmente em um ambiente virtual que contenha todas as
dependências utilizadas, conforme listado em um arquivo `requirements.txt`,
`pyproject.toml` ou `package.json` disponível no seu repositório.

## Boas práticas

- Disponibilize um arquivo `README.md` no repositório do seu desafio, contendo
qualquer instrução que considere relevante sobre como instalar e/ou executar
o `webservice`.
- Mantenha seu
[código limpo](https://impulsogov.notion.site/Princ-pios-do-c-digo-limpo-3758686b9bac49e18b0cf95f528e68c5),
atribuindo nomes significativos às funções e variáveis e comentando
pontualmente a lógica do seu programa.
