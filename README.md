# Bootcamp Rocketseat Arquitetura Flux

## Estrutura do Projeto

```
$ yarn create react-app

```

Já vem com Babel e Webpack configurados
O Webpack e o Babel estão em react-scripts (v. package.json)

Em package.json

```
 "scripts": {
    "start": "react-scripts start", -> ambiente de desenvolvimento
    "build": "react-scripts build", -> ambiente de produção
    "test": "react-scripts test", -> rodar os testes
    "eject": "react-scripts eject"-> Para configurar Babel e Webpack se quiser configurar do zero
  }

```

- Deletar configurações do EsLint para configurá-lo do zero;

- Deletar arquivo manifest.json;

- Os arquivos da pasta src já vêm configurados por padrão;

  \$ yarn start

Roda a aplicação em localhost:3000

Deletar da pasta src:

- app.css
- app.test.js
- index.css
- logo.svg
- serviceWorker.js

Em index.js

- remover as partes do serviceWorker;
- a importação do CSS;

Em App.js

- remover a logo e o CSS;

## ESLint, Prettier & EditorConfig

- Botão direito e escolher Generate .editorconfig
- Trocar os falses p true e add end_of_line = lf

      $ yarn add eslint -D

      $ yarn eslint --init

Selecionar To check syntax, find problems, and enforce code style
e depois as seguintes que já aparecem selecionadas

? Would you like to install them now with npm? escolher Yes
? Does your project use TypeScript? (y/N) N (escolher Não)
Y para o resto

Vai instalar todas as bibliotecas

Remover package-lock.json e rodar

     $ yarn

Para atualizar as dependências em yarn.lock

Instalar dependências

Exceto babel-eslint como está no vídeo. Isso pq ele já vem no react-scripts
Então o comando correto fica desse jeito:

\$ yarn add prettier eslint-config-prettier eslint-plugin-prettier -D

Fazer as modificações em .eslintrc.js

Salvar e criar arquivo .prettierrc na raiz

O prettier deixa o código mais bonito e o EsLint procura por erros

Para rodar o servidor:

```
$ yarn start

```

## Configurando Rotas

\$ yarn add react-router-dom

src/Pages/Cart - Carrinho

src/PagesHome - principal

#### BrowserRouter

Em routes.js não importa o BrowserRouter.

Ele vai ser importado em app.js. Isso pq o Header da aplicação vai se manter
em todas as rotas, pois vai ter como função, fazer a navegalção do site.

## Estilos Globais

\$ yarn add styled-components

Google font Roboto

Imagem de background baixada de link na page da aula
background: #191919 url(\${background}) no-repeat center top;

## Criando Header

## Estilizaçao da Home

lib para manipular cores no javascript polished

$ yarn add polished

escurece cor do botão de adicionar ao carrinho

## Estilização do Carrinho

## Configurando API

#### json-server

API fake p projetos em desenvolvimento

https://github.com/typicode/json-server

Para instalar

$ yarn global add json-server

Arquivo da API

    server.json

Tem as rotas - 'stock' e 'products'

    src/services/api.js

    $ yarn add axios

#### Para rodar a API

    json-server server.json -p 3333 -w

## Buscando produtos da API

#### formatação do preço dos produtos

Utiliza funcionalidade nativa do Javascript chamada Intl

É uma classe para fazer internacionalização

Criar src/utilformat.js

importar a função formatPrice em Home/index













