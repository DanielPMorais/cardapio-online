## Cardápio Online

Aplicação web estática para apresentar um cardápio online com categorias (burgers, churrasco, pizzas, sobremesas, bebidas e steaks), animações, layout responsivo e um fluxo simples de pedido via WhatsApp com cálculo de entrega e coleta do endereço via CEP (ViaCEP).

### Demonstração rápida
- Listagem paginada por categoria (8 itens iniciais + botão "Ver mais").
- Carrinho com ajuste de quantidades, subtotal, taxa de entrega e total.
- Coleta de endereço com busca de CEP (ViaCEP).
- Link de finalização do pedido exportado para WhatsApp.
- Botões rápidos: Ligar, Instagram, Facebook, Whatsapp e Reserva.

## Sumário
- Instalação e execução local
- Estrutura do projeto
- Tecnologias utilizadas
- Como editar o cardápio (dados e imagens)
- Configurações (WhatsApp, redes sociais, entrega)
- Personalização de layout
- Publicação (deploy)
- Acessibilidade e SEO
- Licença

## Instalação e execução local
Por ser um site estático, você pode simplesmente abrir o `index.html` no navegador. Para evitar problemas de CORS e ter URLs limpas, recomenda-se usar um servidor estático local:

```bash
# Opção Python (recomendado)
python3 -m http.server 8080
# Acesse: http://localhost:8080

# Opção Node (serve)
npx --yes serve -l 8080
# Acesse: http://localhost:8080
```

## Estrutura do projeto
- `index.html`: página principal do site.
- `css/`: estilos (Bootstrap, Font Awesome, animações, estilos do projeto e responsivo).
- `js/`:
  - `dados.js`: base de dados do cardápio (`MENU` por categoria, com `id`, `img`, `name`, `dsc`, `price`).
  - `app.js`: lógica principal do cardápio e carrinho (eventos, etapas, CEP e WhatsApp).
  - Demais libs: jQuery, Bootstrap, WOW.js, Modernizr, Popper.
- `img/`: imagens do site e dos itens do cardápio (subpastas por categoria em `img/cardapio/`).
- `fonts/`: fontes (Poppins) e webfonts do Font Awesome.

## Tecnologias utilizadas
- HTML5, CSS3, JavaScript (jQuery)
- Bootstrap 4
- Font Awesome
- Animate.css + WOW.js (animações no scroll)
- Modernizr (detecção de features)

## Como editar o cardápio
Os itens estão definidos em `js/dados.js` na constante global `MENU`. Cada categoria contém um array de itens no formato:

```javascript
{
  id: "unique-id",
  img: "./img/cardapio/<categoria>/<arquivo>.jpg",
  name: "Nome do produto",
  dsc: "Descrição do produto",
  price: 99.90
}
```

Passos para adicionar/alterar itens:
1. Adicione a imagem em `img/cardapio/<categoria>/` e referencie-a em `img`.
2. Edite/adicione o objeto do item na categoria correta em `js/dados.js`.
3. Mantenha `id` único por item.

Categorias disponíveis no momento: `burgers`, `churrasco`, `pizzas`, `sobremesas`, `bebidas`, `steaks`.

### Categoria inicial
Por padrão, a categoria carregada é `burgers`. Para alterar, edite em `js/app.js` o método `obterItensCardapio(categoria = 'burgers', ...)` e troque o valor padrão.

## Configurações
As principais configurações estão no topo de `js/app.js`:

```javascript
let MEU_CARRINHO = [];
let MEU_ENDERECO = null;

let VALOR_CARRINHO = 0;
let VALOR_ENTREGA = 5; // taxa fixa de entrega

let INSTAGRAM_EMPRESA = 'seu_usuario_instagram';
let FACEBOOK_EMPRESA = 'sua_pagina_facebook';
let CELULAR_EMPRESA = '55DDDNUMERO'; // ex: 5511999999999
```

- `VALOR_ENTREGA`: taxa fixa somada ao total.
- `CELULAR_EMPRESA`: usado para gerar o link `wa.me` do WhatsApp.
- `INSTAGRAM_EMPRESA` e `FACEBOOK_EMPRESA`: usados nos botões de redes sociais.

### Fluxo de compra
1. Usuário seleciona categoria e itens (8 primeiros exibidos; "Ver mais" mostra até 12).
2. Adiciona itens ao carrinho, ajusta quantidades.
3. Informa endereço (CEP consultado via ViaCEP).
4. Resumo exibe itens, endereço e total (subtotal + entrega).
5. Botão redireciona para o WhatsApp com a mensagem formatada do pedido.

## Personalização de layout
- Cores, espaçamentos e componentes: `css/style.css`.
- Ajustes responsivos: `css/responsivo.css`.
- Tipografia (Poppins) e ícones (Font Awesome) já incluídos no projeto.

## Publicação (deploy)
Por ser estático, você pode publicar facilmente:
- GitHub Pages: publique o conteúdo da pasta no branch `gh-pages` ou configure Pages no repositório.
- Netlify/Vercel: arraste e solte ou conecte o repositório; defina a pasta raiz como o próprio projeto.
- Qualquer servidor estático: sirva a pasta diretamente.

## Acessibilidade e SEO
- Use textos alternativos (`alt`) descritivos nas imagens dos produtos.
- Ajuste metas de SEO no `index.html` (título, descrição, favicon).
- Garanta contraste adequado ao personalizar cores.

## Licença
Este projeto foi liberado ao domínio público sob a The Unlicense. Consulte o arquivo `LICENSE` para detalhes.

## Créditos
- Imagens, marcas e nomes de produtos são exemplos ilustrativos.
- Bibliotecas de terceiros respeitam suas respectivas licenças.


