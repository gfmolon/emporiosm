# Diagnóstico — Empório São Marcos

Análise do código local em 01/10/2026. Não houve auditoria do site publicado, confirmação comercial dos preços ou teste real de envio ao WhatsApp.

## O que já funciona bem

O projeto oferece presentes, tábuas de frios, cotações e visitas em uma interface pensada para celular. HTML, CSS e JavaScript sem dependências deixam a manutenção e a hospedagem simples. O WhatsApp concentra o atendimento e evita exigir cadastro do cliente.

## Melhorias prioritárias

| Prioridade | Encontrado | Melhorar |
|---|---|---|
| Alta | Produtos e preços ficam escritos no HTML; não existe estoque conectado. | Confirmar preços, variantes e disponibilidade com a loja; depois criar cadastro administrável. |
| Alta | Pedido e visita apenas abrem uma mensagem; não geram registro ou confirmação. | Manter a comunicação como solicitação. Se houver necessidade operacional, integrar uma base de pedidos com status e confirmação. |
| Alta | O catálogo estava acessível apenas no fluxo de presentes e em um link externo. | Implementado catálogo interno com busca, categorias e sacola. |
| Alta | Abertura com `noopener` podia retornar nulo e provocar redirecionamento adicional. | Corrigida para uma única navegação ao WhatsApp. |
| Média | Datas tinham limite visual, mas faltava validação no envio; quantidades aceitavam frações. | Corrigida validação de datas e quantidades inteiras em cotações e visitas. |
| Média | Trocas de tela não moviam foco e faltava foco visível consistente. | Implementados foco nos títulos, indicação de foco e anúncio da sacola. Fazer auditoria completa de acessibilidade como próximo passo. |
| Média | README descrevia produtos, etapas e obrigatoriedades antigas, com referências quebradas. | Documentação reescrita para refletir o código atual. |
| Média | Todo o código está em um arquivo grande. | Separar catálogo, estilos e lógica quando o projeto crescer; não é necessário migrar para um framework agora. |
| Futuro | Não existe medição de abandono ou conversão. | Definir métricas de busca, sacola e intenção de pedido, com tratamento adequado dos dados. |

## Mini app entregue

A nova área Loja reutiliza os 37 produtos existentes e as três tábuas de frios: 40 opções no total. Inclui busca sem distinção de acentos, filtros por categoria, adição e remoção de unidades, limite de 99 unidades por produto, cálculo do total estimado, retirada ou consulta de entrega e observações. A mensagem final inclui os itens, quantidades, valores e recebimento.

A sacola permanece apenas durante a sessão da página e é perdida ao recarregar. Não há pagamento online, frete automático, reserva de estoque ou confirmação automática. As escolhas e os valores precisam ser confirmados pela loja no WhatsApp. Produtos agrupados com múltiplas variantes mantêm os nomes originais; a variante deve ser combinada no atendimento.

## Próxima evolução recomendada

Primeiro validar catálogo e preços com o responsável da loja. Depois observar o uso do mini app para decidir entre melhorar o atendimento pelo WhatsApp ou adicionar painel administrativo, estoque e acompanhamento de pedidos. Isso evita criar uma operação de e-commerce que a loja ainda não utiliza.
