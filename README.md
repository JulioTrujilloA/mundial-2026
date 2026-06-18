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

## Restaurar en otra máquina

El proyecto es 100 % estático y autocontenido: todo lo necesario para la app está versionado en Git. Para restaurarlo basta con clonar:

```bash
git clone https://github.com/JulioTrujilloA/mundial-2026.git
cd mundial-2026
# Abre index.html, o sírvelo por HTTP para la PWA (ver "Uso local")
```

**No hay archivos no versionados que necesites copiar de vuelta para que la app funcione.** No usa `.env`, base de datos local ni uploads. El progreso del usuario (marcadores, bracket, pestaña activa) vive en el `localStorage` de cada navegador, no en la carpeta.

Lo único que queda fuera de Git es la carpeta `.claude/` (config local de Claude Code: preview y permisos). Es opcional y no afecta a la app; si la quieres conservar, hay una copia en `Downloads/respaldo-mundial-2026-<fecha>/`.

> Los datos de grupos, fechas y sedes se basan en información pública del torneo; conviene contrastarlos con el bracket oficial de la FIFA.
