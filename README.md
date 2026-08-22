# EmpórioSM — Documentação do MVP Atual

## 1. Visão geral

O **EmpórioSM** é uma aplicação web desenvolvida para o **Empório São Marcos**, com foco em facilitar ações comerciais e de atendimento diretamente pelo navegador.

A proposta atual é oferecer uma experiência simples, rápida e orientada a tarefas. Em vez de funcionar como um site institucional tradicional com várias páginas, o projeto foi estruturado como uma pequena aplicação em que o usuário escolhe o que deseja fazer e segue um fluxo específico.

Atualmente, o sistema concentra quatro ações principais:

- montar um presente;
- pedir uma cotação;
- agendar uma visita;
- acessar informações de contato.

Também existe acesso direto ao catálogo de vinhos.

---

## 2. Objetivo do projeto

O objetivo do MVP é permitir que clientes do Empório São Marcos realizem ações comuns de forma organizada antes de entrar em contato com o estabelecimento.

A aplicação procura reduzir mensagens genéricas e facilitar o atendimento, fazendo com que algumas informações importantes já sejam preenchidas pelo cliente.

Entre elas:

- data desejada;
- ocasião do presente;
- produtos escolhidos;
- quantidade de presentes;
- faixa de valor;
- tipo de visita;
- quantidade de pessoas;
- observações.

Ao final dos fluxos, essas informações são organizadas automaticamente e encaminhadas para o WhatsApp do Empório. :contentReference[oaicite:0]{index=0}

---

## 3. Estrutura atual

A aplicação foi construída em uma única página utilizando:

- HTML5;
- CSS3;
- JavaScript puro.

Nesta versão não existe:

- backend;
- banco de dados;
- sistema de autenticação.

Toda a interação acontece diretamente no navegador.

A interface é dividida em seções internas que são exibidas ou ocultadas conforme o usuário navega pela aplicação.

---

## 4. Tela inicial

A tela inicial apresenta quatro ações principais:

### Montar um presente

Inicia um fluxo guiado para personalização de um presente.

### Pedir uma cotação

Voltado principalmente para:

- empresas;
- eventos;
- compras em maior quantidade;
- presentes corporativos.

### Agendar uma visita

Permite solicitar uma visita ao Empório e selecionar diferentes atividades de interesse.

### Contato

Apresenta os canais e informações principais do estabelecimento.

Além disso, existe acesso direto ao catálogo de vinhos.

---

## 5. Fluxo de montagem de presente

O processo de montagem de presente possui cinco etapas.

### Etapa 1 — Data e horário

O usuário informa:

- data desejada;
- período aproximado.

Os períodos disponíveis atualmente são:

- manhã;
- tarde;
- fim da tarde.

A aplicação impede a seleção de datas anteriores ao dia atual.

### Etapa 2 — Ocasião

O usuário escolhe a ocasião do presente:

- aniversário;
- especial;
- comemoração;
- agradecimento.

Uma opção deve ser escolhida para continuar.

### Etapa 3 — Base do presente

O usuário escolhe a base que será utilizada.

| Base | Valor inicial |
|---|---:|
| Cesta | R$ 25,00 |
| Caixa | R$ 20,00 |
| Tábua | R$ 35,00 |
| Kit | R$ 15,00 |

O valor da base é automaticamente incluído no cálculo do presente.

### Etapa 4 — Produtos

O usuário pode adicionar produtos ao presente.

Produtos atualmente cadastrados:

| Produto | Valor |
|---|---:|
| Vinho da Serra | R$ 59,90 |
| Queijo colonial | R$ 28,00 |
| Salame artesanal | R$ 24,90 |
| Chocolate | R$ 16,00 |
| Geleia artesanal | R$ 18,50 |
| Espumante | R$ 69,90 |

Os produtos podem ser adicionados ou removidos.

O sistema calcula automaticamente:

`valor da base + produtos selecionados = valor estimado`

### Etapa 5 — Finalização

Na última etapa o usuário pode:

- escrever uma mensagem para o cartão;
- escolher retirada no Empório;
- escolher entrega.

Também é apresentado um resumo contendo:

- base escolhida;
- produtos adicionados;
- valores;
- valor total estimado.

Ao finalizar, o sistema gera automaticamente uma mensagem com todas as informações e abre o WhatsApp do Empório.

---

## 6. Sistema de cotação

A área de cotação foi criada para situações envolvendo maior quantidade de presentes ou compras empresariais.

O formulário solicita:

- quantidade aproximada;
- faixa de valor por presente;
- data desejada;
- nome e telefone;
- descrição da necessidade.

As faixas disponíveis atualmente são:

- até R$ 100;
- R$ 100 a R$ 150;
- R$ 150 a R$ 250;
- acima de R$ 250.

Antes do envio, o sistema verifica se os campos principais foram preenchidos.

Depois disso, uma mensagem é montada automaticamente e aberta no WhatsApp.

---

## 7. Agendamento de visitas

O sistema também possui uma área destinada ao agendamento de visitas.

O usuário pode selecionar uma ou mais opções:

- visita ao Memorial;
- degustação;
- compras na loja;
- grupo ou excursão;
- almoço;
- lanches / café colonial.

Depois são solicitados:

- data desejada;
- horário aproximado;
- quantidade de pessoas;
- nome e telefone;
- observações.

É obrigatório selecionar pelo menos uma atividade.

Ao final, a aplicação organiza todas as informações e abre uma mensagem pronta no WhatsApp.

O horário solicitado ainda precisa ser confirmado pelo Empório. :contentReference[oaicite:1]{index=1}

---

## 8. Área de contato

A aplicação possui uma área com as principais informações do Empório.

### WhatsApp

Permite iniciar uma conversa direta com o estabelecimento.

### Instagram

Perfil:

`@empsaomarcos`

### Como chegar

A aplicação abre o Google Maps utilizando o endereço:

**BR-116, km 113, nº 1223, Bairro Industrial, São Marcos - RS**

### Horários

- segunda a sexta: 8h às 19h;
- sábado e domingo: 9h às 15h.

---

## 9. Integração com WhatsApp

O WhatsApp é atualmente o principal meio de conclusão das ações.

A aplicação não envia os dados para um servidor.

O JavaScript utiliza as informações preenchidas pelo usuário para montar automaticamente uma mensagem e abrir uma conversa no WhatsApp.

Isso acontece nos fluxos de:

- montagem de presente;
- cotação;
- agendamento de visita;
- contato geral.

Essa abordagem permite manter o MVP simples e funcional sem necessidade de backend ou banco de dados. :contentReference[oaicite:2]{index=2}

---

## 10. Validações

O sistema já possui algumas validações básicas.

Entre elas:

- exigir data para o presente;
- exigir uma ocasião;
- exigir uma base;
- validar quantidade da cotação;
- exigir data da cotação;
- exigir contato da cotação;
- exigir pelo menos uma atividade na visita;
- exigir data da visita;
- validar quantidade de pessoas;
- exigir contato para o agendamento.

Quando existe algum problema, o campo recebe destaque visual e uma mensagem de erro.

---

## 11. Interface e responsividade

A interface foi desenvolvida principalmente pensando no uso pelo celular.

O conteúdo possui largura máxima de aproximadamente 560 px, criando uma experiência parecida com um aplicativo.

Características atuais:

- layout centralizado;
- cartões grandes;
- botões fáceis de tocar;
- poucos elementos por tela;
- navegação por etapas;
- indicador de progresso;
- barra inferior durante a montagem do presente;
- cores claras e terrosas;
- tipografia simples;
- adaptação para telas maiores.

---

## 12. Navegação

A aplicação funciona como uma pequena **Single Page Application (SPA)**, mesmo sem utilizar frameworks.

As principais seções são:

```text
home
step1
step2
step3
step4
step5
quote
visit
contact
