# Vinculación de Atributos

En Vue, los bigotes solo se usan para la interpolación de texto. Para vincular un atributo a un valor dinámico, usamos la directiva `v-bind`:

```vue-html
<div v-bind:id="dynamicId"></div>
```

Una **directiva** es un atributo especial que comienza con el prefijo `v-`. Son parte de la sintaxis de la plantilla de Vue. Al igual que las interpolaciones de texto, los valores de las directivas son expresiones de JavaScript que tienen acceso al estado del componente. Los detalles completos de `v-bind` y la sintaxis de directivas se analizan en <a target="_blank" href="/guide/essentials/template-syntax.html">Guía - Plantilla de sintaxis</a>.

La parte después de los dos puntos (`:id`) es el "argumento" de la directiva. Aquí, el atributo `id` del elemento se sincronizará con la propiedad `dynamicId` del estado del componente.

Debido a que `v-bind` se usa con tanta frecuencia, tiene una sintaxis abreviada dedicada:

```vue-html
<div :id="dynamicId"></div>
```

Ahora, intente agregar un enlace `clase` dinámico a `<h1>`, utilizando la propiedad de datos `titleClass` <span class="options-api"></span><span class="composition-api"> ref</span> como su valor. Si está vinculado correctamente, el texto debería volverse rojo.
