# Saturday 30th Notes
## End to End testing React applications

> Forbes Lindesay

Lo normal es esto:

		Unit Tests > Integrationg tests > e2e

Preferible esto 

		Static analisis > JS Tests > e2e tests

Why static analisys?

* Cover 100%
* Captura asunciones incorrectas
* Eslint, TSLint
* [Flow](https://flow.org/), TS
* [prettier](https://github.com/prettier/prettier) is an opinionated code formatter

Porqué TS Tests?

* No testea lo que hace el usuario
* Se necesitan muchos tests para mejorar la cobertura
* [JEST](https://facebook.github.io/jest/), Delightful JavaScript Testing

Porqué e2e tests?

* Testean lo que de verdad quieres hacer
* Expone inconsistencia del browser
* Pocos text tienen una gran cobertura
* Única manera de saber que el sistema está funcionando
* Lentos, caros y dfíciles de seguir, ¿qué falla?

Los dos primeros puntos cubren un 80% de los bugs

* Un WebDriver expone una API consistente para automatizar browsers

* [SAUCELabs](https://saucelabs.com/)
* [BrowserStack](https://www.browserstack.com/)
* [TestingBot](https://testingbot.com/)
* [CrossBrowserTesting](https://crossbrowsertesting.com/)

* [JSDOM](http://airbnb.io/enzyme/docs/guides/jsdom.html) a full implementación del DOM en JS + [TAXI-RANK](https://github.com/ForbesLindesay/taxi-rank) tienes el mismo interface que en el browser pero lo puedes ejecutar en node.js

* [Cabbie](https://www.npmjs.com/package/cabbie) Esto es un típico yo he venido aquí a hablar de mi libro...

Parece que pivota sobre el `dataTestId`, es el id de test

		this.props('data-test-id')
	
** DEMO TIME **

* **Nunca meter un timeout en el Test** JUAS!!
* Polling el website hasta que adquiera las condiciones necesarias para lanzar el test

** LIVE DEMO TIME **

Carga el driver con `cabbie` que es el que emula el DOM. Después con `driver.getElement['whatever'] ` captura lo que quiere testear

Ha venido a comentar **SU** stack de herramientas para realizar e2e testing. Me quedo con lo que ha comentado al principio de manejar análisis estáticos con testing de JS y e2e test para dar una mejor cobertura al desarrollo, sin tener que volverse loco con los test unitarios

### Refs
[End to End (e2e) Testing React Apps With Selenium WebDriver And Node.js is Easier Than You Think](https://marmelab.com/blog/2016/04/19/e2e-testing-with-node-and-es6.html)

## Writing highly reusable React components
> Javi Velasco

[react-toolbox](http://react-toolbox.com/)

Es el creador de la librería. Comenta los problemas del CSS en el JS a la hora de estilizar los componentes de su librería. 

Vuelve a aparecer [www.styled-components.com](http://www.styled-components.com)

## The Dream of Styleguide Driven Development
> Sara Vieira
> [http://blog.npmjs.org/post/161303607370/npm-pride-2017](http://blog.npmjs.org/post/161303607370/npm-pride-2017)

Mas CSS.

[PostCSS Caralho Plugin](https://www.npmjs.com/package/postcss-caralho)

Styleguide Driven Development, es un cambio de perspectiva. Custom CSS es la muerte del desarrollador.

Empieza el desarrollo mostrando un archivo con Tipografía, estilos de botones, iconos, y demás partes del UI, pero sin montar. La idea es dividir el layout en bloques. 

[React Styleguidist](https://github.com/styleguidist/react-styleguidist)

Podemos crear componentes isolados. Se pueden testear extensivamente. 

* Tags `jsx` para Markdown

Pequeña descripción del proceso de StoryBook

Como integrar este paradigma:

* Desarrolladores:
	* Usar un repo propio en una carpeta separada
	* Crear un NPM package y mantenerlo
	* Usar [lerna](https://github.com/lerna/lerna) y [Monorepo](https://www.google.es/search?q=Monorepo)
	
* Diseñadores
	* [sketch](https://www.sketchapp.com/) con [kactus](https://github.com/kactus-io/kactus)
	* [Figma](https://www.figma.com/)
	
Porqué debemos usar SDD. 

* Hacemos los estilos mucho más mantenibles. 
* Menos bug específicos. CSS es duro. 
* Una fuente de la verdad, la guia de estilos. 
* Mejor para el UT

## Building a Realtime Chat with GraphQL Subscriptions

> Nikolas Burk

¿Qué es GraphQL?

* Es un nuevo API standard
* Un lenguaje de query para APIs
* Una forma declarativa de comunicarse con la API

Diferencias entre REST y GraphQL

Para leer la información de un usuario de blogging app en REST:

* 3 API enpoints
	* `/users/id`
	* `/users/<id>/posts`
	* `/users/<id>/followers`
	
Cada llamada a la API devuelve mucha información que no necesitamos. Hay mejores maneras de diseñar una API REST. Pero es mas verbose al comunicarse con el backend

Para hacer lo mismo con GraphQL

Obtiene lo mismo pero con una sola request. En vez de hacer un `GET` para obtener la info, hace un `POST` con la especificación de lo que quiere obtener.  Solo tiene un endpoint. 

* `mutations` para insertar, eliminar datos
* `query` para consultas

El servidor de GraphQL será [graphcool](https://www.graph.cool/). Creación del modelo, `Person` y `Message`. 

		$ gc playground

Esto es una consola para comunicarse con `graphcool`. Se puede acceder desde el navegador.

* `queryVariables` se pueden incluir en las `mutations` para crear funciones

GraphQL Subscriptions, actualizaciones en tiempo real event-based. Implementadas habitualmente con `websockets`

GraphQL Clients:

* API para queries y subscripciones
* Cuidado con el caché
* Clientes:
	* [Relay](https://facebook.github.io/relay/) 
	* [Apollo Client](https://github.com/apollographql)
		* [React Apollo](https://github.com/apollographql/react-apollo)
	
** DEMO TIME **

Al poner en marcha el servidor, este expone las diferentes URLs, entre ellas las de `wss` donde se pueden conectar las subcripciones.

		$ gc logs 

Server side subcripciones

### Refs

* [How to GrapgQL](https://www.howtographql.com/)
* [Grahpql Weekly](https://graphqlweekly.com/)
* [GraphQL Radio Podtscats](https://graphqlradio.com/)

## Code-splitting in React apps

> Glenn Reyes

* Cortar el código e importarlo bajo demanda. En vez de empaquetar en un único `bundle.js` se corta el código y se crean mas archivos `js`. Se carga la página hasta 5x 

¿Volvemos al paradigma de `require.js`?.

Caching y carga del código de manera asíncrona y bajo demanda.

[Code splitting](https://survivejs.com/webpack/building/code-splitting/)

Sync vs async imports.

Introduce async - await con la importación asíncrona. Con esta estrategia, define un componente en el estado de otro componente de React, y hace `async` el `componentDidMount` y `await` la importación.

Recomienda el uso de [Promise.all](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

[react-loadable](https://github.com/thejameskyle/react-loadable)

[TC39 dinamyc imports proposal](https://github.com/tc39/proposal-dynamic-import)

[react-perimeter](https://github.com/aweary/react-perimeter) para predecir

Cortar el app y vendor, route and component

[next.js](https://github.com/zeit/next.js/)

## Redux Saga, the Viking way to manage side effects

>  Nacho Martín

Isloate los side-effects(**SE**) en la parte del middleware. [redux-thunk](https://github.com/gaearon/redux-thunk), es el que lanza las acciones con SE

[redux-saga](https://github.com/redux-saga/redux-saga) una librería para manejar SE

Aprovecha el uso de `generators` ES2016, con `next` ejecutaremos hasta el primer `yield` que encuentre, si no hay mas yields, devuelve `false`. La primera ejecución del `generator` no acepta parámetros. La unión de `generators` con `promises` le aporta mucha legibilidad. Hay que añadir muchos `yield` en el código.

Hace una descripción de muchas de las operaciones de `redux-saga`

`redux-saga` exporta efectos. 

## Introduction to ReasonML = (sick) => The road to a Statically Typed Future

> Patrick Stapfer

Nada sobre [ReasonML](https://github.com/reasonml)

Diferencia entre TS y Flow. El análisis. Con flow no hace falta describir el tipo de los argumentos, variables, los detecta en periodo de análisis. Menos verbose.

Trust Killer de Flow:

* any
* object
* Function

* [flow-runtime](https://github.com/codemix/flow-runtime)
* [andreypopp/validated](https://github.com/andreypopp/validated)
* [flow-typed](https://github.com/flowtype/flow-typed)

Fully typed architecture, con las librerías de 3º y con la API

* Como mejorar:
	* compilar a JS
	* Más funcional
	* tipado
	* strong tooling
	* easy interop
	
[purescript](http://www.purescript.org/)

Ufff, al final si que ha llegado a ReasonML...

[bucklescript](https://github.com/BuckleScript/bucklescript), coje reasonML y devuelve archivos JS

Del tooling nos falta immutable, Ramda, Flow y Flow-typed. Con ReasonML se carga todo menos webpack y mete el anterior.



## Case sudy: Lucentum, creating our own React component librarys

> Flavio Corpa

## Deploying atomic design system at scale

> Nick Balestra

[Open Components](https://github.com/opentable/oc)