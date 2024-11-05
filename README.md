# Guia HTML

# Sumário

[1. Tags Estruturais](#tags-estruturais)   
[2. Tags de Texto Essenciais](#tags-de-texto-essenciais)

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

## Tags de Formatação Básica

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



