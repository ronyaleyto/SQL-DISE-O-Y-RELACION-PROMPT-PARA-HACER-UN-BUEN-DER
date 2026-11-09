---
name: sql-der
description: Crea o mejora diagramas entidad-relación nativos de Mermaid a partir de esquemas SQL, modelos ORM o listas de tablas y claves. Úsala para documentar relaciones PK/FK, aclarar cardinalidades o conservar una cuadrícula con estilo neón en Mermaid Live Editor.
---

# SQL DER

Entrega un bloque completo de Mermaid que se pueda pegar en **Code**. Integra la configuración del diagrama en su encabezado YAML y usa [config.json](config.json) cuando se pida reproducir la configuración guardada de **Config**.

## Modelo y relaciones

1. Toma las tablas, las claves y los tipos del esquema recibido. Para una demostración, usa tablas ficticias e identifícalas como ejemplo.
2. Declara las entidades y relaciones con `erDiagram`. Pon el nombre de la FK en cada línea para que se pueda localizar en la tabla que la contiene.
3. Deriva los extremos de la relación de la nulabilidad y la unicidad de la FK. En `Padre ||..o{ Hija`, cada hija requiere un padre y cada padre puede tener cero o muchas hijas. Una FK única permite como máximo una hija. Si faltan restricciones para determinar la cardinalidad, señala la suposición.
4. Respeta las tablas, las relaciones, el diseño y el orden que el usuario aprobó. Si pide un cambio visual, conserva las relaciones del esquema. Si pide un cambio del modelo, indica qué claves o relaciones cambian en el DER.

## Estilo y distribución

- Para el estilo neón y las posiciones fijas, abre [ejemplo-der-neon.mmd](ejemplo-der-neon.mmd). Ahí están los cuatro acentos, las esquinas curvas y el ejemplo de 15 tablas en 3 × 5 con relaciones nativas.
- Para ajustar los recuadros, mide en el SVG renderizado el contenido visible de cada tabla, incluido el encabezado, las filas y las divisiones. Da a cada contorno el ancho y alto de su propio contenido más un margen interior corto y uniforme. Conserva el tamaño del texto.
- Si se pide una cuadrícula, conserva el orden aprobado y alinea las tablas por fila y columna. Usa el mayor ancho de cada columna y el mayor alto de cada fila para calcular la separación. Mantén las dimensiones individuales de cada recuadro.
- Después de ajustar los recuadros, vuelve a colocar los extremos de las conexiones en sus bordes y sitúa las etiquetas y símbolos en los pasillos. Comprueba que las líneas eviten el interior de otras tablas.
- El ejemplo fija posiciones y recorridos con `themeCSS` en Mermaid 12.2.0. Los selectores de los recorridos siguen el orden de las relaciones. Al agregar, quitar o reordenar una relación, verifica su recorrido y la posición de su etiqueta. Recalcula las posiciones cuando cambie el tamaño de las tablas.
- Renderiza el resultado si tienes acceso al motor. Comprueba el número de tablas y relaciones, las cardinalidades, las claves de destino, que todos los campos queden dentro de su recuadro y que las etiquetas se lean sin solaparse. Si solo puedes revisar el código, indica el alcance de la revisión.

[Guía de lectura y uso del ejemplo](README.md)
