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
