# SQL DER

Skill reutilizable para crear y mejorar diagramas entidad-relación (DER) en **Mermaid**. El diseño combina bordes de neón con una cuadrícula de **3 columnas × 5 filas**. Usa 15 tablas ficticias de un sistema académico y 16 relaciones.

## Archivos

| Archivo | Contenido |
| --- | --- |
| [`SKILL.md`](SKILL.md) | Instrucciones para que un agente construya y revise relaciones nativas de Mermaid y conserve el diseño acordado. |
| [`ejemplo-der-neon.mmd`](ejemplo-der-neon.mmd) | Código completo del último ejemplo, con el diseño neón, las tablas y las relaciones nativas de `erDiagram`. |
| [`config.json`](config.json) | Copia del JSON que estaba en la pestaña **Config** de Mermaid Live Editor al guardar el ejemplo. |

## Usar como skill o prompt

- Si tu agente admite skills, carga este repositorio como una carpeta llamada `sql-der` en la ubicación de skills que use tu herramienta. La entrada es `SKILL.md`.
- Como prompt, comparte `SKILL.md` con el agente y adjunta tu esquema. Si quieres el estilo neón en cuadrícula, incluye también `ejemplo-der-neon.mmd`.

> Usa la skill sql-der con este esquema. Genera un DER en Mermaid con relaciones PK/FK, cardinalidades claras y el estilo neón del ejemplo. Dame un bloque completo para pegar en Mermaid Live Editor.

## Abrir el ejemplo

1. Abre Mermaid Live Editor. [Mermaid Live Editor](https://mermaid.live/)
2. Copia todo el contenido de `ejemplo-der-neon.mmd`, incluido el encabezado que empieza con `---`, y pégalo en **Code**.
3. Para reproducir la sesión guardada, pega `config.json` en **Config**. El archivo `.mmd` también se puede abrir dejando **Config** en `{}` porque incluye su configuración de diseño.
4. Espera a que termine el renderizado antes de ajustar el zoom. El ejemplo se verificó con el motor Mermaid **12.2.0**.

## Cómo leer las relaciones

- **PK** identifica la clave primaria. **FK** señala la clave foránea y **UK** indica que el valor debe ser único.
- Cada conexión lleva el nombre del campo FK en la tabla que referencia a la otra. Por ejemplo, `estudiante_id` une `Matriculas.estudiante_id` con `Estudiantes.id`.
- Los extremos muestran la cardinalidad. En `Estudiantes ||..o{ Matriculas`, cada matrícula pertenece a un estudiante y cada estudiante puede tener cero o muchas matrículas. En `Pagos ||..o| Recibos`, un pago puede tener cero o un recibo.
- Las tablas conservan el orden de la cuadrícula. Las relaciones cortas pasan por los espacios entre tablas y la que une **Matrículas** con **Resultados** recorre el pasillo entre columnas.

El encabezado YAML fija los colores, las posiciones y los recorridos. Si agregas o reordenas relaciones, revisa sus selectores CSS numerados para que los recorridos sigan correspondiendo con sus conexiones.

[Documentación de diagramas entidad-relación de Mermaid](https://mermaid.js.org/syntax/entityRelationshipDiagram.html)
