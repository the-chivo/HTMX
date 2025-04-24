# Que es HTMX
HTMX es una biblioteca JavaScript que permite hacer peticiones HTTP dinámicas directamente desde el HTML, sin tener que escribir JavaScript.
HTMX le brinda acceso a AJAX , transiciones CSS , WebSockets y eventos enviados por el servidor directamente en HTML, 
utilizando atributos , para que pueda crear interfaces de usuario modernas con la simplicidad y el poder del hipertexto.

# Como usar HTMX

### Atraves de CDN

Añade lo siguiente a tu tag principal y enpieza:

`<script src="https://unpkg.com/htmx.org@2.0.4" integrity="sha384-HGfztofotfshcF7+8n44JQL2oJmowVChPTg48S+jvZoztPfvwD79OC/LTtG6dMp+" crossorigin="anonymous"></script>`
`
### Version sin minimizar 

`<script src="https://unpkg.com/htmx.org@2.0.4/dist/htmx.js" integrity="sha384-oeUn82QNXPuVkGCkcrInrS1twIxKhkZiFfr2TdiuObZ3n3yIeMiqcRzkIcguaof1" crossorigin="anonymous"></script>`

### Atraves de npm 

`npm install htmx.org@2.0.4`

# Atributos principales

Realiza una petición GET al servidor: `hx-get`
Realiza una petición POST: `hx-post`
Realiza una petición PUT: `hx-put`
Realiza una petición DELETE: `hx-delete`
Elemento que sera actualizado con la respuesta: `hx-target`
Define como insertar el contenido en el DOM: `hx-swap`
Evento que activa la peticion: `hx-trigger`
Muestra poppup de confirmación antes de ejecutar: `hx-confirm`
Incluye otros datos adicionales en la petición: `hx-include`
Convierte enlaces y formularios en AJAX automáticos: `hx-boost`
Añade valores extra desde JS o JSON: `hx-vals`
Actualiza la url del navegador: `hx-push-url`
Solo usa una parte del HTML devuelto: `hx-select`
Usa extensiones: `hx-ext`
Agrega cabeceras HTTP personalizadas: `hx-headers`

# Algunos ejemplos utiles

### hx-target
<pre> ```html hx-target="#contenedor" hx-target="this" hx-target="closest .clase" ``` </pre>



