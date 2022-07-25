# Desafio ImpulsoGov | Estágio em Engenharia de Dados :hammer:
## Instruções gerais
- Seu desafio idealmente deve ser implementado até 31/07/2022
- Esse desafio não é uma fase eliminatória
- Envie sua resolução para gabrielle@impulsogov.org

## O que avaliaremos
- Sua capacidade analítica e criativade para resolver problemas de forma lógica
- Seus conhecimentos com banco de dados em SQL e Python
- A qualidade do seu código em relação a clareza e funcionalidade

*Dica: Resolva o máximo que você puder, evite enviar questão em branco.*

## Desafio 1 :  SQL | Consultando tabelas

### Contexto

Na Impulso você trabalhará com os dados do SUS, frequentemente relacionado à Atenção Primária de Saúde. Os dados abertos do [Sisab](https://sisab.saude.gov.br/) é uma das nossas principais fontes. Entre eles, o [Relatório de Cadastros Vinculados](https://sisab.saude.gov.br/paginas/acessoRestrito/relatorio/federal/indicadores/indicadorCadastro.xhtml) traz um levantamento mensal dos cadastros de pessoas vinculado às unidades de saúde. Esse cadastro é realizada pelos profissionais de saúde de cada unidade que se organizam em equipes. Você carregou esse relatório em nossa banco em uma tabela chamada `municipios_sisab_cadastros` com os seguintes campos:

```
CREATE TABLE municipios_sisab_cadastros (
            id uiid NOT NULL,
            municipio_id_sus varchar(8) NOT NULL,
            periodo_data date NOT NULL,
            estabelecimento_nome varchar(60) NOT NULL,
            equipe_nome  varchar(100) NOT NULL,
            cadastro_quantidade  int4 NOT NULL,
            cadastro_criterio_pontuacao  bool NOT NULL,
CONSTRAINT municipios_sisab_cadastros_pk PRIMARY KEY (municipio_id_sus, periodo_data, estabelecimento_nome,equipe_nome,cadastro_criterio_pontuacao))
```

Um outra tabela chamada `municipios` resume o total de habitantes de cada município. As duas tabelas se relacionam em uma relação do tipo *1:N* (*um para muitos*), como pode ser visto na figura abaixo:

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/20220725_EstagioEngenhariaDeDados/imagens/1_N.png">
  <source media="(prefers-color-scheme: light)" srcset="/20220725_EstagioEngenhariaDeDados/imagens/1_N.png">
  <img alt="Shows an illustrated sun in light color mode and a moon with stars in dark color mode." src="/20220725_EstagioEngenhariaDeDados/imagens/1_N.png">
</picture>

### Questões
1. A partir das duas tabelas você irá estruturar uma consulta que será utilizada por uma de nossas aplicações e deverá retornar a quantidade de estabelecimentos de saúde, a quantidade de equipes e o porte populacional por município, conforme o modelo abaixo:

  | municipio_nome | estabelcimento_quantidade  | equipe_quantidade | porte_populacional | 
  | ------------------- | ------------------- | ------------------- | ------------------- |
  |  Alto Parnaíba |  4 |  4 |  Pequeno |
  |  Alto Piquiri |  5 |  5 |  Micro |
  |  ... |  ... |  ... |  ... |

2. Como você validaria os dados da sua consulta? [_descritiva_]

### Considerações

  - Considere apenas o mês de maio (05/2022) e cadastros sem critério de pontuação (false)
  - O porte populacional deverá seguir a seguinte regra:
      ```
      Micro : Menor que 10.000 habitantes
      
      Pequeno : Entre 10.000 e 100.000 habitantes
      
      Médio : Entre 100.00 habitantes e 500.000 habitantes
      
      Grande : Maior de 500.000 habitantes
      ```
    
   - Os dados de cada tabela estão nos arquivos CSV desta pasta : [dados_desafio_01](https://github.com/ImpulsoGov/desafios-processos-seletivos/tree/main/20220725_EstagioEngenhariaDeDados/dados_desafio_01)
   - Não é necessário validar os dados, apenas descreva como você o faria.
    

### Entrega

Para resolver o desafio você poderá carregar os arquivos em seu banco para testar sua query, mas exigiremos que apresente apenas o código SQL que você usou para fazer a query.

---

## Desafio 2 : Python | Modelando e armazenando dados

### Contexto

Como estagiária em engenharia de dados uma das suas principais atribuições será apoiar na construção de scripts de extração, tratamento e carregamento dos dados (ETL). Em uma situação hipotética, há um script de extração de dados já pronto para o [relatório de indicadores do Sisab](https://sisab.saude.gov.br/paginas/acessoRestrito/relatorio/federal/indicadores/indicadorPainel.xhtml). A cada quadrimestre o script raspa os dados do relatório gerando um arquivo de formato CSV para cada indicador como os arquivos que estão na pasta [dados_desafio_02](https://github.com/ImpulsoGov/desafios-processos-seletivos/tree/main/20220725_EstagioEngenhariaDeDados/dados_desafio_02).

### Questão

- A partir dos arquivos recebidos, você deverá modelar os dados para que sejam carregados em uma única tabela cuja granularidade deverá estar resumida por município e nome do indicador. Realize transformações que julgar necessário e carregue os dados no seu banco local para uma tabela com a seguinte estrutura :

  ```
  CREATE TABLE sisab_indicadores_municipios (
              municipio_id_sus varchar(8) NOT NULL,
              periodo_data date NOT NULL,
              indicadores_nome varchar(200) NOT NULL,
              numerador int4 NOT NULL,
              denominador_utilizado int4 NOT NULL,
              denominador_identificado int4 NOT NULL,
              denominador_estimado int4 NOT NULL,
              nota_porcentagem int4 NOT NULL,
  CONSTRAINT sisab_indicadores_municipios_pk PRIMARY KEY (municipio_id_sus, indicadores_nome))
  ```

### Considerações

  - O nome de cada indicador está indicado no cabeçalho de cada arquivo
  - O `periodo_data` desse relatório corresponde apenas o 1º quadrimestre de 2022 (início em 2022-01-01)
  - O campo `nota_porcentagem` é o resultado do indicador no mês de referência
  - Crie um módulo para o tratamento dos dados e outro para fazer a inserção no banco
  - Você deverá carregar os dados no seu banco local. Queremos avaliar como você faria essa inserção genericamente.

### Entrega

Esperamos um código em python, de preferência no Google Colab que possamos testar rapidamente _(mesmo que a função de inserção no banco não venha a funcionar)_.
