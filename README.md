# Guia HTML

# Sumário

[1. Tags Estruturais](#tags-estruturais)   
[2. Tags de Texto Essenciais](#tags-de-texto-essenciais)   
[3. Tags de Listas](#tags-de-listas)   
[4. Tags de Mídia](#tags-de-mídia)   
[5. Tag DIV](#tag-div)   
[6. Tags Semânticas](#tags-semânticas)   
[7. Formulários](#formulários)   
[8. Guia de Acessibilidade](#guia-de-acessibilidade)   
[9. Links](#links)   




# Tags Estruturais

## Estrutura Básica
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <!-- meta tags e recursos -->
</head>
<body>
    <!-- conteúdo -->
</body>
</html>
```

## Tags do `<head>`

### Meta Tags Essenciais
```html
<head>
    <!-- Codificação -->
    <meta charset="UTF-8">
    
    <!-- Viewport para responsividade -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Título da página -->
    <title>Nome do Site</title>
    
    <!-- Descrição para SEO -->
    <meta name="description" content="Descrição da sua página para SEO">
    
    <!-- Palavras-chave (menos relevante hoje, mas ainda usado) -->
    <meta name="keywords" content="palavra-chave1, palavra-chave2">
    
    <!-- Autor -->
    <meta name="author" content="Nome do Autor">
</head>
```

### Meta Tags para Social Media
```html
<head>
    <!-- Open Graph (Facebook) -->
    <meta property="og:title" content="Título para compartilhamento">
    <meta property="og:description" content="Descrição para compartilhamento">
    <meta property="og:image" content="url-da-imagem.jpg">
    <meta property="og:url" content="url-da-pagina">
    
    <!-- Twitter -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="Título para Twitter">
    <meta name="twitter:description" content="Descrição para Twitter">
</head>
```

### Links para Recursos
```html
<head>
    <!-- CSS -->
    <link rel="stylesheet" href="styles.css">
    
    <!-- Favicon -->
    <link rel="icon" type="image/png" href="favicon.png">
    <link rel="apple-touch-icon" href="apple-touch-icon.png">
    
    <!-- Fontes -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
    
    <!-- Preload de recursos críticos -->
    <link rel="preload" href="fonte-principal.woff2" as="font" type="font/woff2" crossorigin>
    <link rel="preload" href="imagem-hero.jpg" as="image">
</head>
```

### Scripts no Head
```html
<head>
    <!-- Scripts que precisam carregar primeiro -->
    <script async src="analytics.js"></script>
    
    <!-- Scripts que não devem bloquear o carregamento -->
    <script defer src="nao-critico.js"></script>
    
    <!-- Scripts inline críticos -->
    <script>
        // Código crítico que precisa rodar imediatamente
        window.CONFIG = {
            // configurações importantes
        };
    </script>
</head>
```

## Atributos Importantes

### Para a tag `<html>`
```html
<html lang="pt-BR">
```

### Para meta viewport
```html
<meta 
    name="viewport" 
    content="width=device-width, initial-scale=1.0, maximum-scale=5.0"
>
```

### Para scripts
```html
<script 
    src="script.js"
    async           /* Carrega assíncrono e executa assim que possível */
    defer           /* Carrega assíncrono e executa após o HTML */
    type="module"   /* Para módulos ES6 */
    crossorigin     /* Para recursos de outros domínios */
    integrity="hash" /* Verificação de segurança */
>
</script>
```

## Boas Práticas de Organização

1. **Ordem recomendada no head**:
```html
<head>
    <!-- 1. Charset primeiro -->
    <meta charset="UTF-8">
    
    <!-- 2. Viewport -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- 3. Título -->
    <title>Nome do Site</title>
    
    <!-- 4. Meta tags descritivas -->
    <meta name="description" content="...">
    
    <!-- 5. Social media tags -->
    <meta property="og:title" content="...">
    
    <!-- 6. Preload de recursos críticos -->
    <link rel="preload" href="..." as="...">
    
    <!-- 7. CSS crítico inline -->
    <style>/* CSS crítico */</style>
    
    <!-- 8. Links para CSS externo -->
    <link rel="stylesheet" href="...">
    
    <!-- 9. Scripts críticos -->
    <script>/* Scripts críticos */</script>
    
    <!-- 10. Scripts externos com async/defer -->
    <script defer src="..."></script>
</head>
```

2. **Comentários organizacionais**:
```html
<head>
    <!-- Character Set -->
    
    <!-- Viewport -->
    
    <!-- SEO Tags -->
    
    <!-- Social Media -->
    
    <!-- Recursos Externos -->

# Tags e Scripts no Final do `</body>`

## Estrutura Básica
```html
<body>
    <!-- conteúdo do site -->

    <!-- scripts vão aqui, antes do fechamento do body -->
</body>
```

## Scripts no Final do Body

### 1. Scripts Principais
```html
<body>
    <!-- conteúdo do site -->

    <!-- jQuery (se necessário) -->
    <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>

    <!-- Scripts próprios -->
    <script src="js/main.js"></script>
    <script src="js/components.js"></script>
    <script src="js/utils.js"></script>
</body>
```

### 2. Scripts com Dependências
```html
<body>
    <!-- conteúdo -->

    <!-- Primeiro as dependências -->
    <script src="js/vendor/library.js"></script>
    
    <!-- Depois os scripts que dependem delas -->
    <script src="js/features.js"></script>
</body>
```

### 3. Scripts com Configurações
```html
<body>
    <!-- conteúdo -->

    <!-- Configurações globais -->
    <script>
        const APP_CONFIG = {
            apiUrl: 'https://api.exemplo.com',
            debug: false,
            version: '1.0.0'
        };
    </script>

    <!-- Scripts que usam as configurações -->
    <script src="js/app.js"></script>
</body>
```

### 4. Scripts de Analytics e Tracking
```html
<body>
    <!-- conteúdo -->

    <!-- Google Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=GA_ID"></script>
    <script>
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'GA_ID');
    </script>

    <!-- Outros scripts de tracking -->
    <script src="js/tracking.js"></script>
</body>
```

## Boas Práticas

### Ordem Recomendada
```html
<body>
    <!-- conteúdo -->

    <!-- 1. Bibliotecas de terceiros -->
    <script src="vendor/library1.js"></script>
    <script src="vendor/library2.js"></script>

    <!-- 2. Configurações globais -->
    <script>
        // configurações da aplicação
    </script>

    <!-- 3. Scripts principais da aplicação -->
    <script src="js/app.js"></script>
    <script src="js/components.js"></script>

    <!-- 4. Scripts não críticos -->
    <script src="js/features.js"></script>

    <!-- 5. Analytics e tracking (por último) -->
    <script src="js/analytics.js"></script>
</body>
```


# Tags de Texto Essenciais

## Tags de Título

### `<h1>` a `<h6>`
- **Função**: Define títulos e subtítulos hierárquicos
- **Exemplo**:
```html
<h1>Título Principal</h1>
<h2>Subtítulo</h2>
<h3>Título Menor 3</h3>
<h4>Título Menor 4</h4>
<h5>Título Menor 5</h3>
<h6>Título Menor 6</h3>
```

## Tags de Formatação Básica

### `<p>`
- **Função**: Define um parágrafo
- **Exemplo**:
```html
<p>Este é um parágrafo com texto...</p>
```

### `<span>`
- **Função**: Container inline para texto
- **Exemplo**:
```html
<p>Texto com <span class="destaque">palavra destacada</span></p>
```

### `<strong>`
- **Função**: Indica forte importância, texto com ênfase forte (substitui o antigo `<b>`)
- **Exemplo**:
```html
<p>Este é um <strong>aviso importante</strong> para todos.</p>
```

### `<em>`
- **Função**: Dá ênfase ao texto (substitui o antigo `<i>`)
- **Exemplo**:
```html
<p>Você <em>realmente</em> precisa ver isso.</p>
```

### `<mark>`
- **Função**: Destaca texto como se estivesse marcado com marca-texto
- **Exemplo**:
```html
<p>O <mark>prazo final</mark> é amanhã.</p>
```

### `<small>`
- **Função**: Representa comentários à parte, como texto legal ou notas de rodapé
- **Exemplo**:
```html
<p>Preço: R$99,90 <small>(frete não incluso)</small></p>
```

### `<del>`
- **Função**: Texto deletado/removido
- **Exemplo**:
```html
<p>Preço: <del>R$100,00</del> R$80,00</p>
```

### `<ins>`
- **Função**: Texto inserido/adicionado
- **Exemplo**:
```html
<p>O evento será em <del>março</del> <ins>abril</ins>.</p>
```

## Tags para Texto Técnico

### `<code>`
- **Função**: Representa código de computador
- **Exemplo**:
```html
<p>Use a função <code>console.log()</code> para debugar.</p>
```

### `<pre>`
- **Função**: Preserva formatação do texto (espaços e quebras de linha)
- **Exemplo**:
```html
<pre>
  function exemplo() {
    console.log("olá");
  }
</pre>
```

### `<kbd>`
- **Função**: Representa entrada do teclado
- **Exemplo**:
```html
<p>Pressione <kbd>Ctrl</kbd> + <kbd>C</kbd> para copiar.</p>
```

### `<samp>`
- **Função**: Representa saída de programa/script
- **Exemplo**:
```html
<p>Mensagem de erro: <samp>404 Not Found</samp></p>
```

### `<var>`
- **Função**: Representa uma variável matemática ou de programação
- **Exemplo**:
```html
<p>A equação é <var>x</var> = <var>y</var> + 2</p>
```

## Tags de Citação

### `<blockquote>`
- **Função**: Citação longa em bloco
- **Exemplo**:
```html
<blockquote cite="https://fonte.com">
  <p>Uma longa citação que ocupa várias linhas...</p>
</blockquote>
```

### `<q>`
- **Função**: Citação curta em linha
- **Exemplo**:
```html
<p>Como dizia minha avó: <q>Mais vale um pássaro na mão...</q></p>
```

### `<cite>`
- **Função**: Referência a um trabalho criativo
- **Exemplo**:
```html
<p><cite>Dom Casmurro</cite> foi escrito por Machado de Assis.</p>
```

## Tags de Definição

### `<dfn>`
- **Função**: Marca um termo sendo definido
- **Exemplo**:
```html
<p><dfn>HTML</dfn> é uma linguagem de marcação para criar páginas web.</p>
```

### `<abbr>`
- **Função**: Define uma abreviação
- **Exemplo**:
```html
<p><abbr title="World Wide Web">WWW</abbr> foi criada por Tim Berners-Lee.</p>
```

## Tags de Formatação Especial

### `<sub>`
- **Função**: Texto subscrito
- **Exemplo**:
```html
<p>H<sub>2</sub>O é a fórmula da água.</p>
```

### `<sup>`
- **Função**: Texto sobrescrito
- **Exemplo**:
```html
<p>2<sup>3</sup> é igual a 8.</p>
```

### `<bdi>` e `<bdo>`
- **Função**: Controle de direção do texto (útil para textos em árabe, hebraico, etc.)
- **Exemplo**:
```html
<p><bdo dir="rtl">Este texto está da direita para esquerda</bdo></p>
```

### `<wbr>`
- **Função**: Possível ponto de quebra de linha
- **Exemplo**:
```html
<p>www.exemplo<wbr>.com<wbr>/pagina<wbr>/muito<wbr>/longa</p>
```


# Tags de Listas

## 1. Lista Não Ordenada `<ul>`

### Básica
```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

### Com Classes e Estilos
```html
<ul class="menu-list">
    <li class="menu-item">Home</li>
    <li class="menu-item active">Produtos</li>
    <li class="menu-item disabled">Contato</li>
</ul>
```

### Aninhada
```html
<ul>
    <li>Frutas
        <ul>
            <li>Cítricas
                <ul>
                    <li>Laranja</li>
                    <li>Limão</li>
                </ul>
            </li>
            <li>Tropicais
                <ul>
                    <li>Manga</li>
                    <li>Banana</li>
                </ul>
            </li>
        </ul>
    </li>
</ul>
```

## 2. Lista Ordenada `<ol>`

### Básica
```html
<ol>
    <li>Primeiro passo</li>
    <li>Segundo passo</li>
    <li>Terceiro passo</li>
</ol>
```

### Com Atributos Específicos
```html
<!-- start: início da contagem -->
<!-- type: tipo de marcador -->
<!-- reversed: ordem reversa -->
<ol start="5" type="A" reversed>
    <li>Item E</li>
    <li>Item D</li>
    <li>Item C</li>
</ol>
```

### Tipos de Marcadores
```html
<!-- Números (padrão) -->
<ol type="1">
    <li>Item 1</li>
    <li>Item 2</li>
</ol>

<!-- Letras maiúsculas -->
<ol type="A">
    <li>Item A</li>
    <li>Item B</li>
</ol>

<!-- Letras minúsculas -->
<ol type="a">
    <li>Item a</li>
    <li>Item b</li>
</ol>

<!-- Números romanos maiúsculos -->
<ol type="I">
    <li>Item I</li>
    <li>Item II</li>
</ol>

<!-- Números romanos minúsculos -->
<ol type="i">
    <li>Item i</li>
    <li>Item ii</li>
</ol>
```

## 3. Lista de Definição `<dl>`

### Básica
```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language - linguagem para estruturar páginas web</dd>
    
    <dt>CSS</dt>
    <dd>Cascading Style Sheets - linguagem para estilizar páginas web</dd>
</dl>
```

### Múltiplas Definições
```html
<dl>
    <dt>Front-end</dt>
    <dd>Desenvolvimento da interface do usuário</dd>
    <dd>Parte visual e interativa de um site</dd>
    
    <dt>Back-end</dt>
    <dd>Desenvolvimento do servidor</dd>
    <dd>Processamento de dados e lógica de negócio</dd>
</dl>
```

## 4. Usos Práticos

### Menu de Navegação
```html
<nav>
    <ul class="nav-menu">
        <li><a href="/">Home</a></li>
        <li><a href="/produtos">Produtos</a>
            <ul class="submenu">
                <li><a href="/novo">Novos</a></li>
                <li><a href="/promocao">Promoções</a></li>
            </ul>
        </li>
        <li><a href="/contato">Contato</a></li>
    </ul>
</nav>
```

### Lista de Links Sociais
```html
<ul class="social-links">
    <li>
        <a href="https://facebook.com">
            <i class="fa fa-facebook"></i>
            <span>Facebook</span>
        </a>
    </li>
    <li>
        <a href="https://twitter.com">
            <i class="fa fa-twitter"></i>
            <span>Twitter</span>
        </a>
    </li>
</ul>
```

### Lista de Etapas/Processo
```html
<ol class="process-steps">
    <li class="completed">
        <span class="step">1</span>
        <span class="title">Carrinho</span>
    </li>
    <li class="active">
        <span class="step">2</span>
        <span class="title">Pagamento</span>
    </li>
    <li>
        <span class="step">3</span>
        <span class="title">Confirmação</span>
    </li>
</ol>
```

### Lista de FAQ
```html
<dl class="faq-list">
    <dt class="faq-question">Como faço para criar uma conta?</dt>
    <dd class="faq-answer">
        Para criar uma conta, clique no botão "Registrar" no topo da página...
    </dd>
    
    <dt class="faq-question">Qual o prazo de entrega?</dt>
    <dd class="faq-answer">
        O prazo de entrega varia de acordo com sua localização...
    </dd>
</dl>
```

## 5. Acessibilidade em Listas

```html
<!-- Lista de navegação com ARIA -->
<ul role="menubar" aria-label="Menu principal">
    <li role="menuitem" aria-current="page">Home</li>
    <li role="menuitem">
        Produtos
        <ul role="menu" aria-label="Submenu de produtos">
            <li role="menuitem">Item 1</li>
            <li role="menuitem">Item 2</li>
        </ul>
    </li>
</ul>

<!-- Lista de etapas com ARIA -->
<ol role="list" aria-label="Etapas do processo">
    <li aria-current="step">Etapa atual</li>
    <li>Próxima etapa</li>
</ol>
```


# Tags de Mídia

## 1. Tag `<img>` para Imagens

### Básica
```html
<img src="imagem.jpg" alt="Descrição da imagem">
```

### Com Atributos Completos
```html
<img 
    src="imagem.jpg"
    alt="Descrição detalhada da imagem"
    width="800"
    height="600"
    loading="lazy"
    decoding="async"
    class="imagem-responsiva"
>
```

### Com Picture para Responsividade
```html
<picture>
    <!-- Ordem: mobile primeiro -->
    <source 
        media="(max-width: 768px)" 
        srcset="imagem-mobile.jpg"
    >
    <source 
        media="(max-width: 1200px)" 
        srcset="imagem-tablet.jpg"
    >
    <source 
        media="(min-width: 1201px)" 
        srcset="imagem-desktop.jpg"
    >
    <!-- Fallback para navegadores que não suportam picture -->
    <img src="imagem-fallback.jpg" alt="Descrição">
</picture>
```

### Com Srcset para Diferentes Resoluções
```html
<img 
    src="imagem-pequena.jpg"
    srcset="
        imagem-pequena.jpg 300w,
        imagem-media.jpg 600w,
        imagem-grande.jpg 900w
    "
    sizes="
        (max-width: 320px) 280px,
        (max-width: 640px) 580px,
        800px
    "
    alt="Imagem responsiva"
>
```

### Com Figure e Figcaption
```html
<figure>
    <img 
        src="grafico.jpg" 
        alt="Gráfico de vendas do último trimestre"
    >
    <figcaption>
        Vendas aumentaram 25% no último trimestre
    </figcaption>
</figure>
```

## 2. Tag `<video>` para Vídeos

### Básico
```html
<video src="video.mp4" controls></video>
```

### Com Múltiplas Fontes e Atributos
```html
<video 
    controls
    width="800"
    height="450"
    poster="thumbnail.jpg"
    preload="metadata"
    autoplay
    muted
    loop
    playsinline
>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <track 
        src="legendas-pt.vtt" 
        kind="subtitles" 
        srclang="pt" 
        label="Português"
    >
    <!-- Mensagem de fallback -->
    Seu navegador não suporta o elemento de vídeo.
</video>
```

### Com Picture-in-Picture
```html
<video 
    id="meu-video"
    controls
    pip="true"
    autopictureinpicture
>
    <source src="video.mp4" type="video/mp4">
</video>
```

## 3. Tag `<audio>` para Áudio

### Básico
```html
<audio src="audio.mp3" controls></audio>
```

### Com Múltiplas Fontes e Atributos
```html
<audio 
    controls
    preload="auto"
    loop
    muted
>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    <source src="audio.wav" type="audio/wav">
    <!-- Mensagem de fallback -->
    Seu navegador não suporta o elemento de áudio.
</audio>
```

## 4. Elementos de Faixa (Track)

### Para Vídeo com Múltiplas Legendas
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track 
        kind="subtitles" 
        src="legendas-pt.vtt" 
        srclang="pt" 
        label="Português" 
        default
    >
    <track 
        kind="subtitles" 
        src="legendas-en.vtt" 
        srclang="en" 
        label="English"
    >
    <track 
        kind="descriptions" 
        src="descricoes.vtt" 
        srclang="pt" 
        label="Descrições"
    >
    <track 
        kind="chapters" 
        src="capitulos.vtt" 
        srclang="pt" 
        label="Capítulos"
    >
</video>
```

## 5. Incorporação de Mídia Externa

### YouTube
```html
<iframe 
    width="560" 
    height="315" 
    src="https://www.youtube.com/embed/VIDEO_ID" 
    title="Título do vídeo do YouTube"
    frameborder="0" 
    allow="
        accelerometer; 
        autoplay; 
        clipboard-write; 
        encrypted-media; 
        gyroscope; 
        picture-in-picture
    " 
    allowfullscreen
></iframe>
```

### Vimeo
```html
<iframe 
    src="https://player.vimeo.com/video/VIDEO_ID" 
    width="640" 
    height="360" 
    frameborder="0" 
    allow="autoplay; fullscreen" 
    allowfullscreen
></iframe>
```

## 6. Boas Práticas

### Lazy Loading de Imagens
```html
<!-- Com atributo loading -->
<img 
    src="imagem.jpg" 
    loading="lazy" 
    alt="Imagem com lazy loading"
>

<!-- Com Intersection Observer (via data attribute) -->
<img 
    data-src="imagem.jpg" 
    class="lazy" 
    alt="Imagem para lazy loading via JS"
>
```

### Otimização de Imagens Responsivas
```html
<!-- Art Direction -->
<picture>
    <!-- Imagem para mobile em retrato -->
    <source 
        media="(max-width: 768px) and (orientation: portrait)"
        srcset="mobile-portrait.jpg"
    >
    
    <!-- Imagem para mobile em paisagem -->
    <source 
        media="(max-width: 768px) and (orientation: landscape)"
        srcset="mobile-landscape.jpg"
    >
    
    <!-- Imagem padrão -->
    <img src="default.jpg" alt="Imagem responsiva">
</picture>

<!-- Densidade de Pixels -->
<img 
    src="imagem.jpg"
    srcset="
        imagem.jpg 1x,
        imagem@2x.jpg 2x,
        imagem@3x.jpg 3x
    "
    alt="Imagem para diferentes densidades de pixel"
>
```

### Acessibilidade em Mídia
```html
<!-- Vídeo com legendas e descrições -->
<video controls>
    <source src="video.mp4" type="video/mp4">
    
    <!-- Legendas -->
    <track 
        kind="subtitles" 
        src="legendas.vtt" 
        srclang="pt" 
        label="Legendas"
        default
    >
    
    <!-- Descrições de áudio -->
    <track 
        kind="descriptions" 
        src="descricoes.vtt" 
        srclang="pt" 
        label="Descrições de áudio"
    >
    
    <!-- Transcrição -->
    <a href="transcricao.html">
        Transcrição do vídeo
    </a>
</video>
```

# Tag DIV

## O que é a `<div>`
A `<div>` (division) é uma tag de contêiner genérica que serve para agrupar outros elementos HTML. Ela não tem significado semântico próprio - é usada puramente para fins de layout e organização do conteúdo.

## Quando Usar
```html
<!-- ✅ USAR quando precisar: -->

<!-- 1. Criar layouts e grids -->
<div class="grid">
    <div class="grid-item">Item 1</div>
    <div class="grid-item">Item 2</div>
</div>

<!-- 2. Agrupar elementos relacionados -->
<div class="product-card">
    <img src="product.jpg" alt="Produto">
    <h3>Nome do Produto</h3>
    <p>Descrição</p>
    <button>Comprar</button>
</div>

<!-- 3. Criar contêineres para estilização -->
<div class="background-blue padding-20">
    <p>Conteúdo com fundo azul e padding</p>
</div>

<!-- 4. Wrappers para JavaScript -->
<div id="app" data-component="slider">
    <!-- Conteúdo manipulado por JS -->
</div>
```

## Quando NÃO Usar
```html
<!-- ❌ NÃO USAR quando existir uma tag semântica apropriada -->

<!-- Ruim: -->
<div class="article">
    <div class="title">Título</div>
    <div class="content">Conteúdo</div>
</div>

<!-- Bom: -->
<article>
    <h1>Título</h1>
    <p>Conteúdo</p>
</article>

<!-- Ruim: -->
<div class="navigation">
    <div class="nav-item">Home</div>
</div>

<!-- Bom: -->
<nav>
    <a href="/">Home</a>
</nav>
```

## Padrões de Uso Comuns

### 1. Layout Grid
```html
<div class="grid-container">
    <div class="grid-row">
        <div class="grid-col">Coluna 1</div>
        <div class="grid-col">Coluna 2</div>
        <div class="grid-col">Coluna 3</div>
    </div>
</div>
```

### 2. Cartões de Conteúdo
```html
<div class="card">
    <div class="card-header">
        <h3>Título do Cartão</h3>
    </div>
    <div class="card-body">
        <p>Conteúdo do cartão</p>
    </div>
    <div class="card-footer">
        <button>Ação</button>
    </div>
</div>
```

### 3. Wrappers de Layout
```html
<div class="page-wrapper">
    <div class="content-wrapper">
        <div class="main-content">
            <!-- Conteúdo principal -->
        </div>
        <div class="sidebar">
            <!-- Barra lateral -->
        </div>
    </div>
</div>
```

### 4. Componentes de Interface
```html
<div class="modal" role="dialog">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Título do Modal</h2>
            <button class="close">&times;</button>
        </div>
        <div class="modal-body">
            <!-- Conteúdo do modal -->
        </div>
    </div>
</div>
```

## Boas Práticas

### 1. Nomeação de Classes
```html
<!-- Use classes descritivas e significativas -->
<div class="product-list">
    <div class="product-card">
        <div class="product-image">
            <img src="product.jpg" alt="Produto">
        </div>
        <div class="product-info">
            <div class="product-title">Nome</div>
            <div class="product-price">R$ 99,90</div>
        </div>
    </div>
</div>
```

### 2. Estrutura e Aninhamento
```html
<!-- Mantenha uma estrutura clara e organizada -->
<div class="page-section">
    <div class="container">
        <div class="row">
            <div class="col">
                <!-- Evite aninhar muitas divs sem necessidade -->
                <div class="content">
                    <!-- Conteúdo -->
                </div>
            </div>
        </div>
    </div>
</div>
```

### 3. Acessibilidade
```html
<!-- Adicione atributos ARIA quando necessário -->
<div 
    role="tabpanel" 
    aria-labelledby="tab-1"
    class="tab-content"
>
    <!-- Conteúdo da aba -->
</div>

<!-- Use data-attributes para JavaScript -->
<div 
    class="accordion"
    data-component="accordion"
    data-active="false"
>
    <!-- Conteúdo do acordeão -->
</div>
```

## Exemplos de Uso com Frameworks

### 1. Bootstrap
```html
<div class="container">
    <div class="row">
        <div class="col-md-6">
            <div class="card">
                <!-- Conteúdo -->
            </div>
        </div>
    </div>
</div>
```

### 2. Tailwind CSS
```html
<div class="flex flex-col md:flex-row">
    <div class="w-full md:w-1/2 p-4">
        <div class="bg-white rounded-lg shadow-md">
            <!-- Conteúdo -->
        </div>
    </div>
</div>
```

## Dicas de Performance

```html
<!-- Use data-attributes para seletores de JavaScript -->
<div 
    data-component="slider"
    data-options='{"autoplay": true, "speed": 500}'
>
    <!-- Conteúdo -->
</div>

<!-- Evite divs desnecessárias -->
<!-- Ruim -->
<div class="wrapper">
    <div class="container">
        <div class="content">
            <p>Texto</p>
        </div>
    </div>
</div>

<!-- Bom -->
<div class="container">
    <p>Texto</p>
</div>
```


# Tags Semânticas

## O que são Tags Semânticas?
Tags semânticas são elementos HTML que carregam significado sobre seu conteúdo, ajudando tanto desenvolvedores quanto navegadores a entenderem a estrutura e a importância do conteúdo.

## Principais Tags Semânticas

### 1. `<header>`
Define o cabeçalho da página ou de uma seção
```html
<header>
    <h1>Nome do Site</h1>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/sobre">Sobre</a></li>
        </ul>
    </nav>
</header>
```

### 2. `<nav>`
Define uma seção de navegação
```html
<nav>
    <!-- Menu principal -->
    <nav class="main-nav">
        <a href="/">Home</a>
        <a href="/produtos">Produtos</a>
        <a href="/contato">Contato</a>
    </nav>

    <!-- Breadcrumbs -->
    <nav aria-label="Breadcrumb">
        <ol>
            <li><a href="/">Home</a></li>
            <li><a href="/produtos">Produtos</a></li>
            <li aria-current="page">Produto Atual</li>
        </ol>
    </nav>
</nav>
```

### 3. `<main>`
Define o conteúdo principal da página
```html
<main>
    <h1>Título Principal</h1>
    <article>
        <!-- Conteúdo principal -->
    </article>
    <aside>
        <!-- Conteúdo relacionado -->
    </aside>
</main>
```

### 4. `<article>`
Define um conteúdo independente e autocontido
```html
<article>
    <header>
        <h2>Título do Artigo</h2>
        <time datetime="2024-11-05">5 de Novembro, 2024</time>
        <address>Por <a href="/autor">Nome do Autor</a></address>
    </header>

    <section>
        <!-- Conteúdo do artigo -->
    </section>

    <footer>
        <!-- Meta informações, tags, etc -->
    </footer>
</article>
```

### 5. `<section>`
Define uma seção temática do conteúdo
```html
<section>
    <h2>Produtos em Destaque</h2>
    <div class="products">
        <!-- Lista de produtos -->
    </div>
</section>

<section>
    <h2>Comentários</h2>
    <!-- Lista de comentários -->
</section>
```

### 6. `<aside>`
Define conteúdo relacionado mas separado do conteúdo principal
```html
<aside>
    <h3>Artigos Relacionados</h3>
    <ul>
        <li><a href="#">Outro artigo</a></li>
        <li><a href="#">Mais um artigo</a></li>
    </ul>

    <div class="widget">
        <!-- Widget de redes sociais -->
    </div>
</aside>
```

### 7. `<footer>`
Define o rodapé da página ou de uma seção
```html
<footer>
    <div class="footer-content">
        <section>
            <h4>Contato</h4>
            <address>
                <a href="mailto:email@exemplo.com">email@exemplo.com</a>
                <a href="tel:+5511999999999">+55 11 99999-9999</a>
            </address>
        </section>

        <nav>
            <h4>Links Úteis</h4>
            <ul>
                <li><a href="/privacidade">Política de Privacidade</a></li>
                <li><a href="/termos">Termos de Uso</a></li>
            </ul>
        </nav>
    </div>

    <div class="copyright">
        <small>&copy; 2024 Nome da Empresa</small>
    </div>
</footer>
```

### 8. `<figure>` e `<figcaption>`
Define uma ilustração, diagrama, foto, etc., com legenda
```html
<figure>
    <img src="grafico.jpg" alt="Gráfico de vendas">
    <figcaption>
        Gráfico demonstrando o aumento de vendas em 2024
    </figcaption>
</figure>
```

### 9. `<time>`
Define datas e horários
```html
<article>
    <h2>Título do Post</h2>
    <p>Publicado em <time datetime="2024-11-05T15:00:00">
        5 de Novembro às 15:00
    </time></p>
</article>
```

### 10. `<mark>`
Define texto destacado/marcado
```html
<p>
    O prazo final é <mark>amanhã às 18h</mark>. 
    Não se esqueça!
</p>
```

## Estrutura Semântica Completa

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Página Semântica</title>
</head>
<body>
    <!-- Cabeçalho do site -->
    <header>
        <h1>Nome do Site</h1>
        <nav>
            <!-- Menu principal -->
        </nav>
    </header>

    <!-- Conteúdo principal -->
    <main>
        <!-- Artigo principal -->
        <article>
            <header>
                <h2>Título do Artigo</h2>
                <time datetime="2024-11-05">5/11/2024</time>
            </header>

            <section>
                <h3>Primeira Seção</h3>
                <p>Conteúdo...</p>
            </section>

            <section>
                <h3>Segunda Seção</h3>
                <p>Mais conteúdo...</p>
            </section>

            <footer>
                <!-- Metadados do artigo -->
            </footer>
        </article>

        <!-- Barra lateral -->
        <aside>
            <section>
                <h3>Artigos Relacionados</h3>
                <!-- Links relacionados -->
            </section>
        </aside>
    </main>

    <!-- Rodapé do site -->
    <footer>
        <nav>
            <!-- Links do rodapé -->
        </nav>
        <small>&copy; 2024</small>
    </footer>
</body>
</html>
```

## Benefícios do HTML Semântico

1. **Acessibilidade**: Facilita a leitura por leitores de tela
2. **SEO**: Melhora o entendimento do conteúdo pelos buscadores
3. **Manutenibilidade**: Código mais organizado e fácil de entender
4. **Reutilização**: Estrutura clara para diferentes dispositivos
5. **Consistência**: Padrão de desenvolvimento mais claro

## Dicas de Uso

1. Use `<header>`, `<footer>` e `<nav>` tanto no nível da página quanto dentro de `<article>` e `<section>`
2. `<main>` deve aparecer apenas uma vez por página
3. `<article>` deve fazer sentido independentemente do contexto
4. Use `<section>` para agrupar conteúdo relacionado
5. Use `<aside>` para conteúdo complementar mas não essencial


# Formulários

## Estrutura Básica

### Formulário Simples
```html
<form action="/enviar" method="POST">
    <label for="nome">Nome:</label>
    <input type="text" id="nome" name="nome" required>
    
    <button type="submit">Enviar</button>
</form>
```

## Principais Atributos do `<form>`
```html
<form 
    action="/processar"           <!-- URL para envio dos dados -->
    method="POST"                 <!-- Método HTTP (GET ou POST) -->
    enctype="multipart/form-data" <!-- Para envio de arquivos -->
    autocomplete="on"             <!-- Habilita autocompletar -->
    novalidate                    <!-- Desabilita validação HTML5 -->
    target="_blank"               <!-- Onde abrir a resposta -->
>
```

## Tipos de Input

### Texto e Números
```html
<!-- Texto simples -->
<input type="text" name="nome" placeholder="Seu nome">

<!-- Email -->
<input type="email" name="email" required>

<!-- Senha -->
<input type="password" name="senha" minlength="8">

<!-- Número -->
<input type="number" name="idade" min="18" max="100">

<!-- Telefone -->
<input type="tel" name="telefone" pattern="[0-9]{11}">

<!-- URL -->
<input type="url" name="website">

<!-- Pesquisa -->
<input type="search" name="busca">
```

### Datas e Tempo
```html
<!-- Data -->
<input type="date" name="data">

<!-- Data e Hora -->
<input type="datetime-local" name="data_hora">

<!-- Mês -->
<input type="month" name="mes">

<!-- Semana -->
<input type="week" name="semana">

<!-- Hora -->
<input type="time" name="hora">
```

### Seleção
```html
<!-- Checkbox -->
<input type="checkbox" name="aceito" id="aceito">
<label for="aceito">Aceito os termos</label>

<!-- Radio -->
<input type="radio" name="genero" value="m" id="masculino">
<label for="masculino">Masculino</label>
<input type="radio" name="genero" value="f" id="feminino">
<label for="feminino">Feminino</label>

<!-- Select -->
<select name="estado">
    <option value="">Selecione...</option>
    <option value="SP">São Paulo</option>
    <option value="RJ">Rio de Janeiro</option>
</select>

<!-- Select Múltiplo -->
<select name="interesses" multiple>
    <optgroup label="Frontend">
        <option value="html">HTML</option>
        <option value="css">CSS</option>
        <option value="js">JavaScript</option>
    </optgroup>
    <optgroup label="Backend">
        <option value="python">Python</option>
        <option value="java">Java</option>
    </optgroup>
</select>
```

### Arquivos e Mídia
```html
<!-- Upload de arquivo -->
<input 
    type="file" 
    name="arquivo" 
    accept=".pdf,.doc,.docx"
    multiple
>

<!-- Upload de imagem -->
<input 
    type="file" 
    name="foto" 
    accept="image/*"
    capture="user"
>

<!-- Cor -->
<input type="color" name="cor">

<!-- Range -->
<input 
    type="range" 
    name="volume" 
    min="0" 
    max="100" 
    step="5"
>
```

## Elementos de Texto Longo
```html
<!-- Área de texto -->
<textarea 
    name="mensagem" 
    rows="4" 
    cols="50"
    maxlength="500"
    placeholder="Digite sua mensagem..."
></textarea>

<!-- Editor rico -->
<div contenteditable="true" class="editor">
    Conteúdo editável
</div>
```

## Agrupamento e Layout
```html
<!-- Fieldset para agrupar campos relacionados -->
<fieldset>
    <legend>Dados Pessoais</legend>
    
    <div class="form-group">
        <label for="nome">Nome:</label>
        <input type="text" id="nome" name="nome">
    </div>
    
    <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" name="email">
    </div>
</fieldset>
```

## Validação e Atributos de Controle

### Validação Nativa
```html
<!-- Campos obrigatórios -->
<input type="text" required>

<!-- Padrões (Regex) -->
<input 
    type="text" 
    pattern="[A-Za-z]{3,}" 
    title="Mínimo de 3 letras"
>

<!-- Comprimento -->
<input type="text" minlength="3" maxlength="50">

<!-- Números -->
<input type="number" min="0" max="100" step="5">
```

### Atributos de Controle
```html
<!-- Autocompletar -->
<input type="text" autocomplete="name">

<!-- Autofoco -->
<input type="text" autofocus>

<!-- Somente leitura -->
<input type="text" readonly value="Não editável">

<!-- Desabilitado -->
<input type="text" disabled>

<!-- Sugestões -->
<input list="browsers" name="browser">
<datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
</datalist>
```

## Formulário Completo com Boas Práticas
```html
<form 
    action="/enviar" 
    method="POST" 
    class="form"
    novalidate
>
    <!-- Cabeçalho do formulário -->
    <header class="form-header">
        <h2>Cadastro</h2>
        <p>Preencha seus dados</p>
    </header>

    <!-- Dados pessoais -->
    <fieldset>
        <legend>Dados Pessoais</legend>

        <div class="form-group">
            <label for="nome">Nome Completo:</label>
            <input 
                type="text" 
                id="nome" 
                name="nome"
                required
                minlength="3"
                autocomplete="name"
            >
            <small class="form-help">Digite seu nome completo</small>
        </div>

        <div class="form-group">
            <label for="email">Email:</label>
            <input 
                type="email" 
                id="email" 
                name="email"
                required
                autocomplete="email"
            >
        </div>
    </fieldset>

    <!-- Preferências -->
    <fieldset>
        <legend>Preferências</legend>

        <div class="form-group">
            <label>Interesses:</label>
            
            <div class="checkbox-group">
                <input 
                    type="checkbox" 
                    id="interesse1" 
                    name="interesses[]"
                    value="tecnologia"
                >
                <label for="interesse1">Tecnologia</label>
            </div>

            <div class="checkbox-group">
                <input 
                    type="checkbox" 
                    id="interesse2" 
                    name="interesses[]"
                    value="design"
                >
                <label for="interesse2">Design</label>
            </div>
        </div>
    </fieldset>

    <!-- Arquivo -->
    <fieldset>
        <legend>Documentos</legend>

        <div class="form-group">
            <label for="foto">Foto de Perfil:</label>
            <input 
                type="file" 
                id="foto" 
                name="foto"
                accept="image/*"
                required
            >
            <small class="form-help">
                Formatos aceitos: JPG, PNG. Máximo 5MB
            </small>
        </div>
    </fieldset>

    <!-- Botões -->
    <div class="form-actions">
        <button type="reset" class="btn-secondary">
            Limpar
        </button>
        <button type="submit" class="btn-primary">
            Enviar
        </button>
    </div>
</form>
```

## Acessibilidade em Formulários

```html
<!-- Labels e aria-labels -->
<label for="nome">Nome:</label>
<input 
    type="text" 
    id="nome"
    aria-required="true"
    aria-describedby="nome-help"
>
<small id="nome-help">Digite seu nome completo</small>

<!-- Grupos de campos -->
<fieldset>
    <legend class="sr-only">Opções de Contato</legend>
    <!-- campos -->
</fieldset>

<!-- Mensagens de erro -->
<input 
    type="email" 
    aria-invalid="true"
    aria-errormessage="email-error"
>
<span id="email-error" role="alert">
    Email inválido
</span>
```


# Guia de Acessibilidade

## 1. Estrutura Semântica Base

### Estrutura Básica Acessível
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Título Descritivo da Página</title>
</head>
<body>
    <a href="#main-content" class="skip-link">
        Pular para o conteúdo principal
    </a>

    <header role="banner">
        <nav role="navigation" aria-label="Menu principal">
            <!-- Navegação -->
        </nav>
    </header>

    <main id="main-content" role="main" tabindex="-1">
        <!-- Conteúdo principal -->
    </main>
</body>
</html>
```

## 2. WAI-ARIA Roles, Estados e Propriedades

### Roles (Papéis)
```html
<!-- Landmarks (Pontos de referência) -->
<header role="banner">
<nav role="navigation">
<main role="main">
<aside role="complementary">
<footer role="contentinfo">

<!-- Elementos Interativos -->
<div role="button">
<div role="tab">
<div role="tabpanel">
<div role="dialog">
<div role="alert">
```

### Estados e Propriedades
```html
<!-- Estados -->
<button aria-expanded="false">
<div aria-hidden="true">
<input aria-invalid="true">
<tab aria-selected="true">

<!-- Propriedades -->
<button aria-label="Fechar">
<input aria-describedby="help-text">
<div aria-labelledby="title">
```

## 3. Componentes Acessíveis

### Menu de Navegação
```html
<nav role="navigation" aria-label="Menu principal">
    <ul role="menubar">
        <li role="none">
            <a role="menuitem" href="/" aria-current="page">
                Home
            </a>
        </li>
        <li role="none">
            <button 
                role="menuitem" 
                aria-haspopup="true" 
                aria-expanded="false"
            >
                Produtos
            </button>
            <ul role="menu" aria-hidden="true">
                <li role="none">
                    <a role="menuitem" href="/produtos/novo">
                        Novos
                    </a>
                </li>
            </ul>
        </li>
    </ul>
</nav>
```

### Modal Dialog
```html
<div 
    role="dialog" 
    aria-labelledby="dialog-title" 
    aria-describedby="dialog-desc"
    aria-modal="true"
>
    <h2 id="dialog-title">Título do Modal</h2>
    <p id="dialog-desc">Descrição do modal</p>
    
    <button 
        onclick="closeDialog()" 
        aria-label="Fechar modal"
    >
        ×
    </button>
</div>
```

### Tabs
```html
<div class="tabs">
    <div role="tablist" aria-label="Seções de conteúdo">
        <button 
            role="tab" 
            aria-selected="true" 
            aria-controls="panel-1"
            id="tab-1"
        >
            Aba 1
        </button>
        <button 
            role="tab" 
            aria-selected="false" 
            aria-controls="panel-2"
            id="tab-2"
            tabindex="-1"
        >
            Aba 2
        </button>
    </div>

    <div 
        role="tabpanel" 
        id="panel-1" 
        aria-labelledby="tab-1"
    >
        Conteúdo da aba 1
    </div>
    <div 
        role="tabpanel" 
        id="panel-2" 
        aria-labelledby="tab-2"
        hidden
    >
        Conteúdo da aba 2
    </div>
</div>
```

## 4. Imagens e Mídia

### Imagens Acessíveis
```html
<!-- Imagem informativa -->
<img 
    src="grafico-vendas.jpg" 
    alt="Gráfico mostrando aumento de 50% nas vendas em 2024"
>

<!-- Imagem decorativa -->
<img src="decorativa.jpg" alt="" role="presentation">

<!-- Imagem com descrição longa -->
<figure>
    <img 
        src="infografico.jpg" 
        alt="Infográfico"
        aria-describedby="desc-infografico"
    >
    <figcaption id="desc-infografico">
        Descrição detalhada do infográfico...
    </figcaption>
</figure>
```

### Vídeos e Áudio
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track 
        kind="captions" 
        src="legendas.vtt" 
        srclang="pt-BR" 
        label="Português"
    >
    <track 
        kind="descriptions" 
        src="descricoes.vtt" 
        srclang="pt-BR" 
        label="Descrições de áudio"
    >
</video>
```

## 5. Formulários Acessíveis

### Campos de Formulário
```html
<form>
    <!-- Grupo de campos -->
    <fieldset>
        <legend>Dados Pessoais</legend>

        <!-- Campo com label -->
        <div class="form-group">
            <label for="nome">Nome:</label>
            <input 
                type="text" 
                id="nome"
                name="nome"
                required
                aria-required="true"
                aria-describedby="nome-help"
            >
            <small id="nome-help">
                Digite seu nome completo
            </small>
        </div>

        <!-- Campo com erro -->
        <div class="form-group">
            <label for="email">Email:</label>
            <input 
                type="email" 
                id="email"
                name="email"
                aria-invalid="true"
                aria-errormessage="email-error"
            >
            <span 
                id="email-error" 
                role="alert"
                class="error"
            >
                Email inválido
            </span>
        </div>
    </fieldset>
</form>
```

## 6. Notificações e Alertas

### Mensagens de Status
```html
<!-- Alerta -->
<div 
    role="alert" 
    aria-live="assertive"
>
    Erro ao salvar alterações
</div>

<!-- Status -->
<div 
    role="status" 
    aria-live="polite"
>
    Alterações salvas com sucesso
</div>

<!-- Progresso -->
<div 
    role="progressbar" 
    aria-valuenow="75" 
    aria-valuemin="0" 
    aria-valuemax="100"
>
    75% completo
</div>
```

## 7. Links e Botões

### Links Acessíveis
```html
<!-- Link com descrição clara -->
<a href="politica.html">
    Leia nossa política de privacidade
</a>

<!-- Link que abre em nova janela -->
<a 
    href="https://exemplo.com" 
    target="_blank"
    rel="noopener"
    aria-label="Visitar exemplo.com (abre em nova janela)"
>
    Visitar site
</a>
```

### Botões Acessíveis
```html
<!-- Botão com ícone -->
<button aria-label="Fechar">
    <i class="icon-close" aria-hidden="true"></i>
</button>

<!-- Botão toggle -->
<button 
    aria-pressed="false"
    aria-label="Ativar modo escuro"
>
    Modo Escuro
</button>
```

## 8. Boas Práticas

### Hierarquia de Cabeçalhos
```html
<main>
    <h1>Título Principal</h1>
    
    <section>
        <h2>Subtítulo</h2>
        <h3>Título menor</h3>
    </section>
</main>
```

### Skip Links
```html
<style>
.skip-link {
    position: absolute;
    top: -40px;
    left: 0;
    background: #000;
    color: white;
    padding: 8px;
    z-index: 100;
}

.skip-link:focus {
    top: 0;
}
</style>

<a href="#main-content" class="skip-link">
    Pular para o conteúdo principal
</a>
```

### Texto Escondido para Leitores de Tela
```html
<!-- Visualmente escondido mas disponível para leitores -->
<span class="sr-only">
    Informação adicional para leitores de tela
</span>

<style>
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0,0,0,0);
    border: 0;
}
</style>
```


# Links

## 1. Sintaxe Básica

### Link Simples
```html
<a href="pagina.html">Texto do Link</a>
```

### Atributos Essenciais
```html
<a 
    href="url-destino"          <!-- URL de destino -->
    target="_blank"             <!-- Onde abrir o link -->
    rel="noopener noreferrer"   <!-- Segurança para links externos -->
    title="Descrição do link"   <!-- Tooltip -->
>
    Texto do Link
</a>
```

## 2. Tipos de URLs

### Links Absolutos
```html
<!-- Links externos -->
<a href="https://www.exemplo.com">Site Externo</a>

<!-- Links com protocolo específico -->
<a href="https://exemplo.com">HTTPS</a>
<a href="http://exemplo.com">HTTP</a>
<a href="ftp://servidor.com">FTP</a>
```

### Links Relativos
```html
<!-- Mesmo diretório -->
<a href="pagina.html">Página</a>

<!-- Subdiretório -->
<a href="blog/post.html">Post</a>

<!-- Diretório anterior -->
<a href="../index.html">Voltar</a>

<!-- Raiz do site -->
<a href="/">Home</a>
```

### Links Internos (Âncoras)
```html
<!-- Link para ID na página -->
<a href="#secao1">Ir para Seção 1</a>

<!-- Seção alvo -->
<section id="secao1">
    Conteúdo da Seção 1
</section>

<!-- Link para topo da página -->
<a href="#">Voltar ao topo</a>
```

## 3. Usos Especiais

### Links de Email
```html
<!-- Email simples -->
<a href="mailto:email@exemplo.com">
    Enviar email
</a>

<!-- Email com campos preenchidos -->
<a href="mailto:email@exemplo.com?subject=Assunto&body=Corpo do email">
    Enviar email personalizado
</a>
```

### Links de Telefone
```html
<!-- Telefone -->
<a href="tel:+5511999999999">
    (11) 99999-9999
</a>

<!-- WhatsApp -->
<a href="https://wa.me/5511999999999">
    WhatsApp
</a>
```

### Links para Download
```html
<!-- Download simples -->
<a href="arquivo.pdf" download>
    Baixar PDF
</a>

<!-- Download com nome personalizado -->
<a href="arquivo.pdf" download="novo-nome.pdf">
    Baixar PDF
</a>
```

## 4. Estilos de Link

### Estados dos Links
```html
<style>
/* Link não visitado */
a:link {
    color: blue;
}

/* Link visitado */
a:visited {
    color: purple;
}

/* Mouse sobre o link */
a:hover {
    color: red;
}

/* Link ativo (durante o clique) */
a:active {
    color: orange;
}
</style>
```

### Links com Ícones
```html
<!-- Link com ícone -->
<a href="documento.pdf" class="pdf-link">
    <img src="pdf-icon.svg" alt="">
    Baixar documento
</a>

<!-- Link com ícone de fonte -->
<a href="https://twitter.com" class="social-link">
    <i class="fa fa-twitter" aria-hidden="true"></i>
    <span>Twitter</span>
</a>
```

## 5. Acessibilidade em Links

### Links Acessíveis
```html
<!-- Link descritivo -->
<a href="politica.html">
    Leia nossa política de privacidade
</a>

<!-- Link com descrição adicional -->
<a href="download.zip" aria-label="Baixar arquivos do projeto (10MB)">
    Baixar arquivos
</a>

<!-- Link externo com aviso -->
<a 
    href="https://exemplo.com" 
    target="_blank"
    rel="noopener noreferrer"
    aria-label="Visitar exemplo.com (abre em nova janela)"
>
    Visitar site externo
</a>
```

## 6. Padrões Comuns

### Menu de Navegação
```html
<nav>
    <ul class="nav-menu">
        <li>
            <a href="/" aria-current="page">Home</a>
        </li>
        <li>
            <a href="/produtos">Produtos</a>
        </li>
        <li>
            <a href="/contato">Contato</a>
        </li>
    </ul>
</nav>
```

### Links de Cartão
```html
<article class="card">
    <a href="/post" class="card-link">
        <h2>Título do Post</h2>
        <img src="imagem.jpg" alt="Descrição">
        <p>Resumo do post...</p>
    </a>
</article>
```

### Breadcrumbs
```html
<nav aria-label="Breadcrumb">
    <ol class="breadcrumb">
        <li>
            <a href="/">Home</a>
        </li>
        <li>
            <a href="/produtos">Produtos</a>
        </li>
        <li aria-current="page">
            Produto Atual
        </li>
    </ol>
</nav>
```

## 7. Boas Práticas

### Segurança
```html
<!-- Links externos -->
<a 
    href="https://exemplo.com" 
    target="_blank" 
    rel="noopener noreferrer"
>
    Site Externo
</a>

<!-- Links para downloads -->
<a 
    href="arquivo.pdf" 
    download 
    type="application/pdf"
>
    Baixar PDF
</a>
```

### Performance
```html
<!-- Preload de páginas -->
<a 
    href="proxima-pagina.html" 
    rel="prerender"
>
    Próxima Página
</a>

<!-- Prefetch de recursos -->
<a 
    href="pagina.html" 
    rel="prefetch"
>
    Carregar Antecipadamente
</a>
```

### SEO
```html
<!-- Links internos -->
<a href="/pagina" rel="canonical">
    Página Principal
</a>

<!-- Links para outros idiomas -->
<a href="/en" hreflang="en" rel="alternate">
    English Version
</a>
```

## 8. Exemplos Práticos

### Link de Compartilhamento
```html
<!-- Compartilhar no Twitter -->
<a 
    href="https://twitter.com/share?url=https://meusite.com&text=Texto"
    target="_blank"
    rel="noopener noreferrer"
    aria-label="Compartilhar no Twitter"
>
    <i class="fa fa-twitter" aria-hidden="true"></i>
    Compartilhar
</a>
```

### Link de Ação
```html
<!-- Link que parece botão -->
<a 
    href="/comprar"
    class="button"
    role="button"
>
    Comprar Agora
</a>
```

### Link com Preview
```html
<a 
    href="/artigo"
    class="preview-link"
    data-preview="Prévia do conteúdo..."
>
    Ler Artigo
    <span class="preview-tooltip">
        Prévia do conteúdo...
    </span>
</a>
```
