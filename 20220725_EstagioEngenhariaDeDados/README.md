# Desafio ImpulsoGov | Estágio em Engenharia de Dados :wrench:
## Instruções gerais

## Desafio 1 :  SQL | Consultando tabelas

### Contexto

Na Impulso você trabalhará com os dados do SUS, frequentemente relacionado à Atenção Primária de Saúde. Os dados abertos do [Sisab](https://sisab.saude.gov.br/) é uma das nossas principais fontes. Entre eles, o [Relatório de Cadastros Vinculados](https://sisab.saude.gov.br/paginas/acessoRestrito/relatorio/federal/indicadores/indicadorCadastro.xhtml) traz um levantamento mensal dos cadastros de pessoas vinculado às unidades de saúde. Esse cadastro é realizada pelos profissionais de saúde de cada unidade que se organizam em equipes. Você carregou esse relatório em nossa banco em uma tabela chamada `municipios_sisab_cadastros` com os seguintes campos:

Um outra tabela chamada `municipios` resume o total de habitantes de cada município. As duas tabelas se relacionam em uma relação do tipo *1:N* (*um para muitos*), como pode ser visto na figura abaixo:

<img src="/imagens/1_N.png" alt="Modelo Entidade-Relação"/>

### Questão A [código]

A partir das duas tabelas você irá estruturar uma consulta que será utilizada por uma de nossas aplicações e deverá retornar a quantidade de estabelecimentos de saúde, a quantidade de equipes e o porte populacional por município, conforme o modelo abaixo:

| municipio_nome | estabelcimento_quantidade  | equipe_quantidade | porte_populacional | 
| ------------------- | ------------------- | ------------------- | ------------------- |
|  Alto Parnaíba |  4 |  4 |  Pequeno |
|  Alto Piquiri |  5 |  5 |  Micro |
|  ... |  ... |  ... |  ... |

#### Considerações

  1.  Considere apenas o mês de maio (05/2022) e cadastros sem critério de pontuação (false)
  2. O porte populacional deverá seguir a seguinte regra:
  
      Micro : Menor que 10.000 habitantes
      
      Pequeno : Entre 10.000 e 100.000 habitantes
      
      Médio : Entre 100.00 habitantes e 500.000 habitantes
      
      Grande : Maior de 500.000 habitantes
    

### Questão B [descritiva]

Como você validaria os dados da sua consulta?

### Entrega

Para resolver a questão A você poderá carregar os arquivos em seu banco para testar sua query, mas exigiremos que apresente apenas o código SQL que você usou para fazer a query.

---

## Desafio 2 : Python | Modelando e armazenando dados

### Contexto

Como estagiária em engenharia de dados uma das suas principais atribuições será apoiar na construção de scripts de extração, tratamento e carregamento dos dados (ETL). Em uma situação hipotética, há um script de extração de dados já pronto para o [relatório de indicadores do Sisab](https://sisab.saude.gov.br/paginas/acessoRestrito/relatorio/federal/indicadores/indicadorPainel.xhtml). A cada quadrimestre o script raspa os dados do relatório gerando um arquivo de formato CSV para cada indicador como os arquivos que estão nesta [pasta](https://drive.google.com/drive/folders/1kmAiWfDfih5LaZljEu7orlK7W_jAHMRg?usp=sharing).

### Questão

A partir dos arquivos recebidos, você deverá modelar os dados para que sejam carregados em uma única tabela cuja granularidade deverá estar resumida por município e nome do indicador. Realize transformações que julgar necessário e carregue os dados no seu banco local para uma tabela com a seguinte estrutura :

### Considerações

  1. O tipo de indicador está indicado no cabeçalho de cada arquivo
  2. A data periodo desse relatório corresponde apenas o 1º quadrimestre de 2022 (início em 2022-01-01)

### Entrega

Esperamos um código em python, de preferência no Google Colab que possamos testar rapidamente (mesmo que a função de inserção no banco não venha a funcionar).
