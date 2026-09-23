# Themes CSS

Biblioteca CSS portátil para padronizar temas de interfaces. O tema padrão é escuro; sete temas estão prontos: `dark`, `rosa`, `azul`, `claro`, `terminal`, `roxo` e `vermelho`.

## Uso recomendado

Inclua `themes.css` uma única vez e altere o atributo no elemento que envolve toda a aplicação. As variáveis CSS são herdadas, por isso nenhum componente precisa saber qual tema está ativo.

```html
<html lang="pt-BR" data-theme="dark">
  <head>
    <link rel="stylesheet" href="/styles/themes.css">
  </head>
  <body class="ui-app">
    <main class="ui-card">
      <h1 class="ui-heading">Configurações</h1>
      <p class="ui-copy">Os componentes usam tokens semânticos.</p>
      <button class="ui-button ui-button--primary">Salvar</button>
    </main>
  </body>
</html>
```

Para trocar o tema no navegador:

```js
document.documentElement.dataset.theme = "roxo";
localStorage.setItem("theme", "roxo");
```

Para evitar a troca visual ao recarregar, restaure a preferência antes de a interface ser exibida:

```html
<script>
  document.documentElement.dataset.theme = localStorage.getItem("theme") || "dark";
</script>
```

Também há classes equivalentes, úteis quando apenas uma área da página deve receber um tema: `theme--rosa`, `theme--azul`, `theme--claro`, `theme--terminal`, `theme--roxo` e `theme--vermelho`.

```html
<section class="theme--terminal ui-app">
  <div class="ui-card">Este trecho usa o tema terminal.</div>
</section>
```

## Contrato para componentes e LLMs

Ao criar ou editar componentes, use sempre tokens semânticos — por exemplo `var(--color-surface)`, `var(--color-text)`, `var(--color-primary)` e `var(--color-border)`. Não use valores hexadecimais, `rgb()` ou nomes de cor diretamente no CSS do componente. Isso é o que faz a mudança de tema alcançar toda a interface.

Use as classes prontas quando fizer sentido:

| Necessidade | Classe |
| --- | --- |
| Raiz da aplicação | `ui-app` |
| Superfície | `ui-surface` |
| Bloco elevado | `ui-card` |
| Título | `ui-heading` |
| Texto auxiliar | `ui-copy` ou `ui-text-muted` |
| Botão | `ui-button`, com `ui-button--primary` ou `ui-button--danger` |
| Campo | `ui-field` envolvendo `ui-input`, `ui-select` ou `ui-textarea` |
| Estado | `ui-badge ui-badge--success` (ou `warning`, `danger`, `info`) |
| Mensagem | `ui-alert ui-alert--success` (ou `warning`, `danger`, `info`) |
| Tabela | `ui-table` |
| Código | `ui-code` |

Os nomes de tema devem permanecer estáveis. Para adicionar outro, copie um bloco de tema em `themes.css`, defina todos os tokens `--color-*` e registre o novo valor nesta lista. Não é preciso mudar os componentes.

## Decisões de base

- `dark` é aplicado por padrão sem JavaScript.
- O atributo `data-theme` é o mecanismo principal; as classes `theme--*` existem como compatibilidade e para áreas isoladas.
- Cada paleta tem tokens para fundo, superfícies, texto, bordas, ação, foco e estados. Isso evita que um tema seja apenas uma troca decorativa de fundo.
- `color-scheme` acompanha cada tema, para que controles nativos também se adaptem.
- Foco de teclado, seleção, cursor e barras de rolagem foram tematizados; transições respeitam `prefers-reduced-motion`.
