# Empório São Marcos

Mini app para clientes do Empório São Marcos, em HTML, CSS e JavaScript puro.

## Funcionalidades

- Loja: catálogo com busca e categorias, sacola com quantidades, total estimado e solicitação de pedido pelo WhatsApp.
- Presentes: fluxo de cinco etapas para montar um kit ou escolher uma tábua de frios; data, ocasião e mensagem opcionais.
- Cotação: quantidade inteira, faixa de valor, contato, data opcional e detalhes.
- Visitas: interesses, quantidade inteira de pessoas, contato, data opcional e observações.
- Contato: WhatsApp, Instagram, mapa e horários cadastrados.

## Uso local

Abra `index.html` no navegador ou execute `python3 -m http.server 8080` nesta pasta e acesse `http://localhost:8080`.

## Operação

O catálogo e os preços ficam nos arrays `PRODUCTS` e `BOARD_OPTIONS` em `index.html`. O número de atendimento está em `WHATSAPP_NUMBER`. Os dados comerciais foram preservados do projeto e precisam ser confirmados pelo responsável da loja.

Não existe backend, banco de dados, autenticação, estoque ou pagamento online. A sacola fica em memória e é perdida ao recarregar. Ao finalizar, o cliente abre o WhatsApp com a mensagem pronta e precisa enviá-la. O Empório confirma disponibilidade, preço, entrega e pagamento.

A estrutura atual continua compatível com hospedagem estática. Nenhuma publicação é realizada ao editar os arquivos localmente.

Veja [DIAGNOSTICO.md](DIAGNOSTICO.md) para as prioridades de melhoria e limitações.
