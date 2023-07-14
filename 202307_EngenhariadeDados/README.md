# Desafio ImpulsoGov | Pessoa Engenheira de Dados :hammer:
## Instruções gerais
- Seu desafio idealmente deve ser implementado até 24/07/2023
- Esse desafio não é uma fase eliminatória 
- Envie sua resolução descritos para o e-mail gabrielle@impulsogov.org, bernardo@impulsogov.org e walter@impulsogov.org.

## Enunciado

- **Acelerar a forma que fazemos re/instalações**: No trimestre anterior, no período de 5 semanas tivemos cerca de 15 reuniões para fazer instalação do transmissor em novos municípios parceiros.  Durante esse processo nem sempre conseguimos realizar a instalação em uma única reunião. Esse período alocou grande parte do tempo da equipe em um processo que podemos tornar mais rápido e escalável. Em nossas diretrizes estratégicas temos o objetivo de inserir mais 20 municípios no primeiro trimestre de 2024, se queremos atingir o ritmo de embarcar 20 municípios ou mais a cada trimestre, precisamos um software que garanta essa escala de novos embarques e conforto para entregar novas atualizações.
- **Adequar a forma que processamos os dados no banco**: As transmissões ocorrem de forma simultânea, gerando um pico de trabalho em nosso banco de dados, o que afeta a disponibilidade para a execução de demais rotinas e consultas. O gráfico abaixo demonstra o pico de espera de E/S por volta das 8h, o momento que a maioria dos servidores municipais estão ativos e realizando a primeira tentativa de transmissão do dia. A espera de E/S em um banco de dados se refere ao tempo em que uma transação ou consulta aguarda a conclusão de operações de entrada ou saída relacionadas ao acesso aos dados armazenados no banco de dados.
- **Queremos reduzir e tornar mais eficiente a resolução de falhas nas transmissões**: As falhas nas transmissões ocorrem principalmente devido a três fatores: a) problemas de conectividade na rede do servidor municipal; b) manutenções no servidor municipal que afetam o estado do nosso programa; e c) inatividade da máquina municipal devido a eventos específicos do município, como feriados, ausência de suporte de TI, migração para novos computadores, entre outros. Hoje não temos que nos tornam capazes de depurar o problema da falha de transmissão, mesmo os já conhecidos, sem antes entrar em contato com o município para fazer perguntas e entrar no servidor deles se necessário.


## Entrega
Esperamos um arquivo de formato de sua preferência (texto/video/audio) com suas respostas e seu embasamento para sua proposta. Não esperamos uma resposta muito "bonita" ou "perfeitamente estruturada/completa", o mais importante é você nos mostrar porque escolheria tal opção, seja baseado em pesquisa que realizou ou na sua experiência prévia. Caso deseje mais informações, basta solicitar por email.
