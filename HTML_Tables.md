# HTML Tables

## 1. Introdução
As tabelas HTML são usadas para organizar dados em linhas e colunas, permitindo a apresentação estruturada de informações em páginas web.

## 2. Estrutura Básica
Uma tabela HTML é composta por três tags principais:
- `<table>`: Define a tabela
- `<tr>`: Define uma linha (table row)
- `<td>`: Define uma célula (table data)

### Exemplo Básico
```html
<table>
    <tr>
        <td>Célula 1</td>
        <td>Célula 2</td>
    </tr>
    <tr>
        <td>Célula 3</td>
        <td>Célula 4</td>
    </tr>
</table>
```

## 3. Elementos Semânticos
Para melhor estruturação e acessibilidade, use:
- `<thead>`: Cabeçalho da tabela
- `<tbody>`: Corpo da tabela
- `<tfoot>`: Rodapé da tabela
- `<th>`: Células de cabeçalho
- `<caption>`: Título da tabela

### Exemplo com Elementos Semânticos
```html
<table>
    <caption>Vendas por Região</caption>
    <thead>
        <tr>
            <th>Região</th>
            <th>Vendas</th>
            <th>Meta</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Norte</td>
            <td>R$ 50.000</td>
            <td>R$ 45.000</td>
        </tr>
        <tr>
            <td>Sul</td>
            <td>R$ 60.000</td>
            <td>R$ 55.000</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>R$ 110.000</td>
            <td>R$ 100.000</td>
        </tr>
    </tfoot>
</table>
```

## 4. Atributos Importantes

### colspan e rowspan
Permitem mesclar células horizontalmente e verticalmente:
```html
<table>
    <tr>
        <td colspan="2">Célula ocupando 2 colunas</td>
    </tr>
    <tr>
        <td>Célula normal</td>
        <td>Célula normal</td>
    </tr>
</table>
```

### Outros Atributos Úteis
- `border`: Define a borda da tabela
- `cellpadding`: Espaçamento interno das células
- `cellspacing`: Espaçamento entre células

## 5. Estilização com CSS
Recomenda-se usar CSS para estilização ao invés de atributos HTML:

```css
table {
    border-collapse: collapse;
    width: 100%;
    max-width: 800px;
    margin: 20px 0;
}

th, td {
    padding: 12px;
    text-align: left;
    border: 1px solid #ddd;
}

th {
    background-color: #f4f4f4;
    font-weight: bold;
}

tr:nth-child(even) {
    background-color: #f9f9f9;
}

tr:hover {
    background-color: #f5f5f5;
}
```

## 6. Melhores Práticas

1. **Acessibilidade**
   - Use `<th>` para cabeçalhos de coluna/linha
   - Adicione `scope="col"` ou `scope="row"` aos elementos `<th>`
   - Utilize `<caption>` para descrever o conteúdo da tabela

2. **Responsividade**
```css
.table-container {
    overflow-x: auto;
    max-width: 100%;
}
```

3. **Semântica**
   - Use tabelas apenas para dados tabulares
   - Não use tabelas para layout
   - Organize o conteúdo logicamente com `thead`, `tbody` e `tfoot`

## 7. Exemplo Prático Completo

```html
<div class="table-container">
    <table>
        <caption>Relatório de Vendas 2024</caption>
        <thead>
            <tr>
                <th scope="col">Produto</th>
                <th scope="col">Janeiro</th>
                <th scope="col">Fevereiro</th>
                <th scope="col">Março</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <th scope="row">Notebook</th>
                <td>150</td>
                <td>180</td>
                <td>200</td>
            </tr>
            <tr>
                <th scope="row">Smartphone</th>
                <td>300</td>
                <td>320</td>
                <td>350</td>
            </tr>
            <tr>
                <th scope="row">Tablet</th>
                <td>80</td>
                <td>95</td>
                <td>110</td>
            </tr>
        </tbody>
        <tfoot>
            <tr>
                <th scope="row">Total</th>
                <td>530</td>
                <td>595</td>
                <td>660</td>
            </tr>
        </tfoot>
    </table>
</div>
```

## 8. Considerações de Performance
- Evite tabelas muito grandes
- Use paginação para grandes conjuntos de dados
- Considere lazy loading para tabelas extensas
- Otimize a largura das colunas usando CSS

## 9. Recursos Adicionais
Para tabelas mais complexas, considere usar bibliotecas JavaScript como:
- DataTables
- AG Grid
- Tabulator

Estas bibliotecas oferecem recursos avançados como:
- Ordenação
- Filtros
- Paginação
- Exportação de dados
- Responsividade automática
