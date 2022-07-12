# Desafio para Engenheiro(a) de Dados 

- Seu desafio idealmente deve ser implementado até 06/02/2022 às 12:59.


## Desafio 1: Arquitetura de Datalake
Na Impulso recentemente começamos a criar um datalake. Nossos dados advém em sua grande maioria de requisições feitas no [site do SISAB](https://sisab.saude.gov.br/) e do [ftp do CNES - Cadastro Nacional de Estabelecimentos de Saúde](ftp.datasus.gov.br/dissemin/publicos/CNES/200508_/Dados). Os dados tem um volume grande, porém a frequência de atualização é baixa (em sua grande maioria mensal). Os dados no banco servem tanto para nosso time de analistas quanto para nossas aplicações web. Em grande maioria as informações são consumidas no Google Datastudio. Nossa equipe de tecnologia é formada de 5 profissionais: 2 cientistas de dados, 2 desenvolvedores e 1 engenheiro de dados (você!), que atendem tanto demandas estruturais (como manutenção do banco de dados) quanto demandas de projeto (análises e construção de dashboards). Não temos limitação financeira para as ferramentas a serem usadas no nosso projeto, porém temos a necessidade da solução atender de forma a não necessitar de muita manutenção e que seja simples para que diversos membros possam o modificar.


Com essas informações em mente, responda as questões abaixo:
- Suponha que você tivesse recebido a missão de montar a arquitetura deste DataLake, como o teria feito?
- Quais são os esquemas de fluxo de dados e ferramentas que teria usado? Por que?


**Entrega**
<br>
Esperamos um arquivo de formato de sua preferência (texto/video/audio) com suas respostas e seu embasamento para sua proposta. Não esperamos uma resposta muito "bonita" ou "perfeitamente estruturada/completa", o mais importante é você nos mostrar porque escolheria tal opção, seja baseado em pesquisa que realizou ou na sua experiência prévia. Caso deseje mais informações, basta solicitar por email.
<br>
Exemplos de Respostas:
[Exemplo 1](https://i0.wp.com/www.cienciaedados.com/wp-content/uploads/2018/06/data-lake-blog.png?resize=640%2C244&ssl=1)
[Exemplo 2](https://raw.githubusercontent.com/VAGAScom/desafio-eng-de-dados/master/exemplo_resposta.png)
[Exemplo 3](https://miro.medium.com/max/1400/0*5GlcsYaSdOyZrtFd)



<hr>



## Desafio 2: Python: Estruturando Tabelas
Uma das atividades mais comuns na impulso em engenharia de dados será a extração, transformação e carregamento de dados. Por isso, para esse desafio queremos que você desenvolva um código que 1) extraia os dados de Equipes do CNES - você pode usar a [biblioteca do pysus](https://github.com/AlertaDengue/PySUS/blob/master/pysus/online_data/CNES.py) / [teste](https://github.com/AlertaDengue/PySUS/blob/master/pysus/tests/test_cnes.py) -, podendo extrair somente algumas colunas e puxar os dados de apenas um mês e estado (queremos saber se consegue realizar a extração não que tenha que manipular grandes volumes de dados nesse desafio). 2) Realize as tranformações que achar necessárias e 3) insira os dados no seu banco de dados (use um banco local).

Atualização 31/01/2021: Os códigos não precisam realmente funcionar para inserir os dados no banco, só precisamos da função de como você o faria.


**Entrega**
<br>
Esperamos um código em python, de preferência no Google Colab que possamos testar rapidamente (mesmo que a função de inserção no banco não venha a funcionar).
