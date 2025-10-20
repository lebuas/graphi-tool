Linl: https://lebuas.github.io/graphi-tool/
# 🚀 GraphiTool: Documentación Completa

**GraphiTool** es una herramienta web basada en **D3.js** para la visualización, manipulación y gestión de diseños de grafos (redes). Su objetivo principal es permitir a los usuarios organizar manualmente diseños complejos de nodos y conexiones, manteniendo la posibilidad de guardar y restaurar esas posiciones exactas para trabajos futuros o reportes.

---
<img width="941" height="802" alt="imagen" src="https://github.com/user-attachments/assets/bae89c5c-6fc4-4a82-a1fd-b93b4e58251b" />


---

## 💾 Formato de Archivos XLS/CSV

La herramienta acepta dos formatos de archivos para la carga y produce un formato específico para la descarga. Las columnas son sensibles a mayúsculas y minúsculas y deben estar presentes.

### 1. Archivo de Entrada (Carga Simple)

Este formato es el mínimo necesario para construir la topología de la red. Los nodos se distribuirán aleatoriamente con la simulación de fuerzas.

| Columna | Descripción                             | Ejemplo       |
|---------|-----------------------------------------|---------------|
| From    | ID o nombre del nodo de origen.         | Cliente_A     |
| To      | ID o nombre del nodo de destino.        | Servidor_X    |
| Label   | Etiqueta o descripción del enlace.      | Solicitud_GET |

### 2. Archivo de Entrada/Salida (Carga/Descarga Organizada)

Este formato incluye las coordenadas (X, Y) de los nodos. Se usa para cargar un diseño previamente guardado o para descargar la posición actual del gráfico.

| Columna | Descripción                             | Uso                                      |
|---------|-----------------------------------------|------------------------------------------|
| From    | ID o nombre del nodo de origen.         | Topología                                 |
| To      | ID o nombre del nodo de destino.        | Topología                                 |
| Label   | Etiqueta del enlace.                    | Topología                                 |
| CFrom   | Coordenada X, Y del nodo origen.        | Guarda/Restaura la posición del nodo From |
| CTo     | Coordenada X, Y del nodo destino.       | Guarda/Restaura la posición del nodo To   |

---

## 💻 Interfaz y Controles

La herramienta ofrece controles divididos en un panel lateral (gestión de elementos) y un pie de página (gestión de archivos).

### 1. Pie de Página: Control de Archivos y Exportación

| Botón                    | Función             | Explicación                                                                 |
|--------------------------|---------------------|------------------------------------------------------------------------------|
| Cargar Datos (Simple)    | Carga la topología  | Lee el archivo simple (`From`, `To`, `Label`) e inicia la simulación de fuerzas. |
| Cargar Datos (Organizados) | Restaura el diseño | Lee el archivo completo (`CFrom`, `CTo`) y coloca los nodos en sus posiciones guardadas. |
| Descargar (Organizados) | Guarda el diseño    | Captura las coordenadas actuales (X, Y) de todos los nodos y genera un nuevo archivo. |
| Capturar SVG            | Exportación vectorial | Exporta el gráfico como archivo SVG ajustado para evitar cortes en los bordes. |

### 2. Menú Lateral: Control de Nodos (Visibilidad)

| Elemento             | Acción Principal       | Uso                                                                 |
|----------------------|------------------------|----------------------------------------------------------------------|
| Lista de Nodos (Clic)| Control de visibilidad | Activa o desactiva la clase `hidden-element` del nodo y sus enlaces. |
| Buscador             | Filtrado de lista      | Permite encontrar rápidamente un nodo específico para modificar visibilidad. |

---

## 🧠 Interacción en el Área de Trabajo

- **Arrastrar y Soltar**: Al arrastrar un nodo, se fijan sus coordenadas (`fx`, `fy`), sacándolo temporalmente de la simulación de fuerzas.
- **Conexiones Dinámicas**: Las flechas se recalculan en cada tick para terminar exactamente en la circunferencia del nodo destino.
- **Límites de Frontera**: Una fuerza invisible impide que los nodos se muevan fuera del área de visualización.
