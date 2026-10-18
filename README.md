# 🧁 Doce Sabor / Doce Luigi - Confeitaria & Doceria

Este repositório contém o código-fonte e o **Caderno de Pesquisa Técnica** para o desenvolvimento do website institucional e sistema de encomendas da confeitaria **Doce Sabor / Doce Luigi**.

---

## 📌 Sobre o Projeto

O projeto foi desenvolvido para atender às necessidades da confeitaria da Dona Márcia, estruturando um portal web moderno, acessível e responsivo com:
* Apresentação da marca e slogan.
* Destaques de produtos (Bolo do Mês).
* Cardápio completo de doces, bolos e salgados.
* Seção interativa de Perguntas Frequentes (FAQ).
* Mapa de localização e informações de contato direto.
* Formulário completo para envio de encomendas.

---

## 📁 Estrutura do Repositório

```
atividade-doce-luigi/
├── index.html     # Estrutura HTML5 semântica e acessível
├── estilo.css     # Estilização CSS3 com Grid, Variáveis e Animações
└── README.md      # Documentação e Caderno de Pesquisa Técnica
```

---

## 📖 Caderno de Pesquisa e Soluções Técnicas

### 🛠️ Etapa 1: Estrutura e Semântica

#### 1. Configuração Base do Documento (`head`)
O código inicial apresentava problemas de acentuação, idioma e responsividade. A estrutura corrigida e explicada é:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Doce Sabor</title>
    <link rel="stylesheet" href="estilo.css">
</head>
<body>
</body>
</html>
```

* **`lang="pt-BR"`:** Define o idioma do documento para o português do Brasil, garantindo que leitores de tela pronunciem o texto corretamente.
* **`<meta charset="UTF-8">`:** Define a codificação de caracteres como UTF-8, corrigindo acentuações e caracteres especiais.
* **`<meta name="viewport" content="width=device-width, initial-scale=1.0">`:** Ajusta a área de exibição proporcionalmente ao tamanho da tela do dispositivo (celular/tablet/desktop).
* **`<title>`:** Define o título que aparece na aba do navegador.
* **`<link rel="stylesheet" href="estilo.css">`:** Conecta o arquivo de estilização externa CSS ao HTML.

---

#### 2. Mapeamento Semântico do Wireframe

| Bloco | Conteúdo do Bloco | Tag Semântica Principal | Tags Internas Recomendadas |
| :--- | :--- | :--- | :--- |
| **A** | Logo e Slogan | `<header>` | `<h1>`, `<p>` |
| **B** | Bolo do Mês (Foto, descrição, validade) | `<article>` | `<h2>`, `<img>`, `<p>`, `<time>` |
| **C** | Cardápio (Cards de produtos) | `<section>` | `<h2>`, `<article>`, `<h3>`, `<p>`, `<span>` |
| **D** | Perguntas Frequentes (FAQ) | `<section>` | `<h2>`, `<details>`, `<summary>`, `<p>` |
| **E** | Rodapé (Copyright, e-mail, telefone) | `<footer>` | `<p>`, `<address>`, `<a>` |

* **Justificativa do uso de `<article>` (Bloco B):** Contém o "Bolo do Mês", um conteúdo autônomo e independente que faz sentido completo por si só (poderia ser compartilhado individualmente).
* **Justificativa do uso de `<section>` (Bloco C):** Agrupa uma coleção temática de elementos relacionados (o catálogo de produtos do cardápio).

---

#### 3. Correção de Má Prática Semântica

**Código Corrigido:**
```html
<body>
    <header>
        <h1>Doce Sabor</h1>
    </header>
    <main> 
        <article>
            <h2>Bolo do Mês</h2>
            <h3>Bolo de Pote de Ninho com Morango</h3>
            <p>Válido até 31 de outubro</p>
        </article>
    </main>
    <footer>
        <p>&copy; 2026 Doce Sabor</p>
    </footer>
</body>
```
* **Problemas identificados e corrigidos:**
  1. Uso excessivo de contêineres genéricos (`<div>`) substituídos por elementos semânticos (`<header>`, `<main>`, `<article>`, `<footer>`).
  2. Hierarquia de títulos desajustada (ajustada para a sequência lógica `<h1>`, `<h2>` e `<h3>`).
  3. Ausência da tag de conteúdo principal (`<main>`).

---

#### 4. Acessibilidade e Leitores de Tela
* **`<header>`, `<main>`, `<footer>` vs `<div>`:** Permitem que o leitor de tela identifique as regiões de navegação do site, permitindo que usuários cegos saltem diretamente para o conteúdo principal.
* **`<strong>` vs `<b>`:** A tag `<strong>` atribui importância semântica (o leitor de tela pode enfatizar a voz ao ler), enquanto `<b>` aplica apenas um destaque visual em negrito.
* **`<iframe>` com `title`:** O atributo `title` descreve o conteúdo da janela incorporada, permitindo que o usuário cego decida se deseja interagir com aquele quadro.

---

### 📬 Etapa 2: Interação, Mídia e Contato

#### 5. Seção de Perguntas Frequentes (`<details>` e `<summary>`)
```html
<section>
    <h2>Perguntas Frequentes</h2>
    <details>
        <summary>Vocês fazem entrega?</summary>
        <p>Sim, realizamos entregas em toda a região com taxa sob consulta.</p>
    </details>
    <details open>
        <summary>Aceitam Pix?</summary>
        <p>Sim, aceitamos Pix, cartões de débito/crédito e dinheiro.</p>
    </details>
</section>
```
* O atributo `open` na segunda tag `<details>` faz com que ela já inicie expandida ao carregar a página.

---

#### 6. Rodapé Acessível e Links Interativos
```html
<footer>
    <p>&copy; 2026 Doce Sabor. Todos os direitos reservados.</p>
    <address>
        E-mail: <a href="mailto:contato@docesabor.com">contato@docesabor.com</a><br>
        Telefone: <a href="tel:+551140001234">(11) 4000-1234</a>
    </address>
</footer>
```
* `&copy;`: Entidade HTML para exibir o símbolo de copyright (©).
* `mailto:`: Abre o cliente de e-mail padrão do usuário.
* `tel:`: Inicia uma chamada telefônica em dispositivos móveis.
* `<address>`: Tag semântica para agrupar informações de contato.

---

#### 7. Incorporação de Mapa via `<iframe>`
```html
<iframe
    src="https://www.google.com/maps/embed?pb=..."
    width="600"
    height="450"
    title="Mapa de localização da confeitaria Doce Sabor"
    style="border:0;"
    allowfullscreen=""
    loading="lazy">
</iframe>
```
* **`src`:** URL da fonte do mapa do Google Maps.
* **`width` / `height`:** Largura e altura de exibição do quadro em pixels.
* **`title`:** Descrição textual do iframe para recursos de acessibilidade.

---

### 📝 Etapa 3: Formulário de Encomendas

#### 8. Código do Formulário Completo
```html
<form action="/encomendas" method="post">
    <label for="nome">Nome Completo:</label>
    <input type="text" id="nome" name="nome" required>

    <label for="email">E-mail:</label>
    <input type="email" id="email" name="email" required>

    <label for="sabor">Sabor do Bolo:</label>
    <select id="sabor" name="sabor">
        <option value="chocolate">Bolo de Chocolate</option>
        <option value="morango">Bolo de Morango</option>
        <option value="ninho">Bolo de Ninho com Morango</option>
    </select>

    <label for="data">Data de Retirada/Entrega:</label>
    <input type="date" id="data" name="data" required>

    <fieldset>
        <legend>Forma de Recebimento:</legend>
        <input type="radio" id="loja" name="recebimento" value="loja" checked>
        <label for="loja">Retirar na Loja</label>

        <input type="radio" id="entrega" name="recebimento" value="entrega">
        <label for="entrega">Entrega a Domicílio</label>
    </fieldset>

    <button type="submit">Fazer pedido</button>
</form>
```

---

#### 9. Análise do Formulário
* **Envio do Servidor:** Ao escolher "Bolo de Morango" (`<option value="morango">`), o servidor recebe o par chave-valor `sabor=morango`.
* **Erro no `<label for="...">`:** Se o atributo `for` do `<label>` for diferente do `id` do elemento de entrada (ex: `for="sabores"` e `id="sabor"`), a associação falha. Isso impede que o leitor de tela leia o rótulo correto ao focar no campo e desabilita a função de clicar no texto do rótulo para ativar o campo.

---

### 🎨 Etapa 4: Estilização CSS

#### 10. Variáveis CSS e Identidade Visual
```css
:root {
    --rosa: #f2a7bb;
    --marrom: #6b3e2e;
    --creme: #fff1dc;
}

body {
    background-color: var(--creme);
    color: var(--marrom);
}
```
* **Vantagem das Variáveis:** Permitem alterar o esquema de cores globalmente modificando apenas o valor da variável no bloco `:root`.

---

#### 11. Layout Responsivo com CSS Grid
```css
.cardapio {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 16px;
}

.destaque {
    grid-column: 1 / -1;
}

@media (max-width: 768px) {
    .cardapio {
        grid-template-columns: 1fr;
    }
}
```
* **Computador:** Exibe **3 colunas** de larguras iguais.
* **Celular (400px):** Exibe **1 coluna**, devido à regra `@media (max-width: 768px)`.
* **`1fr`:** Unidade de fração flexível do espaço disponível no contêiner.
* **`gap`:** Espaçamento entre as linhas e colunas do Grid.
* **`grid-column: 1 / -1`:** Faz o elemento ocupar da primeira até a última coluna da grade.

---

#### 12. Efeitos Visuais (Sticky, Glassmorphism e Hover)
```css
header {
    position: sticky;
    top: 0;
    background: rgba(255, 241, 220, 0.7);
    backdrop-filter: blur(10px);
    z-index: 1000;
}

.btn-pedido {
    background-color: var(--rosa);
    color: var(--marrom);
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
    transition: transform 0.3s ease;
}

.btn-pedido:hover {
    transform: scale(1.05);
}
```
* **`position: sticky` + `top: 0`:** Mantém o cabeçalho fixo no topo da tela conforme o usuário rola a página.
* **`backdrop-filter: blur(10px)`:** Aplica o efeito de vidro fosco (glassmorphism) sobre o fundo semi-transparente.
* **`transform: scale(1.05)` + `transition`:** Aplica um efeito suave de ampliação no botão ao passar o ponteiro do mouse.

---

## 📚 Fontes Consultadas

1. **MDN Web Docs:** Documentação oficial de HTML e CSS (`developer.mozilla.org`)
2. **W3Schools:** Tutoriais e guias de referência para tags e seletores (`w3schools.com`)
3. **W3C Markup Validation Service:** Validador oficial de padrões semânticos (`validator.w3.org`)
4. **Modelos de Inteligência Artificial:** Suporte para consultas e validações estruturais (Gemini, Meta AI).

---

## ⚖️ Licença

Projeto desenvolvido para fins educacionais e avaliativos na disciplina de Linguagem de Marcação / Desenvolvimento Web Front-End.
