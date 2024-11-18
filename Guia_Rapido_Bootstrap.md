# Introdução ao Bootstrap

## O que é Bootstrap?
O Bootstrap é um framework front-end gratuito e de código aberto criado pelo Twitter. Ele fornece componentes prontos e um sistema de grid que facilitam a criação de sites responsivos e modernos.

## Instalação
Existem duas maneiras principais de incluir o Bootstrap em seu projeto:

### 1. Via CDN
Adicione os seguintes links no seu arquivo HTML:

```html
<!-- CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- JavaScript (opcional, mas necessário para alguns componentes) -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
```

### 2. Via Download
Baixe os arquivos do [site oficial do Bootstrap](https://getbootstrap.com/docs/5.3/getting-started/download/) e inclua-os em seu projeto.

## Sistema de Grid

O Bootstrap utiliza um sistema de grid baseado em 12 colunas. Este sistema é fundamental para criar layouts responsivos.

### Classes Principais:
- `.container` ou `.container-fluid`
- `.row`
- `.col-*`

### Exemplo Básico:
```html
<div class="container">
  <div class="row">
    <div class="col-12 col-md-6 col-lg-4">Coluna 1</div>
    <div class="col-12 col-md-6 col-lg-4">Coluna 2</div>
    <div class="col-12 col-md-12 col-lg-4">Coluna 3</div>
  </div>
</div>
```

### Breakpoints de Responsividade:
- `sm`: ≥576px
- `md`: ≥768px
- `lg`: ≥992px
- `xl`: ≥1200px
- `xxl`: ≥1400px

## Sistema de Spacing

O Bootstrap oferece classes utilitárias para margin e padding.

### Formato:
{propriedade}{lados}-{breakpoint}-{tamanho}

### Propriedades:
- `m`: margin
- `p`: padding

### Lados:
- `t`: top
- `b`: bottom
- `s`: start (esquerda)
- `e`: end (direita)
- `x`: eixo horizontal
- `y`: eixo vertical

### Tamanhos:
- `0`: 0
- `1`: 0.25rem
- `2`: 0.5rem
- `3`: 1rem
- `4`: 1.5rem
- `5`: 3rem
- `auto`: automático

### Exemplo:
```html
<div class="mt-3 mt-md-5">Margin top 1rem em telas pequenas, 3rem em md ou maior</div>
<div class="px-2 px-lg-4">Padding horizontal 0.5rem, 1.5rem em lg ou maior</div>
```

# Projeto Prático: Landing Page Responsiva

Vamos criar uma landing page simples usando os conceitos aprendidos.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Landing Page</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .hero-section {
            background-color: #f8f9fa;
            min-height: 400px;
        }
        .feature-card {
            transition: transform 0.3s;
        }
        .feature-card:hover {
            transform: translateY(-5px);
        }
    </style>
</head>
<body>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
            <a class="navbar-brand" href="#">MeuSite</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#">Início</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Sobre</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Contato</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero-section d-flex align-items-center">
        <div class="container">
            <div class="row align-items-center">
                <div class="col-12 col-md-6">
                    <h1 class="display-4 mb-3">Bem-vindo ao MeuSite</h1>
                    <p class="lead mb-4">Uma landing page moderna e responsiva criada com Bootstrap.</p>
                    <button class="btn btn-primary btn-lg">Saiba Mais</button>
                </div>
                <div class="col-12 col-md-6 mt-4 mt-md-0">
                    <img src="https://via.placeholder.com/600x400" alt="Hero Image" class="img-fluid">
                </div>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section class="py-5">
        <div class="container">
            <h2 class="text-center mb-5">Nossos Recursos</h2>
            <div class="row g-4">
                <!-- Feature 1 -->
                <div class="col-12 col-md-6 col-lg-4">
                    <div class="card feature-card h-100">
                        <div class="card-body text-center p-4">
                            <h3 class="h5 mb-3">Recurso 1</h3>
                            <p class="mb-0">Descrição do recurso 1 aqui.</p>
                        </div>
                    </div>
                </div>
                <!-- Feature 2 -->
                <div class="col-12 col-md-6 col-lg-4">
                    <div class="card feature-card h-100">
                        <div class="card-body text-center p-4">
                            <h3 class="h5 mb-3">Recurso 2</h3>
                            <p class="mb-0">Descrição do recurso 2 aqui.</p>
                        </div>
                    </div>
                </div>
                <!-- Feature 3 -->
                <div class="col-12 col-md-12 col-lg-4">
                    <div class="card feature-card h-100">
                        <div class="card-body text-center p-4">
                            <h3 class="h5 mb-3">Recurso 3</h3>
                            <p class="mb-0">Descrição do recurso 3 aqui.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

## Sugestões de Melhorias para Praticar:

1. Adicione uma seção de depoimentos usando o componente carousel do Bootstrap
2. Implemente um formulário de contato responsivo usando as classes form-* do Bootstrap
3. Crie um footer com várias colunas que se reorganizam em diferentes breakpoints
4. Adicione um modal que abre quando o botão "Saiba Mais" é clicado
5. Implemente um menu dropdown na navbar
6. Adicione ícones usando Bootstrap Icons
7. Crie uma galeria de imagens usando o sistema de grid
8. Implemente um banner de cookies usando position-fixed e z-index

## Dicas Importantes:
- Sempre teste seu site em diferentes tamanhos de tela
- Use as ferramentas de desenvolvimento do navegador para entender como as classes do Bootstrap afetam seu layout
- Consulte a documentação oficial do Bootstrap para descobrir mais componentes e classes utilitárias
- Combine classes do Bootstrap para criar layouts mais complexos
- Customize as cores e estilos usando variáveis CSS do Bootstrap

## Exercício Final:
Tente recriar este layout e implementar pelo menos 3 das melhorias sugeridas acima. Isso ajudará você a fixar os conceitos aprendidos e explorar mais funcionalidades do Bootstrap.

Lembre-se: O Bootstrap é uma ferramenta poderosa, mas é importante entender os conceitos fundamentais de HTML e CSS para usá-lo de forma eficiente.
