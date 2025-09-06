# LSB — MVP detección de mano (MediaPipe + Netlify)

Prototipo mínimo funcional para detección de mano en el navegador usando MediaPipe Hands. Incluye una heurística simple para reconocer “palma abierta” (simulando el gesto “hola”).

- 100% client‑side (privacidad: no se sube vídeo).
- Listo para desplegar en Netlify.
- Preparado para incrustar en LMS/H5P mediante iframe.

## Estructura

- `index.html` — Micro‑app principal con UI, MediaPipe Hands y heurística.
- `netlify.toml` — Configuración de Netlify (headers de permisos).
- `.gitignore` — Ignora archivos locales temporales.
- `LICENSE` — MIT.

## Requisitos

- Navegador moderno con permiso de cámara.
- Contexto seguro:
  - https:// (Netlify ya lo da) o
  - http://localhost para pruebas locales.

## Ejecutar localmente

1. Clona este repo o copia los archivos en una carpeta.
2. Inicia un servidor local (ejemplos):
   - Python 3:
     ```
     python -m http.server 8000
     ```
   - Node (http-server):
     ```
     npx http-server -p 8000
     ```
3. Abre en tu navegador:
   - http://localhost:8000

4. Pulsa “Iniciar cámara” y prueba los gestos:
   - Palma abierta → debería mostrar “¡Correcto — palma abierta!”
   - Puño o parcial → “Intenta de nuevo…”

## Despliegue en Netlify

1. Crea un repositorio en GitHub y sube estos archivos.
2. En Netlify:
   - New site → Import from Git.
   - Elige tu repo.
   - Build command: (déjalo vacío)
   - Publish directory: (raíz del repo)
3. Publica. Netlify generará una URL con HTTPS lista para usar.

El archivo `netlify.toml` añade encabezados de permisos para cámara/micrófono. Aun así, el navegador solicitará el permiso la primera vez.

## Incrustar en LMS/H5P

Puedes incluirlo con un iframe:
```html
<iframe src="https://TU-SITIO.netlify.app" width="100%" height="520" style="border:0"></iframe>