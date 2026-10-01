# Implementação

## Estrutura e execução

A aplicação é estática, sem framework ou dependências de execução. `index.html` contém metadados, CSS em `<style>`, telas HTML e JavaScript em `<script>` ao final do documento. Não há etapa de compilação ou gerenciador de pacotes configurado.

| Arquivo | Finalidade |
|---|---|
| `index.html` | Aplicação completa |
| `CNAME` | Domínio personalizado do GitHub Pages |
| `README.md` | Apresentação e entrada para a documentação |
| `docs/` | Referência funcional e técnica para manutenção |

## Navegação

As telas são seções com classe `.section`: `home`, `shop`, `step1` a `step5`, `quote`, `visit` e `contact`. A classe `.active` determina qual está visível.

`show(id)` limpa erros, atualiza `current`, alterna as seções, controla o botão Início e a barra do presente, prepara a etapa 4 ou o resumo quando necessário, move o foco para o título e retorna ao topo. Não há roteador, alteração da URL ou integração com o histórico do navegador. O botão Voltar do navegador não navega entre as etapas.

Botões com `data-go` chamam `show()`. O array `order` identifica as etapas que usam `bottomBar`. Não remova IDs ou atributos sem conferir os seletores e eventos associados.

## Dados e estado

| Identificador | Uso |
|---|---|
| `PRODUCTS` | Produtos com `category`, `name` e `price` |
| `BOARD_OPTIONS` | Tábuas com `name`, `people`, `price` e `ingredients` |
| `KIT_BASE_PRICE` | Valor inicial da montagem do kit |
| `WHATSAPP_NUMBER` | Destino das mensagens, em formato internacional somente com dígitos |
| `items` | `Map` de nome para preço das preferências do kit |
| `giftType`, `selectedBoard`, `boardQuantity` | Tipo, tamanho e quantidade do presente |
| `occasionName`, `noMessage` | Estado da ocasião e cartão |
| `shopCatalog` | Catálogo derivado de produtos e tábuas |
| `shopBag` | `Map` de índice de `shopCatalog` para quantidade |
| `shopCategory` | Categoria selecionada na loja |

O estado fica em memória; campos adicionais ficam no DOM. Loja e presentes não compartilham a seleção. Voltar ao início não limpa automaticamente os dados.

Os índices identificam produtos apenas durante a sessão. Se no futuro houver persistência, use identificadores estáveis antes de gravar a sacola. No kit, nomes são chaves; produtos diferentes com nomes iguais colidem.

## Funções principais

| Função | Responsabilidade |
|---|---|
| `renderShop()` | Categorias, busca, contagem e cartões de produtos |
| `renderBag()` | Itens, controles, totais, barra fixa, indicação por produto e habilitação de botões |
| `notifyShop(message)` | Aviso de adição por 2,6 segundos; cancela o temporizador anterior |
| `renderProducts()` | Produtos do kit agrupados por categoria |
| `renderBoards()` | Opções de tábua e indicação da seleção |
| `renderStep4()` | Alterna composição do kit e da tábua |
| `renderSummary()` | Resumo da etapa final do presente |
| `getTotal()` | Total estimado do presente |
| `getOccasion()`, `getMessage()` | Texto final da ocasião e mensagem do cartão |
| `todayISO()`, `validDate(el)` | Data local e rejeição de datas passadas |
| `validateCurrentStep()` | Validação das etapas obrigatórias do presente |
| `showError()`, `showGridError()`, `clearErrors()` | Exibição e remoção de erros |
| `money(n)` | Formatação monetária em pt-BR/BRL |
| `normalizeSearch(value)` | Normalização de caixa e acentos para busca |
| `escapeHTML(value)` | Escape de caracteres especiais nos templates da loja |
| `openWhatsApp(text)` | Codificação e navegação para a mensagem no WhatsApp |

Os eventos de listas geradas são delegados aos contêineres: `productsList`, `boardList`, `shopProducts` e `cartItems`. Isso permite substituir o HTML das listas sem reinstalar os eventos de cada botão.

## Totais e mensagens

A sacola soma em centavos: `Math.round(price * 100) * quantity`, convertendo para reais ao exibir. O kit soma valores em reais; `money()` formata o resultado. Nenhum valor é uma cobrança efetiva.

`openWhatsApp()` usa `encodeURIComponent(text)` e `window.location.assign()` para abrir `https://wa.me/<numero>?text=<mensagem>`. Não usa API de envio, não recebe confirmação e não salva a solicitação. Links de Instagram e Maps são abertos em outra aba com `noopener`.

Os formulários usam eventos de clique e validação explícita em JavaScript. O atributo `required` sozinho não garante validação, pois não há envio nativo de formulário. Preserve as verificações nos handlers.

## CSS e comportamento móvel

As variáveis em `:root` controlam cores, bordas e raio. `.brand` usa Palatino em negrito, com fontes alternativas locais; não há download de fonte. `.app` limita a largura e reserva espaço para barras fixas.

`.bottom` e `.shop-bag-bar` controlam as barras do presente e da sacola. `.form-submit` fixa as ações de cotação e visita. `env(safe-area-inset-bottom)` evita conflito com a área inferior de celulares. `.shop-card-action` mantém o botão compacto e a contagem separada; `.shop-add-count:empty` oculta contagens vazias.

Há regras móveis em mais de um bloco `@media(max-width:520px)`. Regras posteriores prevalecem quando têm a mesma especificidade; ao alterar espaçamentos, confira ambos. `details.optional-details` implementa observações recolhíveis sem JavaScript adicional.

## Cuidados para evolução

Mantenha valores numéricos positivos e nomes únicos no catálogo. Os templates do kit e das tábuas interpolam os dados diretamente em HTML; o escape aplicado na loja não é global. Antes de aceitar dados externos ou permitir edição administrativa, padronize a renderização segura em todos os fluxos.

Dados informados pelo cliente são incluídos na URL do WhatsApp. Não registre URLs completas com observações ou contato em logs ou ferramentas de métricas. Eventual backend deve validar pedidos e preços no servidor, além de definir persistência, privacidade e controle de acesso.

Uma futura separação de CSS, catálogo e JavaScript pode facilitar manutenção, preservando o comportamento. A versão atual não exige migração para um framework.
