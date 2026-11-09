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
- Si se pide una cuadrícula, conserva las posiciones ya aprobadas. Traza las conexiones por los pasillos entre tablas. Ajusta solo el espacio necesario para las etiquetas y los símbolos.
- El ejemplo fija posiciones y recorridos con `themeCSS` en Mermaid 12.2.0. Los selectores de los recorridos siguen el orden de las relaciones. Al agregar, quitar o reordenar una relación, verifica su recorrido y la posición de su etiqueta. Recalcula las posiciones cuando cambie el tamaño de las tablas.
- Renderiza el resultado si tienes acceso al motor. Comprueba el número de tablas y relaciones, las cardinalidades, las claves de destino y el espacio entre etiquetas y tablas. Si solo puedes revisar el código, indica el alcance de la revisión.

[Guía de lectura y uso del ejemplo](README.md)
