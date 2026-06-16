# Mundial 2026 ⚽

App web interactiva de la Copa Mundial de la FIFA 2026 (Canadá · México · EE. UU.). Una sola página, sin dependencias ni build: HTML, CSS y JavaScript puro.

## Funciones

Tres pestañas: **Grupos**, **Partidos** y **Eliminatorias**.

- **Grupos** — cada grupo muestra su tabla de posiciones (PJ, PG, PE, PP, GF, GC, DG, Pts) calculada automáticamente desde los marcadores —con los 8 mejores terceros— y debajo sus partidos con horarios en la hora local de quien abre la app. Colores por confederación.
- **Partidos** — los 104 encuentros; escribe los marcadores de fase de grupos y la tabla se actualiza sola. Horarios de saque en hora local.
- **Eliminatorias** — cuadro en doble pirámide (de fase de grupos a la final + 3er lugar) con:
  - En escritorio: arrastrar y soltar selecciones (validación de grupo/posición en Ronda de 32, sin duplicados por ronda). En celular: selección por toque con candidatos válidos.
  - Líneas conectoras que iluminan la ruta de un equipo hasta la final.
  - Botón **Simular** (proyección por ranking FIFA) y modo compacto.
- **Resultados reales** — botón que consulta la API pública de ESPN y rellena marcadores y clasificados.
- **PWA** — instalable en el celular y con soporte offline.

Todo el progreso (marcadores, bracket, pestaña activa) se guarda en el navegador con `localStorage`. La carpeta es portátil: todas las rutas son relativas, así que puedes moverla o renombrarla sin romper nada (el repositorio Git se mueve con ella).

## Uso local

Abre `index.html` en el navegador. Para la versión instalable (PWA) sírvelo por HTTP:

```bash
python -m http.server 8765
# luego abre http://localhost:8765
```

## Publicar

Arrastra la carpeta a [Netlify Drop](https://app.netlify.com/drop) o publícala con GitHub Pages / Cloudflare Pages.

## Archivos

| Archivo | Descripción |
|---|---|
| `index.html` | La app completa (HTML + CSS + JS) |
| `manifest.json` | Metadatos PWA |
| `sw.js` | Service worker (caché offline) |
| `icon.svg` | Ícono de la app |

> Los datos de grupos, fechas y sedes se basan en información pública del torneo; conviene contrastarlos con el bracket oficial de la FIFA.
