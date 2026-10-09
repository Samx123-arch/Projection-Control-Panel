# Projection Control Panel

Panel web en HTML para acceder rápidamente a las interfaces del proyecto de projection mapping desde un solo lugar.

## Características

- Diseño oscuro y adaptable a distintos tamaños de pantalla.
- Tarjetas con nombre y descripción de cada herramienta.
- Botón para abrir cada ruta en una pestaña nueva.
- Botón para copiar la URL al portapapeles.
- Favicon personalizado en la pestaña del navegador.

## Páginas incluidas

El panel apunta al servidor local `http://127.0.0.1:8000`.

| Página | URL | Descripción |
|---|---|---|
| Final Scene | `http://127.0.0.1:8000/` | Escena final, ideal para mostrar a pantalla completa en el proyector. |
| Editor | `http://127.0.0.1:8000/editor` | Crear polígonos, vincular dispositivos y configurar la lógica. |
| Projection Editor | `http://127.0.0.1:8000/editor/projection` | Réplica editable 1:1 de la escena para ajustar formas a escala de proyección. |
| Style | `http://127.0.0.1:8000/style` | Modificar la apariencia de los objetos. |
| Style Preview | `http://127.0.0.1:8000/style/preview` | Vista previa de la escena que registra los clics en la página y la consola. |
| Tune | `http://127.0.0.1:8000/tune` | Ajustar efectos, colores y velocidad por objeto. |
| Text Projector | `http://127.0.0.1:8000/text` | Mostrar texto a pantalla completa. |
| Text Editor | `http://127.0.0.1:8000/text/editor` | Controlar el contenido de la página `/text`. |
| Align | `http://127.0.0.1:8000/align` | Ajustar la posición de polígonos rastreados; pensado para rigs con motores stepper. |

## Archivos

Estructura recomendada:

```text
Projection Control Panel/
├── index.html
├── logo.png
└── favicon.ico   # opcional, si se usa un favicon .ico
```

- `index.html`: contiene el panel, los estilos CSS y el JavaScript de los botones.
- `logo.png`: icono que se muestra en la pestaña si se configura como favicon.
- `favicon.ico`: alternativa para el icono de la pestaña.

Los nombres de los archivos pueden cambiar, pero las rutas dentro del HTML deben coincidir con los nombres reales.

## Requisitos

1. Un navegador moderno.
2. El servidor del proyecto ejecutándose en `http://127.0.0.1:8000` para que las rutas de destino estén disponibles.
3. Los archivos de imagen del favicon colocados donde el HTML pueda encontrarlos.

El panel puede abrirse directamente haciendo doble clic en `index.html`. No necesita un servidor propio, aunque el servidor del proyecto sí debe estar encendido para abrir las interfaces listadas.

## Cómo funciona

El panel define una URL base:

```javascript
const BASE_URL = "http://127.0.0.1:8000";
```

El botón **Abrir** combina esa dirección con la ruta de la tarjeta y la abre en una pestaña nueva:

```javascript
function openPage(path) {
    window.open(BASE_URL + path, "_blank");
}
```

El botón **Copiar** copia la URL completa. Esta función utiliza la API del portapapeles del navegador, por lo que puede depender de los permisos y del contexto de seguridad del navegador.

## Flujo de trabajo sugerido

- **Monitor del ordenador:** utiliza `/editor`, `/editor/projection`, `/style`, `/style/preview`, `/tune`, `/text/editor` y `/align`.
- **Proyector:** utiliza `/` para la escena final o `/text` para proyectar texto.

El panel es solo un lanzador de enlaces: no inicia el servidor ni modifica por sí mismo la lógica de las páginas del proyecto.
