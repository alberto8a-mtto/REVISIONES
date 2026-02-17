# Agenda Inspecciones Vehiculares — Proyección para TV

Esta página muestra la agenda diaria desde Google Sheets y está preparada para funcionar en GitHub Pages sin errores de CORS.

## Archivos

- `index.html`: interfaz y lógica de carga de datos.
- `logo.png`: logo de la empresa (debe existir con ese nombre).

## Cómo funciona

- La carga usa `Google Visualization (gviz)` con `JSONP`.
- Este método evita el problema típico de `fetch` + `export?format=csv` en hosting estático.
- Refresca datos cada 30 segundos.
- Permite filtrar “solo hoy”.

## Configuración de la hoja

1. En Google Sheets, verifica que la hoja sea visible para lectura (`Cualquiera con el enlace puede ver`).
2. Si no carga, usa **Archivo > Compartir > Publicar en la web** para la pestaña usada en TV.
3. En `index.html`, actualiza estas constantes si cambias de hoja:
  - `SPREADSHEET_ID` (actual: `1CqvY7dnSdw6jT8vL7In-NqXnVTydo_wRa0egA5I0CwA`)
  - `SHEET_GID` (actual: `0`)

## Encabezados esperados

La primera fila debe incluir, idealmente:

`TIPO, FECHA, EMPRESA, VEHICULO, HORA INICIO, HORA FINAL, COORDINADOR, RESULTADO`

También acepta variantes como `VEHÍCULO` y `HORA FIN`.

## Ejecutar en red local

En Windows (PowerShell), desde esta carpeta:

```powershell
python -m http.server 8000
```

Luego abre en el TV: `http://IP_DEL_PC:8000`

## Publicar en GitHub Pages

Sube este directorio al repo y activa Pages. Al abrir la URL pública, la agenda debería cargar sin bloquearse por CORS.