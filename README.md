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

## Configurando o Redux

Instalar pacote do Redux e sua integração com react 

    $ yarn add redux react-redux 

Em src/store vão ficar todos os arquivos relacionados ao Redux

O store será o estado global

Importar Provider from react-redux em App.js. O Provider deixa o store disponível para
todos os componentes. O store deve ser passado como parâmetro na tag Provider.

Agora toda a aplicação tem acesso ao store


Em src/store/index.js vai estar um Reducer (q vai ser o carrinho de compras) no formato de função.
Dele será retornado o stado inicial do carrinho - array vazio.

P melhorar, jogar o reducer dentro de src/store/modules/cart/reducer.js

É possível ter vários reducers dentro de uma aplicação e para isso deve-se combinar todos os reducers em 
um único reducer

Para ter vários reducers

  store/modules/rootReducer.js 

Em rootReducer importar combineReducers 

## Adicionando ao carrinho

Objetivo - Fazer com que o Reducer do Cart seja acessível à toda a aplicação

Quando clicar em adicionar ao carrinho. Passar o objeto do produto para 
o reducer do Cart.


#### disparar ação do botão 'adicionar ao carrinho'

Em Home/index.js:

Importar connect from react-redux. O connect retorna a funçao Home. O connect
conecta o componente com o estado do Redux

Para realizar uma alteração no estado é preciso disparar a ACTION

#### ACTION:

É um objeto que contém um 'type' (obrigatório) e outros conteúdos que quiser

onClick this.handleAddProduct(product)

Todo componente que se conecta com o Redux recebe uma propriedade chamada 'dispatch'

#### Dispatch 

É uma propriedade que serve para disparar uma action ao Redux.

    this.props.dispacth

Sempre que se dispara uma action, um dispatch, de dentro de um componente, todos os reducers
são ativados. 

As informações específicas p a ação esta variável 'action'. Todo reducer
recebe por padrão as variáveis 'state' e 'action'

    export default function cart(state, action)

A action é a ação que se está disparando

O state é o state anterior da alteração feita pela action

Todo reducer vai seguir o esquema switch/case

então p ouvir a action ADD_TO_CART, cria-se um case e retorna o state modificado como quiser

    switch(action.type){
    case 'ADD_TO_CART':
      return [];
      default: 
      return state;
    }

No caso, o switch vai garantir que este reducer só ouça a ação add to cart

Os reducers que não ouvirem a ação, deixarão o state da forma como estava - 
por isso o return state

Para acessar as informações do reducer dentro de outro componente qualquer
deve-se usar o connect que tem como parâmetro uma função que é o state que retorna as informações
que se quer acessar - retorna em formato de objeto.

Sempre que o state mudar, o componente vai ser renderizado do zero, mostrando assim, as novas 
informações que se tem no estado do Redux

cartSize para mostrar quantos produtos foram colocados no carrinho

#### fluxo do redux 

* Componente dispara Action;
* Action avisa o Reducer;
* Reducer faz as alterações necessárias;
* Redux avisa todos os componentes que precisam da informação;
* Estes componentes se atualizam com a nova informação;




























