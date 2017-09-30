# Friday 29th Notes
## The effect of React on web standards

>Karl Horky

* Uso del context `this` en estándares es un problema. 
* Mucho boilerplate.
* Custom elements es la propuesta del estandar
* Crítica a los problemas de los estándares
	* Incompatibilidades entre browsers
	* Insuficiente componentes
	* Imperativa y sin estado (barriendo para casa)
* Aproximaciones:
	* jQuery, dojo, mootools (2005-6)
	* CoffeScript (2009)
	* Angular, Knockout, Ember (2009-11)
* React, nuevos paradigmas
	* VirtualDOM
	* JSX
	* Programación Funcional
	* Inmutabilidad
	* Unidirectional Flow Data
	* Modelo de componentes
	* Desacoplado del DOM
	* Minimallismo.
* **Minimal surrface API Area** [Sebastian Markbage](https://www.youtube.com/watch?v=4anAwXYqLG8)
* Web Componentes, críticas
	* Asumen imperativa
	* No buena composición
	* Abrazan el DOM
* Web Standars proposal, process:
	* Stage 0 (strawman)
	* Stage 1 (proposal)
	* Stage 2 (draft)
	* Stage 3 (candidate)
	* Stage 4 (finished)
	* Inclusion in spec
* Objetivos de React en estándares
* [Taming the metalanguage](https://www.youtube.com/watch?v=_0T5OSSzxms)
* Proposición a los estándares:
	* Reducción del boilerplate
* Descripción de las diferentes propuestas de React a los estándares y su estado (stage)
	* [Dave Herman](http://effectivejs.com/), [Do Expressions (Stage 1)](https://github.com/tc39/proposal-do-expressions)
	* [Jordan Harband](https://github.com/ljharb)
	* Sebastian Markbage 
		* Immutable data structure
		* Shallow comparation
* Esfuerzos de integración
	* [skateJS]https://github.com/skatejs/skatejs()
* Futuros lenguajes
	* [ReasonML](https://reasonml.github.io/)
* Los estándares se mueven despacio, necesitan consenso. JUAS!!.
* [https://prop-tc39.now.sh](https://prop-tc39.now.sh)
* [tc39 proposals](https://github.com/tc39/proposals)

La idea es que los estándares son como dinosaurios, y React quiere ser estandar, en un momento de la charla comenta que React debería desaparecer en pos de un estandar que cubra su funcionalidad, así que van proponiendo cosas al tc, pero siguen su marcha.

## Modular CSS

> Andrey trolololo

CSS ha pasado de aplicarse en documentos para ser usado en apps. Pasaron 20 años desde el primer estandar.  Separación de contextos: CSS, HTML, JS.

Momento actual, HTML in JS aka JSX.  No hagas eso!!!, y todo el mundo lo hace. 

> f(state) => UI

[BEM](http://getbem.com/), manual work.

> BEM + JS = CSS Modules

CSS Modules necesitan el `build`. 

> CSS Modules + JS = [JSS](https://github.com/cssinjs/jss)

CSS in JS no necesita `build`

[www.styled-components.com](https://www.styled-components.com/)

En un futuro rendering para muchos tipos de device
[glamor css library](https://github.com/threepointone/glamor)
La mantenibilidad es posiblemente una de las mejores características para perfomance. Mucha repeticiñon en CSS, muy verbose.

CSS Funcional?

[styletron](http://styletron.js.org/)

Para que usar SASS si JS ya tiene parte de la funcionalidad

* [npm install glam](https://www.npmjs.com/package/glam)

Me falta contexto en CSS para poder aportar mi opinión, pero la idea es que CSS es muy verbose, crea grandes archivos que son dificiles de mantener y leer (ha mostrado métricas de como airbnb disminuye el tamaño de CSS usando algunas de las tecnologías de las que comenta en la charla) y que además es global. Critica el uso de SASS, LESS, etc, ya que muchas de las funcionalidades que proponen ya están incluidas en JS, así que muestra JSS como solución. Respecto a BEM comenta que es muy verbose y sigue con los problemas de origen de CSS, pero dio un poco de orden en su momento.

## React >> Redux, a development workflow

> Braulio the clown

Tal vez no necesites usar Redux desde el minuto cero de tu aplicación. 

** DEMO TIME **

Se han hecho un tutorial de React + Redux en directo. No se ve un carallo, y más sin gafas. 

## React Storybook

> Marie-Laure Thuret

[StoryBook](https://storybook.js.org/)

** DEMO TIME **

Es una herramienta para definir los diferentes estados de un componente. Cada Story es un estado del componente.

StoryShots, testing snapshots.

Visual regresion testing, [argo](https://speckyboy.com/wp-content/uploads/2010/03/four-oh-four_08.jpg)

Una buena herramienta para comunicar con otros. Se adjuntan al PR o a la Issue.

## A practical guide to Redux Form

> Erik Rasmussen

Formularios, el peor problema en desarrollo frontend:

* Validación
* Tasa de cambio de estado alta
* Comunicación con el usuario

Cambia el estado desde los hijos del formulario al padre, que maneja el estado y se lo pasa a los hijos. Los cambios en los hijos se pasan mediante callbacks, manteniendo el paradigma de React.

[Redux Form](https://redux-form.com)

* a single reducer
* a HOC form

** LIVE CODING **

Importa el `redux-form`, crea un componente que renderice un `form` con los campos del formulario y se lo pasa a una HOC que le da el `redux-form`. Ya tiene conectado el formulario a redux.

Crea un componente `renderComponent` y la librería le inyecta estados en una propiedad `meta`. Puede acceder a errores de validación a través del `meta` que se muestran en el formulario.

## Lightning Talks
### Custom CSS is the path to inconsistent UI

> Artem Sapegin 

Que significa inconsistencia?. La introducción de variables disminute la inconsistencia.

Cual es la solución. El uso de components en vez de custom CSS

[Nathan curtis framework](https://medium.com/@nathanacurtis)

Me pasa lo que en la charla anterior de CSS, que me falta contexto, pero lo que viene a decir es que uses components y no uses Custom CSS, lo contrario del de la primera charla de CSS, WTF!!.

### Beyond JavaScript: The Real Benefit of React Native

> Wojciech Ogrodowczyk

[Piraha people](https://en.wikipedia.org/wiki/Pirah%C3%A3)

La gente que construye los botes somos los programadores.

"Premature optimisation is the root of all evil". Donald Knuth

Descenso de bgs usando typescript o flow

## React Native - Case study: From zero to a super hero app

> Ferran Negre

Explica la creación de un side projectsobre twshows. 
Material theme

* Architecture, Redux, [redux-observable](https://redux-observable.js.org/), realm, [asyncstorage](https://facebook.github.io/react-native/docs/asyncstorage.html)
* Styling and theme, material design.
	* [react-native-paper](https://github.com/callstack/react-native-paper)
	* soporta modo dia & noche
* Internacionalización:
	* [react-native-i18n](https://github.com/AlexanderZaytsev/react-native-i18n)
* Orientation: no bloquear orientación
* Navigation: [Deep linking](https://en.wikipedia.org/wiki/Mobile_deep_linking)
Cuando pones la React-native app en background, el OS se carga la app. Puede que lo haga en menos de un minuto. [AppState](https://facebook.github.io/react-native/docs/appstate.html) es un listener que controla si la Aop está en background o vuelve a foreground. Esta librería guarda el estado de la app. AppState MOLA!!!.
* Background tasks: controlar los cambios de datos externos por ejemplo. 
	* [HeadlessJS](). Ejecuta tareas de JS mientras la App está en background
	* [Android SyncAdapter](https://developer.android.com/training/sync-adapters/creating-sync-adapter.html) => [react-native-sync-adapter](https://github.com/ferrannp/react-native-sync-adapter)
* Animated API de React Native:
	* useNativeDriver: true
	* Las animaciones suceden en la parte nativa
	* Deligthful interactions
* Permissions
	* Remove permissions
* App Store
	* [CodePush](https://microsoft.github.io/code-push/)

## Mutable or Immutable?. Let's do both

> Mattia Manzati

Gestión del estado por:

* Redux
* Mobx

Cual elijo?, depende...

Son patrones opuestos:

* redux => immutable
* mobx => mutable

**Rehydratation** mas facil con redux, con mobx tenemos que serializar y deserializar nuestro estado ya que los compoenntes pueden tener estado interno.

**Snapshots** son mejor con Redux.

[mobx-state-tree](https://github.com/mobxjs/mobx-state-tree) lo mejor de los dos mundos:

* definimos un datashape que será claro y las accinones están definidas
* Podemos obtener snapshots de nuestros datos, Podremos crear una instancia de snapchost también. Así como escuchar cambios en el snapshot.
* Componiendo modelos
* Types
* Typechecking
* Reconciliación.
* Acciones, con redux podemos reporducir el flujo de acciones. No con Mobx. `mobx-state-tree` incluye esto para mobx
* Observabilidad:
	* fine grained en mobx
	* si cambian las referncias, cambian los valores
	* con `mobs-state-tree` se tienen las dos, pero si los valores cambian, se obtiene una nueva snapshot

Podremos crear una Redux store desde una instancia de MST  out-the-box