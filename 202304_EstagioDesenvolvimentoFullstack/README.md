# Desafio ImpulsoGov | Desenvolvedor Fullstack

Este arquivo contém as instruções de dois desafios que constituem a primeira etapa da avaliação técnica para a vaga de Estágio em desenvolvimento Fullstack.

**Atenção:** Nenhum código feito por você será usado pela Impulso Gov sem sua permissão.


## Instruções Gerais 
- **Seus desafios deve ser entregue até domingo (23/04/2022), às 23:59**. 
- Você deve enviar um email com suas soluções para gabrielle@impulsogov.org.

## Desafio 1 - Animação

Na Impulso estamos sempre buscando aprimorar os nossos sistemas. Com sua ajuda queremos melhorar a nossa [página institucional inicial](https://www.impulsogov.org/), tranformando hoje o nosso banner estático em uma animação - como segue em GIF abaixo - e gerar assim mais empatia com nossos usuários.

Para isso esperamos que você crie um componente em React que faça de digitação (somente a parte de digitação do texto e nenhum outro elemento do GIF abaixo). Você pode se basear [nesse componente](https://designsystem.impulsogov.org/#/componentes/header), que tem código [aqui](https://github.com/ImpulsoGov/DesignSystem/blob/producao/componentes/Header/Header.css) para informações do css.

![](https://raw.githubusercontent.com/ImpulsoGov/desafios-processos-seletivos/2da6b351808c3233cecbfdc68e26b2e642039c76/20220711_DesenvolvedorFullstack/animacao_home.gif)

### Entrega
- Para esta entrega você é livre para o formato das suas entregas, sugere-se fortemente a entrega de **no Codepen com seu componente**, como este [exemplo](https://codepen.io/lbain/pen/ENpzBZ).

**Para ir além:** você pode implementar sua animação em uma aplicação, dar deploy em sua plataforma favorita e compartilhar conosco 😀.


## Desafio 2 - Componente em JS

Criar um componente Reactjs (JS) que receberá um JSON com nomes e notas como propriedade:

[
  {
    "nome" : "José Alves Dos Santos",
    "nota" : 37
  },  
  {
    "nome" : "Anderson Da Silva",
    "nota" : 49
  },
  {
    "nome" : "Maria Ferreira",
    "nota" : 68
  },  
  {
    "nome" : "Ana Oliveira",
    "nota" : 87
  }
]

O nome deve ser exibido pelo componente centralizado na vertical e na horizontal e em ordem alfabética, se a nota do menor que 5, o nome deve aparecer em vermelho, se a nota for maior ou igual a 5, o nome deve aparecer em verde:

O codigo pode ser implementado na plataforma [One compiler](https://onecompiler.com/react)


### Entrega
- Para esta entrega esperamos um repositório público ou privado (compartilhado com o email gabrielle@impulsogov.org e danilo@impulsogov.org) no github que possa ser rodado localmente ou já hosteado.

