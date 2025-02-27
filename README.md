# Auditoría de la accesibilidad de la web de restaurante

## Contenido de la página web

- **index.html**
  En este apartado se encuentra:
  - Una explicación del restaurante.
  - Un formulario para que los clientes puedan reservar.
  - Una forma de llegar a ver la carta del plato específico que deseas.
  - Cómo se pueden comunicar con nosotros.
  

- **menu.html**
  En este apartado se encuentra:
  - La carta del restaurante.
  - Varios enlaces que nos permiten volver atrás.
  - Un apartado con la localidad del local y cómo se pueden comunicar con nosotros.


- **style.css**
  Donde se encuentran los estilos de la web.

---

## Accesibilidad index.html

### Correcciones que debemos realizar para que la web sea más accesible

#### ❌ Los colores de fondo y de primer plano no tienen una relación de contraste adecuada

**Problema:** En varias zonas del documento, había contrastes de un color gris oscuro con otro gris un poco más claro, lo que puede dificultar la lectura.

**Solución:** Para solucionar este problema, he realizado dos cambios principales en varios lugares del código:

- `text-light`: Este es una modificación de bootstrap que pone el texto de color claro (blanco) lo he añadido al código, en el título de “Carta”, ya que está en un fondo gris oscuro, y antes el color que había, era muy oscuro, ara el gris.

```html
<h1 class="text-center pb-3 text-light">Carta</h1>
```

- `text-secondary`: Este lo he cambiado (en el footer) por una clase que pudiera modificar en el CSS, ya que los colores de Bootstrap no me convencían, ya que eran o muy oscuras, o se parecía al color que ya tenía para identificar la información que iba a añadir.

```html
<div class="col-md-6 p-5">
  <p>Dirección - <span class="contact">Carrer d'Enric Alzamora 3, 07002 Palma de Mallorca, Mallorca, España</span></p>
  <iframe src="https://www.google.com/maps/embed?pb=..." 
          title="Mapa de la ubicación de Hungry Gastro" 
          width="300" height="250" 
          style="border:0;" 
          allowfullscreen="" 
          loading="lazy"></iframe>
</div>
<div class="col-md-6 p-5">
  <div class="mb-3">
    <h3>Contacto</h3>
    <p>Teléfono: <span class="contact">+34 123 456 789</span></p>
    <p>Email: <span class="contact">info@hungrygastro.com</span></p>
    <p>Síguenos en nuestras redes sociales:</p>
  </div>
</div>
```


#### ❌ Los elementos `<frame>` o `<iframe>` no tienen título

**Problema:** En el footer, había puesto un `<iframe>` con la ubicación del restaurante de Google Maps, pero no le había dado un título, haciéndolo menos accesible, ya que podría ser complicado de identificar.

**Solución:** Vamos al `<iframe>` y le ponemos un apartado para el título:

```html
<iframe src="https://www.google.com/maps/embed?pb=..." 
        title="Mapa de la ubicación de Hungry Gastro" 
        width="300" height="250" 
        style="border:0;" 
        allowfullscreen="" 
        loading="lazy">
</iframe>
```

#### ❌ Los elementos de encabezado no aparecen en orden secuencial descendente

**Problema:** Esto ocurre porque he puesto etiquetas `<h_>` sin orden secuencial, es decir, por ejemplo, en partes del código pasaba de un `<h1>` a un `<h5>`, saltándome el `<h2>`, `<h3>`, `<h4>`, y eso no sería correcto.

**Solución:** Para solucionarlo he cambiado los títulos `<h_>` que eran mayores por los que correspondían secuencialmente. Si luego quería editar el tamaño, lo hacía con una clase CSS.

---

### Elementos que se comprueban manualmente

Los siguientes puntos los he comprobado manualmente, si he visto que los tengo correctos, les pongo un check ✅, si por el contrario, están mal, pondré una cruz ❌, y explicaré el problema y la solución que le he dado

- ✅ **Interactive controls are keyboard focusable:** Los controles interactivos, como botones, enlaces, etc., deben ser accesibles utilizando el teclado.
- ✅ **The page has a logical tab order:** Al navegar con la tecla Tab, los elementos deben enfocarse en un orden lógico.
- ✅ **Visual order on the page follows DOM order:** El orden en que los elementos aparecen visualmente en la página debe coincidir con el orden en el DOM (Document Object Model).
- ✅ **User focus is not accidentally trapped in a region:** Los usuarios deben poder navegar libremente por todo el contenido utilizando el teclado, sin quedar atrapado en una sección específica de la página, como en un modal o formulario.
- ✅ **HTML5 landmark elements are used to improve navigation:** La implementación de elementos de referencia de HTML5, como `<header>`, `<nav>`, `<main>` y `<footer>`, mejora la estructura semántica de la página y facilita la navegación.

---

### Puntos de la auditoría aprobados

- ✅ `[aria-hidden="true"]` no se encuentra en el documento `<body>`.
- ✅ Los botones tienen nombres accesibles.
- ✅ Los elementos de imagen tienen atributos `[alt]`.
- ✅ `[user-scalable="no"]` no se utiliza en el elemento `<meta name="viewport">` y el valor del atributo `[maximum-scale]` no es inferior a 5.
- ✅ El documento tiene un elemento `<title>`.
- ✅ El elemento `<html>` tiene un atributo `[lang]`.
- ✅ El atributo `[lang]` del elemento `<html>` tiene un valor válido.
- ✅ Los elementos de formulario tienen etiquetas asociadas.
- ✅ Los enlaces tienen nombres reconocibles.
- ✅ Las listas contienen únicamente elementos `<li>` y elementos que admiten secuencias de comandos (`<script>` y `<template>`).
- ✅ Los elementos de lista (`<li>`) están incluidos dentro de elementos superiores `<ul>`, `<ol>` o `<menu>`.
- ✅ Los elementos `<select>` tienen elementos `<label>` asociados.
- ✅ Las áreas táctiles deben tener un tamaño y un espaciado suficientes.
- ✅ Los elementos de imagen no tienen atributos `[alt]` que sean texto redundante.

### Puntos que no se aplican

- 🤷🏽‍♀️ Los valores de `[accesskey]` son únicos.
- 🤷🏽‍♀️ Los atributos `[aria-*]` coinciden con sus funciones.
- 🤷🏽‍♀️ Usa roles de ARIA solo en elementos compatibles.
- 🤷🏽‍♀️ Los elementos `button`, `link` y `menuitem` tienen nombres accesibles.
- 🤷🏽‍♀️ Los atributos ARIA se usan como se especifica para la función del elemento.
- 🤷🏽‍♀️ No se han usado roles de ARIA obsoletos.
- 🤷🏽‍♀️ Los elementos con `role="dialog"` o `role="alertdialog"` tienen nombres accesibles.
- 🤷🏽‍♀️ Los elementos `[aria-hidden="true"]` no contienen ningún elemento inferior seleccionable.
- 🤷🏽‍♀️ Los campos de entrada ARIA tienen nombres accesibles.
- 🤷🏽‍♀️ Los elementos `meter` de ARIA tienen nombres accesibles.
- 🤷🏽‍♀️ Los elementos `progressbar` de ARIA tienen nombres accesibles.
- 🤷🏽‍♀️ Los elementos solo usan atributos ARIA permitidos.
- 🤷🏽‍♀️ Todos los elementos `[role]` tienen los atributos `[aria-*]` obligatorios.
- 🤷🏽‍♀️ Los elementos con un `[role]` ARIA que requieren que los elementos secundarios contengan un `[role]` específico tienen todos los elementos secundarios necesarios.
- 🤷🏽‍♀️ Los atributos `[role]` están incluidos en los elementos principales correspondientes.
- 🤷🏽‍♀️ Los valores de `[role]` son válidos.
- 🤷🏽‍♀️ Los elementos con el atributo `role=text` no tienen descendientes enfocables.
- 🤷🏽‍♀️ Los campos de interruptores ARIA tienen nombres accesibles.
- 🤷🏽‍♀️ Los elementos `tooltip` de ARIA tienen nombres accesibles.
- 🤷🏽‍♀️ Los elementos `treeitem` de ARIA tienen nombres accesibles.
- 🤷🏽‍♀️ Los atributos `[aria-*]` tienen valores válidos.
- 🤷🏽‍♀️ Los atributos `[aria-*]` son válidos y están bien escritos.
- 🤷🏽‍♀️ La página contiene un encabezado, un enlace de omisión o una región de punto de referencia.
- 🤷🏽‍♀️ Los elementos `<dl>` contienen únicamente grupos de `<dt>` y `<dd>` o elementos `<script>`, `<template>` o `<div>` ordenados correctamente.
- 🤷🏽‍♀️ Los elementos de la lista de definiciones están incluidos dentro de elementos `<dl>`.
- 🤷🏽‍♀️ Los ID de ARIA son únicos.
- 🤷🏽‍♀️ Ningún campo de formulario tiene varias etiquetas.
- 🤷🏽‍♀️ El elemento `<html>` tiene un atributo `[xml:lang]` con el mismo idioma base que el atributo `[lang]`.
- 🤷🏽‍♀️ Los botones de entrada tienen texto reconocible.
- 🤷🏽‍♀️ Los elementos `<input type="image">` tienen texto `[alt]`.
- 🤷🏽‍♀️ Los enlaces se distinguen sin depender del color.
- 🤷🏽‍♀️ El documento no usa `<meta http-equiv="refresh">`.
- 🤷🏽‍♀️ Los elementos `<object>` tienen texto alternativo.
- 🤷🏽‍♀️ Los enlaces de salto son enfocables.
- 🤷🏽‍♀️ No hay ningún elemento con un valor de `[tabindex]` superior a 0.
- 🤷🏽‍♀️ Las tablas tienen contenido diferente en el atributo `summary` y en `<caption>`.
- 🤷🏽‍♀️ Las celdas de un elemento `<table>` que usan el atributo `[headers]` hacen referencia a otras celdas de la misma tabla.
- 🤷🏽‍♀️ Los elementos `<th>` y los elementos con atributos `[role="columnheader"/"rowheader"]` contienen las celdas de datos que describen.
- 🤷🏽‍♀️ Los atributos `[lang]` tienen un valor válido.
- 🤷🏽‍♀️ Los elementos `<video>` contienen un elemento `<track>` con el atributo `[kind="captions"]`.

---

## Accesibilidad menu.html

### Correcciones que debemos realizar para que la web sea más accesible

#### ❌ Los colores de fondo y de primer plano no tienen una relación de contraste adecuada

**Problema:** En varias zonas del documento, había contrastes de un color gris oscuro con otro gris un poco más claro, lo que puede dificultar la lectura.

**Solución:** Para solucionar este problema, he realizado dos cambios principales en varios lugares del código:

- `text-light`: En este documento, lo añadimos cuando ponemos el título de cada apartado de la carta (“Entrantes”, “Platos principales”, “Guarniciones”, etc.). Ejemplo:

```html
<h1 class="text-center pb-3 text-light">Entrantes</h1>
```

- `text-secondary`: Este lo he cambiado (en el footer) por una clase que pudiera modificar en el CSS, ya que los colores de Bootstrap no me convencían, ya que eran o muy oscuras, o se parecía al color que ya tenía para identificar la información que iba a añadir.

```html
<div class="col-md-6 p-5">
  <p>Dirección - <span class="contact">Carrer d'Enric Alzamora 3, 07002 Palma de Mallorca, Mallorca, España</span></p>
  <iframe src="https://www.google.com/maps/embed?pb=..." 
          title="Mapa de la ubicación de Hungry Gastro" 
          width="300" height="250" 
          style="border:0;" 
          allowfullscreen="" 
          loading="lazy"></iframe>
</div>
<div class="col-md-6 p-5">
  <div class="mb-3">
    <h3>Contacto</h3>
    <p>Teléfono: <span class="contact">+34 123 456 789</span></p>
    <p>Email: <span class="contact">info@hungrygastro.com</span></p>
    <p>Síguenos en nuestras redes sociales:</p>
  </div>
</div>
```

#### ❌ Los elementos `<frame>` o `<iframe>` no tienen título

**Problema:** En el footer, había puesto un `<iframe>` con la ubicación del restaurante de Google Maps, pero no le había dado un título, haciéndolo menos accesible.

**Solución:** Vamos al `<iframe>` y le ponemos un apartado para el título:

```html
<iframe src="https://www.google.com/maps/embed?pb=..." 
        title="Mapa de la ubicación de Hungry Gastro" 
        width="300" height="250" 
        style="border:0;" 
        allowfullscreen="" 
        loading="lazy">
</iframe>
```

---

### Elementos comprobados manualmente

Los siguientes puntos los he comprobado manualmente, si he visto que los tengo correctos, les pongo un check ✅, si por el contrario, están mal, pondré una cruz ❌, y explicaré el problema y la solución que le he dado

- ✅ **Interactive controls are keyboard focusable:** Los controles interactivos, como botones, enlaces, etc., deben ser accesibles utilizando el teclado.
- ✅ **The page has a logical tab order:** Al navegar con la tecla Tab, los elementos deben enfocarse en un orden lógico.
- ✅ **Visual order on the page follows DOM order:** El orden en que los elementos aparecen visualmente en la página debe coincidir con el orden en el DOM (Document Object Model).
- ✅ **User focus is not accidentally trapped in a region:** Los usuarios deben poder navegar libremente por todo el contenido utilizando el teclado, sin quedar atrapado en una sección específica de la página, como en un modal o formulario.
- ✅ **HTML5 landmark elements are used to improve navigation:** La implementación de elementos de referencia de HTML5, como `<header>`, `<nav>`, `<main>` y `<footer>`, mejora la estructura semántica de la página y facilita la navegación.

---

### Puntos de la auditoría aprobados

- ✅ `[aria-hidden="true"]` no se encuentra en el documento `<body>`.
- ✅ Los elementos de imagen tienen atributos `[alt]`.
- ✅ `[user-scalable="no"]` no se utiliza en el elemento `<meta name="viewport">`.
- ✅ El documento tiene un elemento `<title>`.
- ✅ El elemento `<html>` tiene un atributo `[lang]`.
- ✅ El atributo `[lang]` tiene valores válidos.
- ✅ Los enlaces tienen nombres reconocibles.
- ✅ Las listas contienen únicamente elementos `<li>` y elementos compatibles.
- ✅ Las áreas táctiles tienen tamaño suficiente.
- ✅ Los elementos de imagen no tienen atributos `[alt]` redundantes.

## No se aplican:

- 🤷🏽‍♀️ Los valores de [accesskey] son únicos
- 🤷🏽‍♀️ Los atributos [aria-*] coinciden con sus funciones
- 🤷🏽‍♀️ Usa roles de ARIA solo en elementos compatibles
- 🤷🏽‍♀️ Los elementos button, link y menuitem tienen nombres accesibles
- 🤷🏽‍♀️ Los atributos ARIA se usan como se especifica para la función del elemento
- 🤷🏽‍♀️ No se han usado roles de ARIA obsoletos
- 🤷🏽‍♀️ Los elementos con role="dialog" o role="alertdialog" tienen nombres accesibles.
- 🤷🏽‍♀️ Los elementos [aria-hidden="true"] no contienen ningún elemento inferior seleccionable
- 🤷🏽‍♀️ Los campos de entrada ARIA tienen nombres accesibles
- 🤷🏽‍♀️ Los elementos meter de ARIA tienen nombres accesibles
- 🤷🏽‍♀️ Los elementos progressbar de ARIA tienen nombres accesibles
- 🤷🏽‍♀️ Los elementos solo usan atributos ARIA permitidos
- 🤷🏽‍♀️ Todos los elementos [role] tienen los atributos [aria-*] obligatorios
- 🤷🏽‍♀️ Los elementos con un [role] ARIA que requieren que los elementos secundarios contengan un [role] específico tienen todos los elementos secundarios necesarios.
- 🤷🏽‍♀️ Los atributos [role] están incluidos en los elementos principales correspondientes
- 🤷🏽‍♀️ Los valores de [role] son válidos
- 🤷🏽‍♀️ Los elementos con el atributo role=text no tienen descendientes enfocables.
- 🤷🏽‍♀️ Los campos de interruptores ARIA tienen nombres accesibles
- 🤷🏽‍♀️ Los elementos tooltip de ARIA tienen nombres accesibles
- 🤷🏽‍♀️ Los elementos treeitem de ARIA tienen nombres accesibles
- 🤷🏽‍♀️ Los atributos [aria-*] tienen valores válidos
- 🤷🏽‍♀️ Los atributos [aria-*] son válidos y están bien escritos
- 🤷🏽‍♀️ Los botones tienen nombres accesibles
- 🤷🏽‍♀️ La página contiene un encabezado, un enlace de omisión o una región de punto de referencia
- 🤷🏽‍♀️ Los elementos `<dl>` contienen únicamente grupos de `<dt>` y `<dd>` o elementos `<script>`, `<template>` o `<div>` ordenados correctamente.
- 🤷🏽‍♀️ Los elementos de la lista de definiciones están incluidos dentro de elementos `<dl>`
- 🤷🏽‍♀️ Los ID de ARIA son únicos
- 🤷🏽‍♀️ Ningún campo de formulario tiene varias etiquetas
- 🤷🏽‍♀️ El elemento `<html>` tiene un atributo [xml:lang] con el mismo idioma base que el atributo [lang].
- 🤷🏽‍♀️ Los botones de entrada tienen texto reconocible.
- 🤷🏽‍♀️ Los elementos `<input type="image">` tienen texto [alt]
- 🤷🏽‍♀️ Los elementos de formulario tienen etiquetas asociadas
- 🤷🏽‍♀️ Los enlaces se distinguen sin depender del color.
- 🤷🏽‍♀️ El documento no usa `<meta http-equiv="refresh">`
- 🤷🏽‍♀️ Los elementos `<object>` tienen texto alternativo
- 🤷🏽‍♀️ Los elementos `<select>` tienen elementos `<label>` asociados.
- 🤷🏽‍♀️ Los enlaces de salto son enfocables.
- 🤷🏽‍♀️ No hay ningún elemento con un valor de [tabindex] superior a 0
- 🤷🏽‍♀️ Las tablas tienen contenido diferente en el atributo summary y en `<caption>`.
- 🤷🏽‍♀️ Las celdas de un elemento `<table>` que usan el atributo [headers] hacen referencia a otras celdas de la misma tabla.
- 🤷🏽‍♀️ Los elementos `<th>` y los elementos con atributos [role="columnheader"/"rowheader"] contienen las celdas de datos que describen.
- 🤷🏽‍♀️ Los atributos [lang] tienen un valor válido
- 🤷🏽‍♀️ Los elementos `<video>` contienen un elemento `<track>` con el atributo [kind="captions"]
