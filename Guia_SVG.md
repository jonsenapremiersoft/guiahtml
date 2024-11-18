# Introdução ao SVG (Scalable Vector Graphics)

## 1. O que é SVG?

SVG é um formato de imagem vetorial baseado em XML que permite criar gráficos escaláveis para a web. Diferente de formatos rasterizados como JPG ou PNG, imagens SVG mantêm sua qualidade independentemente do tamanho ou zoom aplicado.

### Principais características:
* Baseado em texto/XML
* Escalável sem perda de qualidade
* Editável com editores de texto
* Suporte nativo em navegadores modernos
* Pequeno tamanho de arquivo
* Acessível e pesquisável

## 2. Estrutura Básica

Um documento SVG começa com a tag `<svg>`:

```xml
<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
  <!-- Elementos SVG aqui -->
</svg>
```

## 3. Formas Básicas

### Retângulo
```xml
<rect x="10" y="10" width="90" height="60" fill="blue" />
```

### Círculo
```xml
<circle cx="50" cy="50" r="40" fill="red" />
```

### Linha
```xml
<line x1="10" y1="10" x2="90" y2="90" stroke="black" />
```

### Polígono
```xml
<polygon points="50,0 100,100 0,100" fill="green" />
```

## 4. Atributos Comuns

* `fill`: cor de preenchimento
* `stroke`: cor da borda
* `stroke-width`: espessura da borda
* `opacity`: transparência
* `transform`: transformações (rotação, escala, etc.)

## 5. Casos de Uso na Vida Real

### 1. Ícones e Logos
* Ícones de interface
* Logotipos empresariais
* Menus interativos

### 2. Infográficos
* Gráficos estatísticos
* Diagramas
* Mapas interativos

### 3. Animações
* Transições suaves
* Loading spinners
* Ilustrações interativas

### 4. Design Responsivo
* Elementos que se adaptam a diferentes telas
* Gráficos escaláveis
* Backgrounds adaptativos

### 5. Exemplo prático: ícone de usuário em SVG

```xml
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <!-- Círculo para cabeça -->
  <circle cx="50" cy="35" r="20" fill="#4A90E2"/>
  
  <!-- Corpo -->
  <path d="M20 85 Q50 95 80 85 L80 65 Q50 75 20 65 Z" fill="#4A90E2"/>
  
  <!-- Ombros -->
  <path d="M20 65 Q50 75 80 65 Q75 55 50 55 Q25 55 20 65" fill="#4A90E2"/>
</svg>
```

## 6. Boas Práticas

### 1. Otimização
* Remova metadados desnecessários
* Use ferramentas de otimização como SVGO
* Minimize pontos em paths complexos

### 2. Acessibilidade
* Adicione atributos `title` e `desc`
* Use `aria-label` quando necessário
* Mantenha IDs únicos

### 3. Organização
* Use grupos (`<g>`) para organizar elementos relacionados
* Nomeie elementos importantes
* Mantenha uma estrutura lógica

### 4. Performance
* Evite SVGs muito complexos
* Use `viewBox` em vez de width/height fixos
* Considere lazy loading para SVGs grandes

## 7. Exemplo de SVG Animado

```xml
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="45" fill="none" stroke="#e0e0e0" stroke-width="8"/>
  <circle cx="50" cy="50" r="45" fill="none" stroke="#2196F3" stroke-width="8" 
          stroke-linecap="round" stroke-dasharray="70 283">
    <animateTransform
      attributeName="transform"
      type="rotate"
      dur="1s"
      repeatCount="indefinite"
      from="0 50 50"
      to="360 50 50"/>
  </circle>
</svg>
```

## 8. Exercícios Práticos Sugeridos

1. Criar um ícone simples usando formas básicas
2. Implementar uma animação SVG
3. Otimizar um SVG existente
4. Criar um logo responsivo
5. Criar um gráfico simples

## 9. Ferramentas Recomendadas

### Editores
* Inkscape (gratuito)
* Adobe Illustrator
* Figma
* VSCode (para edição manual)

### Otimização
* SVGO
* SVGOMGs
* Clean Multiple SVG Files

### Bibliotecas JavaScript
* Snap.svg
* SVG.js
* GreenSock (GSAP)

## 10. Recursos Adicionais

### Sites de Referência
* [MDN Web Docs - SVG](https://developer.mozilla.org/pt-BR/docs/Web/SVG)
* [W3C SVG 2 Specification](https://www.w3.org/TR/SVG2/)
* [SVG na W3Schools](https://www.w3schools.com/graphics/svg_intro.asp)

### Tutoriais e Guias
* CSS-Tricks Guide to SVG
* Sara Soueidan's SVG Articles
* SVG on the Web (A Practical Guide)

## 11. Conclusão

SVG é uma tecnologia poderosa e versátil para criação de gráficos vetoriais na web. Com suporte amplo nos navegadores modernos e diversas ferramentas disponíveis, é uma escolha excelente para ícones, ilustrações e visualizações de dados interativas.
