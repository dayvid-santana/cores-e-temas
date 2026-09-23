# Convenção de temas

Antes de criar ou alterar uma interface neste projeto, importe `themes.css` e aplique o tema na raiz da aplicação com `data-theme`. O valor padrão e fallback é `dark`.

Componentes devem usar apenas tokens semânticos de `themes.css` (por exemplo, `var(--color-surface)`, `var(--color-text)`, `var(--color-primary)` e `var(--color-border)`). Nunca introduza cores hexadecimais, `rgb()`, `hsl()` ou gradientes diretamente em componentes. Se um token estiver ausente, adicione-o a todos os temas antes de usá-lo.

Reutilize as classes `ui-*` existentes quando elas cobrirem a necessidade. Mantenha acessíveis os estados de hover, foco visível, desabilitado, erro e carregamento. Para acrescentar uma paleta, defina o mesmo conjunto completo de tokens de cor já presente em cada bloco de tema e preserve os nomes de tema existentes.
