# Representación Declarativa

<div class="sfc">

Lo que ve en el editor es un componente de un solo archivo de Vue, tambien llamado Single File Component (SFC) en inglés. Un SFC es un bloque de código autónomo reutilizable que encapsula HTML, CSS y JavaScript que pertenecen juntos, escrito dentro de un archivo `.vue`.

</div>

La característica central de Vue es la **representación declarativa**: al usar una sintaxis de plantilla que extiende HTML, podemos describir cómo debería verse el HTML en función del estado de JavaScript. Cuando cambia el estado, el HTML se actualiza automáticamente.

<div class="composition-api">

Los estados que pueden desencadenar actualizaciones cuando se modifican se consideran **reactivos**. Podemos declarar el estado reactivo usando la API `reactive()` de Vue. Los objetos creados a partir de `reactive()` son JavaScript [Proxies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) que funcionan como objetos normales:

```js
import { reactive } from 'vue'

const counter = reactive({
  count: 1
})

console.log(counter.count) // 0
counter.count++
```

`reactive()` solo funciona en objetos (incluidos arreglos y tipos integrados como `Map` y `Set`). `ref()`, por otro lado, puede tomar cualquier tipo de valor y crear un objeto que expone el valor interno bajo una propiedad `.value`:

```js
import { ref } from 'vue'

const message = ref('Hello World!')

console.log(message.value) // "Hello World!"
message.value = 'Changed'
```

Los detalles sobre `reactive()` y `ref()` se analizan en <a target="_blank" href="/guide/essentials/reactivity-fundamentals.html">Guía - Fundamentos de reactividad</a>.

<div class="sfc">

El estado reactivo declarado en el bloque `<script setup>` del componente se puede usar directamente en la plantilla. Así es como podemos representar texto dinámico basado en el valor del objeto 'counter' y la referencia 'message', usando la sintaxis de bigotes:

</div>

<div class="html">

El objeto que se pasa a `createApp()` es un componente de Vue. El estado de un componente debe declararse dentro de su función `setup()` y devolverse mediante un objeto:

```js{2,5}
setup() {
  const counter = reactive({ count: 0 })
  const message = ref('Hello World!')
  return {
    counter,
    message
  }
}
```
  
Las propiedades del objeto devuelto estarán disponibles en la plantilla. Así es como podemos representar texto dinámico basado en el valor de `message`, usando la sintaxis de bigotes:

</div>

```vue-html
<h1>{{ message }}</h1>
<p>count is: {{ counter.count }}</p>
```

Observe cómo no necesitábamos usar `.value` al acceder a la referencia `message` en las plantillas: se desenvuelve automáticamente para un uso más breve.

</div>

<div class="options-api">
  
Los estados que pueden desencadenar actualizaciones cuando se modifican se consideran **reactivos**. En Vue, el estado reactivo se mantiene en los componentes. En el código de ejemplo, el objeto que se pasa a `createApp()` es un componente.

Podemos declarar el estado reactivo usando la opción del componente `data`, que debería ser una función que devuelva un objeto:

<div class="sfc">

```js{3-5}
export default {
  data() {
    return {
      message: 'Hello World!'
    }
  }
}
```

</div>
<div class="html">

```js{3-5}
createApp({
  data() {
    return {
      message: 'Hello World!'
    }
  }
})
```

</div>
  
La propiedad `message` estará disponible en la plantilla. Así es como podemos representar texto dinámico basado en el valor de `message`, usando la sintaxis de bigotes:

```vue-html
<h1>{{ message }}</h1>
```

</div>

El contenido dentro de los bigotes no se limita solo a identificadores o rutas; podemos usar cualquier expresión de JavaScript válida:

```vue-html
<h1>{{ message.split('').reverse().join('') }}</h1>
```

<div class="composition-api">

Ahora, intente crear algún estado reactivo usted mismo y utilícelo para generar contenido de texto dinámico para `<h1>` en la plantilla.

</div>

<div class="options-api">

Ahora, intente crear una propiedad de datos usted mismo y utilícela como contenido de texto para `<h1>` en la plantilla.

</div>
