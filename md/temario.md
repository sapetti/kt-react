# React

=====

### Agenda 

* React – Conceptos principales
* [JSX](https://es.reactjs.org/docs/introducing-jsx.html)
* [Renderizado de elementos](https://es.reactjs.org/docs/rendering-elements.html)
* Componentes y tipos de componente
* Props
* [State](https://es.reactjs.org/docs/react-component.html#setstate)
* [Ciclo de vida de los componentes](https://es.reactjs.org/docs/react-component.html#the-component-lifecycle)
* Children
* Eventos
* Estilos

_____

* Patrones de diseño
  * [HOC](https://es.reactjs.org/docs/higher-order-components.html)
  * [Render Props](https://reactjs.org/docs/render-props.html)
* [Fragmentos](https://es.reactjs.org/docs/fragments.html)
* [Contexto](https://es.reactjs.org/docs/context.html)
* [Error boundaries](https://es.reactjs.org/docs/error-boundaries.html)
* [Lazy/Suspense](https://es.reactjs.org/docs/code-splitting.html)
* [Portals](https://es.reactjs.org/docs/portals.html)
* [Hooks](https://es.reactjs.org/docs/hooks-intro.html)
* [PureComponent](https://es.reactjs.org/docs/react-api.html#reactpurecomponent)
* [React.memo](https://es.reactjs.org/blog/2018/10/23/react-v-16-6.html#reactmemo)
* [React.lazy](https://es.reactjs.org/blog/2018/10/23/react-v-16-6.html#reactlazy-code-splitting-with-suspense)
* [StrictMode](https://es.reactjs.org/docs/strict-mode.html)
* [Webpack](https://webpack.js.org/) – Conceptos básicos

_____

* create-react-app
* Extensiones VS Code
* [React Developer Tools](https://es.reactjs.org/docs/optimizing-performance.html#virtualize-long-lists)
* Redux – Conceptos básicos
  * Redux Developer Tools
* Otras librerías
  * [React Router](https://reacttraining.com/react-router/) - Amiga Framework
  * GraphQL
  * [Formik](https://github.com/jaredpalmer/formik) - Formularios
  * [Downshift](https://github.com/downshift-js/downshift) - dropdown/autocomplete/select
  * [Virtualizar listas largas](https://es.reactjs.org/docs/optimizing-performance.html#virtualize-long-lists)
    * [react-window](https://react-window.now.sh/)
    * [react-virtualized](https://bvaughn.github.io/react-virtualized/) - Amiga Framework
* Test
  * [Jest](https://jestjs.io/) - Amiga Framework
  * [Enzyme](https://airbnb.io/enzyme/)
* [Plugin maven para incluir apps react](https://github.com/eirslett/frontend-maven-plugin)

_____

* Amiga - Framework Front
  * Application
  * Router
  * Redux: Actions, Reactions...
  * i18n
  * Logging
  * Mocking
  * Test

Ideas

* Rest/Spread props
* Loops
* Ref
* sobreescribir estilos
* Extensiones VS Code
  * sublime-babel-vscode
* Preguntar quien conoce NodeJS, NPM, NPX, React, ES6, Babel y Webpack
* Create-react-app zero configuration
* Synthesize events
* npx create-react-app my-app
* chiste tutorial code tutorial code
* Flux -> Redux
* Redux imagenes
* Redux boilerplate
* Single source of truth - un unico estado
* State es solo lectura - unidirectional data-flow
* Changes performed with pure functions, avoids non-deterministic events
* Redux lifecycle - imagenes 
* https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/Sintaxis_Spread
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters

=====

* Libreria Javascript para crear interfaces sencillas
* De manera declarativa
* Basadas en Componentes (manejan su propio estado)
* Como un Lego, a partir de piezas sencillas crear estructuras más complejas
* Learn Once, Write Anywhere - DOM, Native, VR

=====

# JSX

* Extensión de JavaScript
* Crear elementos de React

_____

<pre><code data-trim class="hljs">
React.createElement(component, props, ...children)
</code></pre>

![](../images/createelement.png)

_____

<pre><code data-trim class="hljs">
<h1>JSX rocks!!</h1> // Sigue siendo JS
</code></pre>

![](../images/jsx.png)

_____

[Babel REPL](https://babeljs.io/repl)

![](../images/babel.png)

_____

<pre><code data-trim class="hljs">
console.log(<h1>Hello World</h1>)
</code></pre>

<pre><code data-trim class="hljs">
{
    $$typeof: Symbol(react.element),
    key: null,
    props: {
        children: "Hello World"
    },
    ref: null,
    type: "h1",
    _owner: null,
    __proto__: Object
}
</code></pre>

_____

<pre><code data-trim data-line-numbers class="hljs">
const element =
  React.createElement('div', null,
        React.createElement('p', null,
              React.createElement('h1', null, 'Hello World')))
</code></pre>

<pre><code data-trim data-line-numbers class="hljs">
const element = (
  &lt;div&gt;
    &lt;p&gt;
      &lt;h1&gt;Hello World&lt;/h1&gt;
    &lt;/p&gt;
  &lt;/div&gt;
)
</code></pre>

_____

## Interpolación en JSX

<pre><code data-trim class="hljs">
<p><%= 1 + 2 %></p>
</code></pre>

<pre><code data-trim class="hljs">
<p>{ 1 + 2 }</p>
</code></pre>
_____

<pre><code data-trim class="hljs">
const world = 'Mundo'
<p>{ 'Hola ' + world }</p> // <p><%= 'Hola ' + world %></p>
<p>{ `Hola ${world}` }</p>
</code></pre>

_____

<pre><code data-trim class="hljs">
function someFn() {
  return 'someResult'
}
<p>{ someFn() }</p> // <p><%= someFn() %></p>
<p>{ Math.max(2, 5) }</p>
</code></pre>

_____

<pre><code data-trim class="hljs">
const isEmpty = true
&lt;p&gt;
  {
    1 &lt; 2 ? &lt;h3&gt;1 es menor que 2&lt;/h3&gt;
          : undefined
  }
&lt;/p&gt;
&lt;p&gt;
  {
    isEmpty &amp;&amp; &lt;h3&gt;Esta vac&iacute;o&lt;/h3&gt;
  }
&lt;/p&gt;
</code></pre>

=====

## Renderizado

* [codepen.io](https://codepen.io/)
  * Preprocesador de Javascript: Babel
  * Librerías:
    * React - Funcionalidad común (createElement, Component, Children...)
    * ReactDOM - Funcionalidad ligada al navegador (render, mount...)

* [codesandbox.io](https://codesandbox.io/)
  * React template
_____

Learn Once, Write Anywhere

\* [react-dom](https://github.com/facebook/react/tree/master/packages/react-dom), [react-native](https://facebook.github.io/react-native/), [react-vr](https://facebook.github.io/react-360/)...

_____

Vamos a probar a renderizar nuestro propio elemento
_____

<pre><code data-trim class="hljs">
ReactDOM.render(<h1>Hello World</h1>, 
                document.getElementById('root'))
</code></pre>

<iframe height="350" style="width: 100%;" scrolling="no" title="HelloWorld" src="https://codepen.io/sapetti/embed/PowqjJd?height=350&theme-id=default&default-tab=html,result&font-size=20px" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/PowqjJd'>HelloWorld</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

<iframe height="600" style="width: 100%;" scrolling="no" title="Tick" src="https://codepen.io/sapetti/embed/dyPozxB?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/dyPozxB'>Tick</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

* Hasta ahora solo hemos visto como crear elementos y renderizarlos
* Elementos inmutables (no se pueden cambiar hijos o atributos)
* Normalmente solo habrá un render() por aplicación

=====

### Componentes

<pre><code data-trim class="hljs">
// Function Components
function Hello() {
  return <h1>Hello World</h1>;
}
</code></pre>

<pre><code data-trim class="hljs">
const Hello = () => <h1>Hello World</h1>
</code></pre>

<pre><code data-trim class="hljs">
// Class Components
class Hello extends React.Component {
    render() {
        return <h1>Hello World</h1>;
    }
}
</code></pre>

_____

* El nombre de los componentes deben empezar por mayusculas (Box, UserList, MyComponent...)
* Método render obligatorio en componentes de clase
* Deben devolver
  * Un único elemento
  * Un array de elementos o Fragmentos
  * Portales
  * Strings o numeros
  * Boolean o nulos

_____

En el caso de los componentes usamos JSX

<pre><code data-trim class="hljs">
ReactDOM.render(&lt;Hello /&gt;, document.getElementById('root'))
</code></pre>

<iframe height="350" style="width: 100%;" scrolling="no" title="Hello Component" src="https://codepen.io/sapetti/embed/KKwpXVZ?height=350&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/KKwpXVZ'>Hello Component</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

=====

## Props

* Los componentes aceptan atributos
* Solo lectura (componentes como funciones puras)
* One way data flow
* camelCase

_____

<pre><code data-trim class="hljs">
function Hello(props) {
  return <h1>Hello { props.name }</h1>;
}
</code></pre>

<iframe height="400" style="width: 100%;" scrolling="no" title="Props" src="https://codepen.io/sapetti/embed/zYxGaNy?height=400&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/zYxGaNy'>Props</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

<pre><code data-trim class="hljs">
class Hello extends React.Component {
    render() {
        return <h1>Hello {this.props.name}</h1>
    }
}
</code></pre>

<iframe height="400" style="width: 100%;" scrolling="no" title="Props Class" src="https://codepen.io/sapetti/embed/eYmNKWP?height=400&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/eYmNKWP'>Props Class</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

<pre><code data-trim class="hljs">
&lt;Hello name='Walter' /&gt;

&lt;Hello { name: 'Walter' } /&gt;

function Hello({ name, surname }) {
  return &lt;h1&gt;Hello { name } { surname }&lt;/h1&gt;
}

const user = { name: 'Walter', surname: 'White' }
const element = &lt;Hello { ...user } /&gt;
</code></pre>

_____

## Prop Types

* Comprueba el tipo de las propiedades en tiempo de ejecución
* Solo en modo desarrollo
* String, Boolean, Array, Function, Number, Symbol, Node, Enum...
* Mas de un tipo
* Obligatorio
* Validación personalizada
* No se incluye en la librería de React

_____

<pre><code data-trim class="hljs">
npm i prop-types
</code></pre>

<pre><code data-trim class="hljs">
import PropTypes from 'prop-types'

function Hello({ name, surname }) {
  return <h1>Hello { name } { surname }</h1>
}

Hello.propTypes = {
    name:       PropTypes.string.isRequired,
    surname:    PropTypes.string
}

&lt;Hello surname={2} /&gt;
</code></pre>

_____

## Default Props

<pre><code data-trim class="hljs">
import PropTypes from 'prop-types'

function Hello({ name, surname }) {
  return &lt;h1&gt;Hello { name } { surname }&lt;/h1&gt;
}

Hello.defaultProps = {
    surname: 'White'
}

&lt;Hello name='Walter' /&gt;
// Walter White
</code></pre>

_____

<pre><code data-trim class="hljs">
function Hello({ name, surname = 'White' }) {
  return &lt;h1&gt;Hello { name } { surname }&lt;/h1&gt;
}

&lt;Hello name='Walter' /&gt;
// Walter White
</code></pre>

=====

## Eventos

* Igual que los eventos en el DOM pero en camelCase
  onclick -> onClick, onchange -> onChange
* Reciben una función y no un string
  onclick="requestData()" -> onClick={requestData}
* Hay que llamar a preventDefault, no podemos devolver false para evitarlo
* El handler recibe un evento sintético de React (evita problemas de incompatibilidad entre navegadores)
* [Listado de eventos soportados](https://es.reactjs.org/docs/events.html#supported-events)

_____

#### Definición de handlers - Funciones flecha

<iframe height="400" style="width: 100%;" scrolling="no" title="Events - Arrow Functions" src="https://codepen.io/sapetti/embed/WNbrpEV?height=400&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/WNbrpEV'>Events - Arrow Functions</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<sub>Problemas de performance</sub>

_____

#### Definición de handlers - Bind

<iframe height="400" style="width: 100%;" scrolling="no" title="Events - Bind" src="https://codepen.io/sapetti/embed/LYEGLPP?height=400&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/LYEGLPP'>Events - Bind</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<sub>Mucho código y muy repetitivo</sub>

_____

#### Definición de handlers - Campos públicos de clases

<iframe height="400" style="width: 100%;" scrolling="no" title="Events - Public field" src="https://codepen.io/sapetti/embed/bGNERGo?height=400&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/bGNERGo'>Events - Public field</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<sub>Experimental. Por defecto incluida con create-react-app</sub>

=====

## Ref

Es una forma de acceder a los nodos del DOM o a elementos creados en el metodo de renderizado

* Controlar el foco
* Selección de texto
* Reproducción de medios
* Inputs de tipo file

_____

<iframe height="600" style="width: 100%;" scrolling="no" title="Refs" src="https://codepen.io/sapetti/embed/OJPQPXm?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/OJPQPXm'>Refs</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

=====

## State

* El estado es local (componentes de clase***)
* No es accesible desde otro componente
* Cada componente tiene su propio estado
* Crearemos la propiedad de clase state que contendrá el estado del componente
* No modificar el estado directamente
* Usaremos el método setState para actualizarlo
* setState lanza un re-renderizado (salvo excepciones)
* setState puede ser asincrono!!
* setState hace un shallow merge del objeto que se envía con el estado existente

_____

<iframe height="550" style="width: 100%;" scrolling="no" title="Props Class" src="https://codepen.io/sapetti/embed/oNgXPZM?height=550&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/oNgXPZM'>Props Class</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

Cada componente tiene su propio estado

<iframe height="550" style="width: 100%;" scrolling="no" title="First State Component" src="https://codepen.io/sapetti/embed/RwNPYjO?height=550&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/RwNPYjO'>First State Component</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

setState puede ser asincrono!!

<pre><code data-trim class="hljs">
state = { counter: 0 }
// ...
this.setState({ counter: this.state.counter + 1}) // counter: 0 + 1
this.state.counter // 0

// O

this.setState({ counter: this.state.counter + 1}) // counter: 0 + 1
this.setState({ counter: this.state.counter + 1}) // counter: 0 + 1
// ...
this.state.counter // 1
</code></pre>

_____

<iframe height="650" style="width: 100%;" scrolling="no" title="setState is async" src="https://codepen.io/sapetti/embed/povJOLe?height=650&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/povJOLe'>setState is async</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

Mejor usar setState(callback)

<pre><code data-trim class="hljs">
this.setState((state, props) => {
    return { counter: state.counter + 1 }
})
</code></pre>

_____

<iframe height="650" style="width: 100%;" scrolling="no" title="setState is async" src="https://codepen.io/sapetti/embed/rNaVqgE?height=650&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/rNaVqgE'>setState is async</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

setState hace un merge shallow del objeto que se envía con el estado existente

<pre><code data-trim class="hljs">
state = {
    counter: 0,
    user: 'Walter',
}
// ...
this.setState({ user: 'Skyler' })
// state: { counter: 0, user: 'Skyler' }
</code></pre>

_____

Ojo con los objetos
<iframe height="600" style="width: 100%;" scrolling="no" title="setState shallow merge" src="https://codepen.io/sapetti/embed/BayNGar?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/BayNGar'>setState shallow merge</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

=====

## Componentes controlados y no controlados

* Los componentes controlados son aquellos en los que cada campo del formulario tiene un handler para cambios
* Los compnentes no controlados son aquellos que no tienen handlers por cada campo y recopilan el estado en un único momento (onSubmit)

_____

### Componentes controlados

<iframe height="600" style="width: 100%;" scrolling="no" title="Controlado" src="https://codepen.io/sapetti/embed/qBExEMb?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/qBExEMb'>Controlado</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

### Componentes no controlados

<iframe height="600" style="width: 100% !important;" scrolling="no" title="No Controlado" src="https://codepen.io/sapetti/embed/VwYQevY?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/VwYQevY'>No Controlado</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

=====

## Ciclo de vida

[Métodos comunes del ciclo de vida](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

![](../images/lifecycle-simple.png)

[React Reconciliation](https://es.reactjs.org/docs/reconciliation.html)

_____

Funciones puras:

* No hace side effects
* No modifica estado del componente (bucles infinitos)
* Devuelve el mismo resultado para cada vez que se invoca

_____

### Render phase

* constructor: Para inicializar el estado local o enlazar eventos. Recibe las props y debe hacer super(props).
* render: Obligatorio. Devuelve elementos React, Arrays, Fragmentos, Portales, Strings, Numeros, Booleanos o nulos.

_____

### Commit phase

* componentDidMount: Suscribirse a servicios.
* componentDidUpdate: Realizar operaciones en el DOM tras una actualización o peticiones de red. Recibe el estado y las propiedades anteriores. Cuidado si se llama setState, puede crear un bucle infinito.
* componentWillUnmount: Borrar las suscripciones a servicios.

_____

<iframe height="600" style="width: 100%;" scrolling="no" title="Component lifecycle" src="https://codepen.io/sapetti/embed/GRgJPOb?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/GRgJPOb'>Component lifecycle</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>
_____

Hay más métodos.

Según sea necesario, React realizará llamadas a métodos del ciclo de vida de los componentes

_____

* Al crear un componente se llaman los siguientes métodos
  * constructor
  * getDerivedStateFromProps
  * render
  * componentDidMount

_____

* Al lanzar una actualización a través del estado o las props
  * getDerivedStateFromProps
  * shouldComponentUpdate
  * render
  * getSnapshotBeforeUpdate
  * componentDidUpdate

_____

* Al eliminar el componente del DOM
  * componentWillUnmount

_____

* Al ocurrir un error
  * getDerivedStateFromError
  * componentDidCatch

=====

## Children

* Los componentes pueden tener ningun, uno o varios hijos
* Podemos usar la API de **React.Children** para tratarlos
* Favorecen la composición

_____

<iframe height="600" style="width: 100%;" scrolling="no" title="props.children" src="https://codepen.io/sapetti/embed/KKwdrrL?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/KKwdrrL'>props.children</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

* props.children puede ser de cualquier tipo (array, objeto, función...)
* Esto hace que trabajar con los hijos sea un poco caótico

_____

Un unico hijo no funciona en este ejemplo

<iframe height="600" style="width: 100%;" scrolling="no" title="props.children fail!" src="https://codepen.io/sapetti/embed/bGNVQZO?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/bGNVQZO'>props.children fail!</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

React.Children

<iframe height="600" style="width: 150%;" scrolling="no" title="React.Children" src="https://codepen.io/sapetti/embed/NWPxdxX?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/NWPxdxX'>React.Children</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

API React.Children

* map
* count
* forEach (como map pero devuelve un array)
* toArray (para ordenación)
* only (forzar que solo se pueda poner un hijo)

=====

## Estilos

* Hay distintas formas de aplicar estilos
* No hay una que predomine sobre las otras
* Todas tienen pros y contras

_____

### Estilos en línea

* Pasar los estilos al atributo **style**
* Los estilos deben pasarse como un objeto
* Las nombres de las propiedades son __camelCase__ (font-weight -> fontWeight)

_____

<iframe height="600" style="width: 100%;" scrolling="no" title="Inline style" src="https://codepen.io/sapetti/embed/povjOme?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/povjOme'>Inline style</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

Podemos extraer los estilos a un objeto

<iframe height="500" style="width: 100%;" scrolling="no" title="Inline style object" src="https://codepen.io/sapetti/embed/yLyYRaz?height=500&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/yLyYRaz'>Inline style object</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

### CSS-in-JS

* Escribir CSS usando JS
* Utilizando librerías como:
  * [glamorous](https://glamorous.rocks/)
  * [styled-components](https://www.styled-components.com/)
  * [Emotion](https://emotion.sh/docs/introduction)

_____

#### styled-components

<iframe height="500" style="width: 100%;" scrolling="no" title="CSS-in-JS" src="https://codepen.io/sapetti/embed/LYEpXQb?height=500&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/LYEpXQb'>CSS-in-JS</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<sub>[Plantillas de cadena de texto con postprocesador](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/template_strings)</sub>

_____

### Hojas de estilo CSS

* Importamos el fichero CSS de estilos directamente
* Se puede importar una hoja de estilos en el raíz de la aplicación para aplicar a todos

![](../images/import-css.png)

_____

* O podemos importar una hoja de estilo por componente 
  
  ![](../images/css-by-component.png)

_____

### className

* **class** es una palabra reservada
* En su lugar usaremos className
* React nos advierte si no lo cumplimos

![](../images/warningClass.png)

_____

<iframe height="600" style="width: 100%;" scrolling="no" title="className" src="https://codepen.io/sapetti/embed/oNgjaor?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/oNgjaor'>className</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

=====

## Patrones de diseño

### Higher Order Components

* Función que recibe un componente y devuelve un nuevo componente
* Se envuelve el componente que se recibe con una funcionalidad
* Se usa en librerías como Redux o Relay

_____

<iframe height="650" style="width: 100%;" scrolling="no" title="HOC" src="https://codepen.io/sapetti/embed/ExaWxxg?height=650&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/ExaWxxg'>HOC</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

_____

### Render Props

* Un attributo que recibe una función que devuelve un elemento
* El elemento con la Render Prop se encargará de llamar a la función
* No se tiene porque llamar render, pero es algo común
* Se usa en librerías como React Router

_____

<iframe height="600" style="width: 100%;" scrolling="no" title="Render Props" src="https://codepen.io/sapetti/embed/eYmVZzm?height=600&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/sapetti/pen/eYmVZzm'>Render Props</a> by Cesar Sapetti
  (<a href='https://codepen.io/sapetti'>@sapetti</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

=====

## Fragmentos




* [Contexto](https://es.reactjs.org/docs/context.html)
* Error boundaries
* [Lazy/Suspense](https://es.reactjs.org/docs/code-splitting.html)
* Portals
* Hooks
* PureComponent
* React.memo
* [React.lazy](https://es.reactjs.org/blog/2018/10/23/react-v-16-6.html#reactlazy-code-splitting-with-suspense)
* [StrictMode](https://es.reactjs.org/docs/strict-mode.html)
* Webpack – Conceptos básicos
* create-react-app
* Extensiones VS Code
* [React Developer Tools](https://es.reactjs.org/docs/optimizing-performance.html#virtualize-long-lists)
