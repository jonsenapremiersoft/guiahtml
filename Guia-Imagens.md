# Guia de Imagens para Desenvolvimento Web

## Formatos Principais

### JPEG/JPG
- Ideal para fotografias e imagens com muitas cores
- Compressão com perdas mas tamanhos menores
- Não suporta transparência
- Melhor uso: fotos, banners, imagens de fundo complexas

### PNG
- Compressão sem perdas
- Suporta transparência
- Dois tipos:
  - PNG-8: 256 cores, ideal para ícones simples
  - PNG-24: milhões de cores, maior qualidade
- Melhor uso: logos, ícones, imagens com texto

### SVG
- Gráficos vetoriais escaláveis
- Baseado em XML
- Perfeito para responsividade
- Tamanho de arquivo pequeno para imagens simples
- Melhor uso: logos, ícones, ilustrações simples

### WebP
- Formato moderno da Google
- Suporta compressão com e sem perdas
- Oferece transparência
- Melhor compressão que JPEG e PNG
- Melhor uso: substituir JPG/PNG quando houver suporte

## Boas Práticas

### Otimização
1. Escolha o formato apropriado para cada caso
2. Comprima imagens antes de usar
3. Use ferramentas de otimização automática
4. Forneça diferentes tamanhos para diferentes dispositivos

### Responsividade
```html
<!-- Imagem responsiva básica -->
<img srcset="small.jpg 300w,
             medium.jpg 600w,
             large.jpg 900w"
     sizes="(max-width: 320px) 280px,
            (max-width: 640px) 580px,
            900px"
     src="fallback.jpg"
     alt="Descrição da imagem">

<!-- Picture para art direction -->
<picture>
  <source media="(min-width: 800px)" srcset="hero.jpg">
  <source media="(min-width: 400px)" srcset="hero-middle.jpg">
  <img src="hero-small.jpg" alt="Herói">
</picture>
```

### Performance
1. Lazy loading para imagens abaixo da dobra
```html
<img loading="lazy" src="imagem.jpg" alt="Descrição">
```

2. Use CDN para distribuição global
3. Implemente cache adequado
4. Considere blur/placeholder para carregamento progressivo

### Acessibilidade
1. Sempre use alt text descritivo
2. Evite texto em imagens
3. Mantenha contraste adequado
4. Use ARIA labels quando necessário

## Ferramentas Recomendadas
- Compressão: ImageOptim, TinyPNG
- Conversão: Squoosh
- CDN: Cloudinary, imgix
- Otimização automatizada: Next.js Image, Gatsby Image
