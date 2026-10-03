# Funcionalidades e regras

## Início

A tela inicial apresenta três opções principais: Conheça nossos produtos, Montar um presente e Agendar uma visita. Abaixo, links menores dão acesso à cotação, contato e horários e ao catálogo de vinhos no Google Drive. O cabeçalho usa uma fonte serifada encorpada e uma descrição curta. O botão Início aparece nas demais telas.

## Loja e sacola

O catálogo reúne os 37 produtos de `PRODUCTS` e as três opções de `BOARD_OPTIONS`, totalizando 40 opções na versão documentada. As categorias são derivadas dos dados; as tábuas recebem a categoria Tábuas de frios.

A busca procura no nome e na categoria, ignorando diferenças de maiúsculas e acentos. Busca e filtro de categoria funcionam em conjunto. A tela informa o número de resultados e apresenta uma mensagem quando não encontra produtos.

Cada clique em Adicionar + inclui uma unidade. O botão mantém uma única linha; a quantidade aparece discretamente abaixo quando o produto está na sacola. Um aviso temporário confirma a adição. A barra fixa no rodapé mostra a quantidade total de unidades e o valor estimado, com acesso à sacola.

Na sacola, os controles permitem aumentar ou diminuir a quantidade, de 1 a 99 unidades por produto. Diminuir de 1 para 0 remove o produto. Ao atingir 99, a adição fica desabilitada. A solicitação fica desabilitada quando a sacola está vazia.

O cliente seleciona retirada ou consulta de entrega e pode escrever até 1.000 caracteres de observações. A conclusão abre o WhatsApp com produtos, quantidades, subtotais, total estimado, recebimento e observações. O cliente ainda precisa enviar a mensagem.

## Presentes

O fluxo possui cinco etapas, com indicador de progresso e botões fixos Voltar e Continuar:

1. Data e período: opcionais; a data, quando preenchida, não pode ser anterior ao dia atual. Há uma ação para pular os dois campos.
2. Ocasião: opcional; aniversário, especial, comemoração, agradecimento ou outro, com descrição livre opcional.
3. Tipo: escolha obrigatória entre kit e tábua de frios.
4. Composição: seleção opcional de produtos para o kit, ou escolha obrigatória do tamanho da tábua e quantidade de 1 a 99.
5. Finalização: mensagem de cartão opcional, recebimento e resumo. A ação final abre o WhatsApp.

No kit, cada produto pode ser selecionado uma vez ou removido. A estimativa soma a base de montagem (`KIT_BASE_PRICE`, atualmente R$ 15,00) aos itens selecionados. É possível continuar sem produtos, para pedir uma sugestão ao Empório.

Na tábua, a estimativa é preço da opção multiplicado pela quantidade. As opções atuais são pequena (2 pessoas, R$ 65,00), média (4 pessoas, R$ 95,00) e grande (6 pessoas, R$ 135,00). A quantidade de pessoas corresponde a cada tábua.

Ao mudar para kit, a tábua selecionada é removida e sua quantidade volta a 1. Ao mudar para tábua, as preferências de produtos do kit são removidas. A sacola da loja é independente desse fluxo.

## Cotação

Solicita quantidade aproximada, faixa de valor por presente, data opcional, contato e observações opcionais. As faixas são até R$ 100, R$ 100–150, R$ 150–250 e acima de R$ 250.

Quantidade deve ser um inteiro positivo. Contato é obrigatório, em um campo único de nome e telefone; o sistema verifica apenas se está preenchido, sem validar o formato do telefone. Data preenchida não pode ser passada. As observações ficam recolhidas em Adicionar observações. O botão Solicitar cotação permanece fixo no rodapé e abre uma mensagem no WhatsApp.

## Visitas

Permite escolher uma ou mais atividades: Memorial, degustação, compras na loja, grupo/excursão, almoço e lanches/café colonial. Ao menos uma atividade é obrigatória.

Solicita data opcional, período, quantidade de pessoas, contato e observações opcionais recolhidas. Pessoas deve ser um inteiro positivo. Contato deve estar preenchido, sem validação de formato. Data preenchida não pode ser passada. O botão Solicitar visita permanece fixo no rodapé.

A mensagem enviada é uma solicitação: não reserva um horário nem confirma o atendimento.

## Contato

Oferece conversa no WhatsApp, perfil do Instagram, endereço no Google Maps e painel expansível de horários. Os horários cadastrados são segunda a sexta das 8h às 19h e sábado e domingo das 9h às 15h.

## Experiência móvel e acessibilidade

A interface tem largura máxima de 620 px e ajustes específicos até 520 px. Os produtos aparecem em duas colunas. Textos e espaços foram reduzidos para antecipar as ações. As barras inferiores consideram a área segura do celular; o conteúdo tem espaço inferior para não ficar coberto.

Trocas de tela movem o foco para o título. Controles de quantidade têm rótulos acessíveis; sacola e avisos usam regiões de status. Há destaque de foco e suporte a preferência por movimento reduzido em partes da interface. Esses recursos não substituem uma auditoria completa de acessibilidade.

## Limitações

Não há backend, banco de dados, cadastro de clientes, painel administrativo, pagamento, cálculo de frete, controle de estoque, reserva ou histórico de pedidos. Não há armazenamento persistente nem sincronização entre dispositivos. Recarregar a página perde a sacola e as escolhas.

Preços e disponibilidade precisam ser confirmados pela loja. Nomes com múltiplas variantes mantêm o agrupamento do catálogo original; a variante é combinada no atendimento. Abrir o WhatsApp não significa que a mensagem foi enviada, recebida ou que a solicitação foi confirmada.
