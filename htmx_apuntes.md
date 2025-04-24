# ¿Qué es HTMX?

HTMX es una biblioteca JavaScript que permite hacer peticiones HTTP dinámicas directamente desde el HTML, sin tener que escribir JavaScript.

HTMX le brinda acceso a AJAX, transiciones CSS, WebSockets y eventos enviados por el servidor directamente en HTML utilizando atributos, para que puedas crear interfaces de usuario modernas con la simplicidad y el poder del hipertexto.

---

# ¿Cómo usar HTMX?

### A través de CDN

Añade lo siguiente dentro del `<head>` o al final del `<body>`:

```html
<script src="https://unpkg.com/htmx.org@2.0.4" integrity="sha384-HGfztofotfshcF7+8n44JQL2oJmowVChPTg48S+jvZoztPfvwD79OC/LTtG6dMp+" crossorigin="anonymous"></script>
```

### Versión sin minimizar

```html
<script src="https://unpkg.com/htmx.org@2.0.4/dist/htmx.js" integrity="sha384-oeUn82QNXPuVkGCkcrInrS1twIxKhkZiFfr2TdiuObZ3n3yIeMiqcRzkIcguaof1" crossorigin="anonymous"></script>
```

### A través de npm

```bash
npm install htmx.org@2.0.4
```

---

# Atributos principales

- `hx-get`: Realiza una petición GET al servidor  
- `hx-post`: Realiza una petición POST  
- `hx-put`: Realiza una petición PUT  
- `hx-delete`: Realiza una petición DELETE  
- `hx-target`: Elemento que será actualizado con la respuesta  
- `hx-swap`: Define cómo insertar el contenido en el DOM  
- `hx-trigger`: Evento que activa la petición  
- `hx-confirm`: Muestra un popup de confirmación antes de ejecutar  
- `hx-include`: Incluye otros datos adicionales en la petición  
- `hx-boost`: Convierte enlaces y formularios en AJAX automáticos  
- `hx-vals`: Añade valores extra desde JS o JSON  
- `hx-push-url`: Actualiza la URL del navegador  
- `hx-select`: Solo usa una parte del HTML devuelto  
- `hx-ext`: Usa extensiones  
- `hx-headers`: Agrega cabeceras HTTP personalizadas  

---

# Algunos ejemplos útiles

### `hx-target`

```html
hx-target="#contenedor"
hx-target="this"
hx-target="closest .clase"
```
### `hx-swap`: insertar la respuesta

```html
hx-swap="innerHTML"     <!-- (default) Reemplaza contenido interno -->
hx-swap="outerHTML"     <!-- Reemplaza el elemento completo -->
hx-swap="beforebegin"`  <!-- Inserta antes del elemento -->
hx-swap="afterbegin"`   <!-- Inserta como primer hijo -->
hx-swap="beforeend"`    <!-- Inserta como último hijo -->
hx-swap="afterend"`     <!-- Inserta después del elemento -->
hx-swap="none"`         <!-- No actualiza nada -->
```
#### Tambien se pueden controlar las transiciones:
`hx-swap="outerHTML transition:true swap:1s settle:500ms"`

### `hx-swap`: cuando disparar la petición

```html
hx-trigger="click"
hx-trigger="change"
hx-trigger="submit"
hx-trigger="every 5s"
hx-trigger="load"
hx-trigger="keyup delay:500ms"
hx-trigger="revealed" <!-- cuando el elemento entra en viewport -->
```
### Algunos modificadores interesantes:

- `once`: Solo una vez
- `changued` Solo si cambia el valor
- `delay:500ms`: espera la cantidad de tiempo definida antes de disparar(en este caso 500ms)

### hx-confirm

Muestra un mensaje antes de realizar una acción: 
```html
<button hx-post="/borrar" hx-confirm="¿Estás seguro?">Borrar</button>
```
# Formularios con htmx
```html
<form hx-post="/procesar" hx-target="#resultado" hx-swap="outerHTML">
  <input name="nombre">
  <button type="submit">Enviar</button>
</form>

<div id="resultado"></div>
```

# Incluir datos adicionales
 - `hx-include`: Permite incluir otros campos
 ```html
 <form>
  <input name="email">
  <input id="oculto" name="token" value="abc123">
  <button hx-post="/api" hx-include="#oculto">Enviar</button>
</form>
 ```
 - `hx-vals`: Agrega datos extra directamente
 ```html
 <button hx-post="/api" hx-vals='{"clave": "valor"}'>Guardar</button>
```
- `hx-select`: Solo renderiza parte del html devuelto:
```html
<div hx-get="/info" hx-select="#solo-esto" hx-target="#destino"></div>
```
# Navegacion y estado

- `hx-push`: Modifica el historial del navegador:
```html
<a hx-get="/pagina2" hx-push-url="true" hx-target="#main">Ir</a>
```
# Eventos emitidos por HTMX

Puedes enganchar JS personalizando con estos eventos:

- `htmx:configRequest`: Ocurre antes de enviar la petición
- `htmx:beforeRequest`: Ocurre justo antes del envio
- `htmx:afterRequest`: Ocurre despues de completarla
- `htmx:beforeSwap`: Ocurre antes de insertar HTML
- `htmx:afterSwap`: Ocurre despues de insertar HTML
- `htmx:responseError`: Ocurre si hay un error en la respuesta
- `htmx:error`: Ocurre si hay cualquier error en la operación
- `htmx:load`: Cada vez que se carga un fragmento nuevo

#### Ejemplo:
```js
document.body.addEventListener("htmx:afterSwap", (e) => {
  console.log("Se actualizó algo con HTMX");
});
```
# Extensiones

### WebSockets:
```html
<script src="https://unpkg.com/htmx.org/dist/ext/ws.js"></script>

<div hx-ext="ws" ws-connect="/stream"></div>
```
### SSE
```html
<div hx-get="/notificaciones" hx-trigger="sse:mensaje" hx-swap="beforeend"></div>
```
