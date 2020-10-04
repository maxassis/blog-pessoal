---
date: 2020-10-03 21:11:23
title: Styled-Components — instalação e configuração básica
description: Instalação e Configuração do Styled Compoenents
category: css
background: "#7d669e"
---

Uma das ferramentas mais adotadas pela comunidade para utilizar CSS-in-JS no React é a styled-components. Para adicioná-la no seu projeto, neste exemplo usando Yarn, basta executar o seguinte comando no terminal:

```
yarn add styled-components
```

Após a instalação, no início do seu arquivo *App.js* importe a biblioteca com inserindo a linha:

```
import styled from 'styled-components'
```

Para criar um componente estilizado basta declará-lo com o elemento “styled” seguido do elemento html que receberá o estilo. Veja o exemplo abaixo:

```
const Title = styled.h1`
    color: #F00;
    font-size: 32px;
`;
```

O componente declarado recebeu o nome de “Title”, será uma H1 de cor vermelha e tamanho 32px.

Obs: Caso você utilize o editor VS Code, há uma extensão chamada “vscode-styled-components” que pode ser instalada e que permite que o editor faça a sintaxe highlight dos estilos que você criar para os componentes da mesma forma que estivesse escrevendo CSS normal.

A principal característica do styled-components é que com ele os estilos criados ficam escopados apenas no componente definido, sem interferir em outros estilos da aplicação.

Para criar estilo gerais que vão atingir toda a aplicação é necessário configurar estilos globais.

## Configurando estilos globais

Para criar estilos globais recomenda-se criar uma nova pasta chamada *styles* dentro do diretório *src* do seu projeto, dentro dela criar um arquivo chamado *global.js*. Abra este arquivo e insira o código abaixo:

```
import { createGlobalStyle } from 'styled-components';import 'font-awesome/css/font-awesome.css';const GlobalStyle = createGlobalStyle`   * {    
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    outline: 0;
  }  body {
    background: #9B65E6;
    text-rendering: optimizeLegibility !important;
    -webkit-font-smoothing: antialiased !important;
    font-family: sans-serif;
  }`;export default GlobalStyle;
```

Feito isso abra seu aquivo *App.js* (remova a parte do componente “Title” criado no exemplo acima) e importe o estilo global:

```
import React, { Fragment } from 'react';import GlobalStyle from './styles/global';const App = () => (
  <Fragment>
    <GlobalStyle />
    <div className="App" />
  </Fragment>
);export default App;
```

O componente *GlobalStyle* foi importado e para para poder ser usado com os outros componentes foi aninhado dentro do componente *Fragment*.