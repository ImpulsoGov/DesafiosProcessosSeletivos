# Desafio ImpulsoGov | Pessoa Engenheira de Dados :hammer:
## Instruções gerais
- Seu desafio idealmente deve ser implementado até 24/07/2023
- Esse desafio não é uma fase eliminatória 
- Envie sua resolução descritos para o e-mail gabrielle@impulsogov.org, bernardo@impulsogov.org e walter@impulsogov.org.

## Enunciado
Hoje em um dos nossos principais produtos o Impulso Previne entregamos listas nominais de publicos prioritários em uma interface intuitiva. Para isso puxamos dados do banco de dados do municipio (que é um PostgreSQL) e enviamos para o nosso banco. Fazemos isso utilizando a extensão do *postgres_fdw*, e chamamos esse processo de transmissor. O transmissor em produção é um script SQL responsável por conectar e integrar bancos de dados, permitindo operações de leitura e escrita. Ele é executado no banco ESUS do município e segue o seguinte fluxo:

![image](https://github.com/ImpulsoGov/desafios-processos-seletivos/blob/main/202307_EngenhariadeDados/Captura%20de%20tela%20de%202023-06-26%2014-32-34.png?raw=true)

1️⃣ Agendador de tarefas aciona o script

2️⃣ Estabelece conexão com o banco de dados da Impulso, importa tabelas onde serão armazenados os dados das listas nominais e consulta o código fonte para a geração de relatórios.

3️⃣ Cria views materializadas das listas nominais com base no código fonte consultado.

4️⃣ Consulta os dados provenientes das views materializadas e insere nas tabelas importadas.

5️⃣ Registra um log da execução da tarefa.


Você pode ver mais sobre o transmissor [aqui](https://www.canva.com/design/DAFoc8VtzV0/8n38KGe3KGHP7G4V0AzSlA/view?utm_content=DAFoc8VtzV0&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink). Recentemente estamos querendo atualizar nosso transmissor, e queremos sua ajuda! Alguns motivos para queremos mudar o nosso modelo de transmissão incluem:
- **Acelerar a forma que fazemos re/instalações**: No trimestre anterior, no período de 5 semanas tivemos cerca de 15 reuniões para fazer instalação do transmissor em novos municípios parceiros.  Durante esse processo nem sempre conseguimos realizar a instalação em uma única reunião. Esse período alocou grande parte do tempo da equipe em um processo que podemos tornar mais rápido e escalável. Em nossas diretrizes estratégicas temos o objetivo de inserir mais 20 municípios no primeiro trimestre de 2024, se queremos atingir o ritmo de embarcar 20 municípios ou mais a cada trimestre, precisamos um software que garanta essa escala de novos embarques e conforto para entregar novas atualizações.
- **Adequar a forma que processamos os dados no banco**: As transmissões ocorrem de forma simultânea, gerando um pico de trabalho em nosso banco de dados, o que afeta a disponibilidade para a execução de demais rotinas e consultas. O gráfico abaixo demonstra o pico de espera de E/S por volta das 8h, o momento que a maioria dos servidores municipais estão ativos e realizando a primeira tentativa de transmissão do dia. A espera de E/S em um banco de dados se refere ao tempo em que uma transação ou consulta aguarda a conclusão de operações de entrada ou saída relacionadas ao acesso aos dados armazenados no banco de dados.
![image](https://github.com/ImpulsoGov/desafios-processos-seletivos/blob/main/202307_EngenhariadeDados/Untitled.png?raw=true)
- **Queremos reduzir e tornar mais eficiente a resolução de falhas nas transmissões**: As falhas nas transmissões ocorrem principalmente devido a três fatores: a) problemas de conectividade na rede do servidor municipal; b) manutenções no servidor municipal que afetam o estado do nosso programa; e c) inatividade da máquina municipal devido a eventos específicos do município, como feriados, ausência de suporte de TI, migração para novos computadores, entre outros. Hoje não temos que nos tornam capazes de depurar o problema da falha de transmissão, mesmo os já conhecidos, sem antes entrar em contato com o município para fazer perguntas e entrar no servidor deles se necessário.

Pensando nisso, como você modificaria esse modelo?

## Entrega
Esperamos um arquivo de formato de sua preferência (texto/video/audio) com suas respostas e seu embasamento para sua proposta. Não esperamos uma resposta muito "bonita" ou "perfeitamente estruturada/completa", o mais importante é você nos mostrar porque escolheria tal opção, seja baseado em pesquisa que realizou ou na sua experiência prévia. Caso deseje mais informações, basta solicitar por email.

**Para ir além:** Como repensaria esse sistema pensando em extrair, processar e armazenar um volume maior de dados.
