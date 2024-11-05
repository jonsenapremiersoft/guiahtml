# Guia HTML

# Sumário

[1. Tags Estruturais](#tags-estruturais)   
[2. Tags de Texto Essenciais](#tags-de-texto-essenciais)   
[3. Tags de Listas](#tags-de-listas)   
[4. Tags de Mídia](#tags-de-mídia)   


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
