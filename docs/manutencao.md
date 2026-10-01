# Manutenção e publicação

## Executar localmente

Abra `index.html` no navegador ou, na raiz do projeto, execute:

```sh
python3 -m http.server 8080
```

Acesse `http://localhost:8080`. Não é necessário instalar dependências ou executar build.

## Alterações comuns

| Alteração | Onde procurar em `index.html` |
|---|---|
| Produtos, categorias e preços | `const PRODUCTS` |
| Tábuas, porções, ingredientes e preços | `const BOARD_OPTIONS` |
| Base do kit | `const KIT_BASE_PRICE` |
| WhatsApp | `const WHATSAPP_NUMBER` |
| Instagram e endereço | Eventos de `instagramBtn` e `mapsBtn`, e conteúdo de contato |
| Horários | `hoursBox` |
| Catálogo externo | Link em `.home-extra` |
| Cor e identidade visual | `:root` e `.brand` |
| Layout móvel | Blocos `@media(max-width:520px)` |
| Texto dos pedidos | Handlers de `nextBtn`, `shopCheckout`, `quoteWhatsApp` e `visitWhatsApp` |

Exemplo de produto:

```js
{ category:'Sucos', name:'Suco exemplo 1 L', price:20.00 }
```

Use números, sem `R$` e com ponto decimal. A categoria nova aparece automaticamente. Os produtos alimentam loja e kit; as tábuas alimentam loja e fluxo de presentes. Confirme com a loja qualquer mudança comercial.

## Verificação antes de publicar

Para uma alteração apenas documental, confira links relativos, nomes de funções e a correspondência entre texto e código. Para alterações de interface ou comportamento, revise os fluxos afetados.

```sh
git diff --check
node -e 'const fs=require("fs"); const html=fs.readFileSync("index.html","utf8"); new Function(html.match(/<script>([\s\S]*?)<\/script>/)[1]); console.log("Sintaxe JavaScript válida");'
```

O comando de sintaxe exige Node.js disponível e apenas verifica parsing; não testa interação ou apresentação. Não há uma suíte de testes automatizados versionada. Verificações temporárias usadas durante as melhorias não fazem parte do repositório.

Roteiro funcional recomendado conforme a mudança:

- Início: acessar as cinco ações e voltar sem perder seleções.
- Loja: buscar com e sem acentos; filtrar; obter zero resultados; adicionar unidades; conferir aviso, quantidade e total; remover item; verificar limite de 99 e sacola vazia.
- Presente: navegar pelas cinco etapas, pular opcionais, testar kit sem produtos, trocar tipo, escolher tábua e conferir resumo.
- Cotação e visita: rejeitar quantidade zero ou fracionada, contato vazio e data passada; visita exige uma atividade.
- WhatsApp: conferir o destino e o texto preparado; abrir a conversa não comprova envio. Evite enviar pedidos reais apenas para testar.
- Celular: conferir larguras de 320, 375 e 390 px, textos longos, rolagem, teclado aberto, botões fixos e área segura. Conferir também o desktop.
- Acessibilidade: navegar por teclado, verificar foco ao trocar de tela e anúncio de adição na sacola.

## Publicação em produção

O repositório é `gfmolon/emporiosm` no GitHub. A produção usa GitHub Pages, publicando a raiz (`/`) da branch `main`. O arquivo `CNAME` contém `emporiosm.com.br`. Preserve-o em alterações estruturais.

Um push na `main` dispara a publicação. Revise os arquivos antes de executar:

```sh
git status --short
git add <arquivos-revisados>
git commit -m "Descrição da mudança"
git push origin main
```

Quando GitHub CLI estiver instalado e autenticado, confira a configuração e o resultado:

```sh
gh api repos/gfmolon/emporiosm/pages
gh api repos/gfmolon/emporiosm/pages/builds/latest --jq '{status,commit,error}'
```

Aguarde `status: built` e confira se `commit` corresponde ao commit enviado. Também verifique o conteúdo do domínio. Apenas o sucesso do push não confirma que a publicação terminou.

Nas verificações realizadas, o site respondeu com `Cache-Control: max-age=600`, permitindo cache por até dez minutos. Quando uma mudança ainda não aparecer no navegador, use uma URL com parâmetro novo, por exemplo `https://emporiosm.com.br/?v=<commit>`, ou recarregue após o cache expirar. O parâmetro não modifica o funcionamento do app.

A pasta `docs` é documentação do repositório; não é uma nova tela do app. Como está na raiz publicada, seu conteúdo deve ser considerado público: não inclua credenciais ou dados de clientes. O GitHub também permite ler os arquivos Markdown formatados no repositório.

## Corrigir uma publicação problemática

Faça uma correção pequena e publique novamente. Se precisar desfazer um commit específico, prefira `git revert <commit>` e envie o novo commit, após revisar o resultado. Evite reescrever a história da `main` com force push.

## Manter a documentação

Atualize `funcionalidades.md` ao mudar regras ou telas; `implementacao.md` ao mudar arquitetura, estado ou funções; e este guia ao mudar a hospedagem ou o procedimento de manutenção. Ao adicionar persistência, estoque ou pagamentos, revise também as limitações documentadas.
