# Desafio Técnico ImpulsoGov

Olá, bem-vindo! 🖖

Seja bem-vindo ao desafio técnico da vaga para de Consultor(a) de Suporte em TI da Impulso Gov (Abr./2024)!

## Enunciado

Hoje em um dos nossos principais produtos o Impulso Previne entregamos listas nominais de públicos prioritários em uma interface intuitiva. Para isso, puxamos dados do banco de dados do município (que é um PostgreSQL, versão 9.6) e enviamos para o nosso banco. Fazemos isso utilizando a extensão do *postgres_fdw*, e chamamos esse processo de transmissão. O transmissor em produção é um script SQL responsável por conectar e integrar bancos de dados, permitindo operações de leitura e escrita. Ele é executado no banco eSUS do município e segue o seguinte fluxo:

![image](https://github.com/ImpulsoGov/desafios-processos-seletivos/blob/main/202307_EngenhariadeDados/Captura%20de%20tela%20de%202023-06-26%2014-32-34.png?raw=true)

1️⃣ Agendador de tarefas aciona o script

2️⃣ Estabelece conexão com o banco de dados da Impulso, importa tabelas onde serão armazenados os dados das listas nominais e consulta o código fonte para a geração de relatórios.

3️⃣ Cria views materializadas das listas nominais com base no código fonte consultado.

4️⃣ Consulta os dados provenientes das views materializadas e insere nas tabelas importadas.

5️⃣ Registra um log da execução da tarefa.

Você pode ver mais sobre o transmissor [aqui](https://www.canva.com/design/DAFoc8VtzV0/8n38KGe3KGHP7G4V0AzSlA/view?utm_content=DAFoc8VtzV0&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink).

Atualmente, o processo de instalação deste transmissor passa por um processo manual, onde um profissional da impulso acessa a máquina do município via acesso remoto, instala as dependências necessárias, registra a tarefa agendada no sistema operacional (windows ou linux) e faz uma primeira execução de testes.

Após essa primeira execução, as primeiras tabelas enviadas ao banco ImpulsoGov são analisadas a fim de analisar possíveis problemas, e após aprovado,  o processo de instalação é concluído.

Porém, os servidores municipais não têm um único cenário, e sim vários cenários como pode ser observado [nesse site](https://sisaps.saude.gov.br/esus/).

Nosso transmissor é instalado em um único computador com a aplicação e-SUS APS PEC instalado e apenas naquele com os dados de todas as unidades de saúde (ou seja, aquele responsável por mandar para o centralizador nacional). Dessa forma conseguimos com uma única instalação do transmissor capturar diariamente todas as informações do município.

Nem todos os municípios mantêm esse servidor municipal ligado 100% do tempo, motivos para o desligamento da máquina envolvem:

- Máquina desligada nos finais de semana e feriado
- Máquina ligada apenas durante horário de trabalho da secretaria de saúde
- Apagões de energia
- Manutenção ou troca da máquina

Muitas vezes esse servidor não é uma máquina dedicada, e sim um computador administrativo da secretaria de saúde, onde profissionais acabam usando para seu trabalho.

Todos esses problemas acarretam no problema de reinstalação, onde nosso transmissor passa a não funcionar e temos que voltar a etapa de acesso remoto aquele município.

## Desafio

Com toda a contextualização dada acima, precisamos entender a sua capacidade de comunicar e se organizar no *debug* de problemas que possam ocorrer em nosso dia a dia. Seu papel dá impulso será metade tecnológico, metade suporte, então esperamos uma capacidade tanto de identificar o ponto de falha em nosso pipeline de dados quanto se comunicar com o profissional da prefeitura responsável.

Considere o seguinte cenário:

Com o crescimento cada vez maior da quantidade de municípios parceiros, a Impulso passa a ter um frequência de 20 municípios por semana com problemas em suas transmissões e 10 municípios por semana para receberem instalações pela primeira vez, tornando inviável analisar cuidadosamente cada uma delas.

A seguinte lista como os principais quatro problemas:

1 - Transmissor removido do executor de agendamento de tarefas do sistema operacional

2 - Máquina está sempre desligada na hora programada

3 - Constantes inconsistências (2-4 dias seguidos) devido apagões na região

4 - Unidade Básica de saúde não enviou os dados para o e-SUS APS PEC centralizador

Considerando que sabemos a ordem dos principais problemas anteriormente solucionados, proponha um processo para mitigar o trabalho manual de acessos remotos a essas máquinas. Essa solução pode ser técnica ou de comunicação com o município, o importante é reduzir a quantidade de tempo reservado para acessos remotos para manutenção.

## Entregável

A sua solução pode ser entregue no formato de sua preferência (vídeo/texto). Não é necessário codificar nada, porém soluções técnicas podem vir acompanhadas de diagramas ou referências.

Você pode propor solução para cada um dos problemas listados ou apenas alguns, recomendamos priorizar de acordo com a ordem apresentada.