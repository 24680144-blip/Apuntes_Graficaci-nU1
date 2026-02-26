
---

Bloque 1.1: Historia y Evolución de la Graficación

La graficación por computadora no comenzó con imágenes realistas, sino con la necesidad de representar datos visualmente. Podemos dividir su evolución en etapas clave que se reflejan en la forma en que escribimos código hoy en día.

### 1. La Era de los Vectores (Años 50 - 60)

En los inicios, las pantallas no tenían "píxeles" como las conocemos, sino que eran osciloscopios que dibujaban líneas rectas entre puntos. El concepto fundamental aquí es el **Vértice**.

* 
**Hito:** El sistema *Sketchpad* (1963) permitió por primera vez manipular objetos geométricos directamente.


* **Concepto en Blender:** Todo objeto 3D nace de una lista de coordenadas $(x, y, z)$. Sin vértices, no hay geometría.



### 2. La Era de la Topología y Polígonos (Años 70 - 80)

Se descubrió que conectando vértices se podían crear caras (polígonos). Esto permitió representar superficies sólidas y no solo "esqueletos" de alambre.

* 
**Hito:** Algoritmos para determinar qué caras son visibles y cuáles están ocultas.


* 
**Concepto en Blender:** La relación entre Vértices e Índices para formar Aristas y Caras (`from_pydata`).



---

## 💻 Código Funcional: La Evolución de la Geometría

Este script demuestra cómo pasamos de un simple punto (años 50) a una estructura conectada (años 70) usando la lógica de tus archivos cargados.

```python
import bpy

def explicar_evolucion_grafica():
    # [cite_start]Limpieza inicial de la escena [cite: 1, 15, 16]
    bpy.ops.object.select_all(action='SELECT')
    bpy.ops.object.delete()

    # --- ETAPA 1: EL VÉRTICE (Años 50) ---
    # Representa el inicio: un punto puro en el espacio
    coords_punto = [(0, 0, 0)]
    mesh_punto = bpy.data.meshes.new("PuntoHistorico")
    obj_punto = bpy.data.objects.new("PuntoHistorico", mesh_punto)
    bpy.context.collection.objects.link(obj_punto)
    [cite_start]mesh_punto.from_pydata(coords_punto, [], []) # Solo vértices [cite: 16]

    # --- ETAPA 2: LA LÍNEA/VECTOR (Años 60) ---
    # Conectamos dos puntos para crear una dirección
    coords_linea = [(2, 0, 0), (2, 2, 0)]
    [cite_start]aristas_linea = [(0, 1)] # Conexión entre índice 0 e índice 1 [cite: 16]
    mesh_linea = bpy.data.meshes.new("LineaVectorial")
    obj_linea = bpy.data.objects.new("LineaVectorial", mesh_linea)
    bpy.context.collection.objects.link(obj_linea)
    mesh_linea.from_pydata(coords_linea, aristas_linea, [])

    # --- ETAPA 3: EL POLÍGONO (Años 70 en adelante) ---
    # [cite_start]Cerramos la figura para crear una superficie (Cara) [cite: 16, 17]
    coords_cara = [(4, 0, 0), (6, 0, 0), (6, 2, 0), (4, 2, 0)]
    [cite_start]caras_poli = [(0, 1, 2, 3)] # Definimos la cara por sus índices [cite: 9]
    mesh_cara = bpy.data.meshes.new("PoligonoSuperficie")
    obj_cara = bpy.data.objects.new("PoligonoSuperficie", mesh_cara)
    bpy.context.collection.objects.link(obj_cara)
    mesh_cara.from_pydata(coords_cara, [], caras_poli)

    print("✅ Evolución demostrada: Punto -> Línea -> Polígono")

explicar_evolucion_grafica()

```

### 💡 Análisis del Código aplicado a la Historia

1. **Vértices (`vertices`):** Representan la posición matemática pura. Es el nivel más básico de la computación gráfica.


2. **Aristas (`edges`):** Introducen la noción de conectividad. Esto permitió el "Wireframe" (modelado de alambre) típico de las computadoras de los años 60.


3. **Caras (`faces`):** Es el salto a la **Rasterización**. Al tener una cara, la computadora puede decidir qué píxeles rellenar y cómo aplicarles luz o color.



---

**Siguiente paso:**
Hemos cubierto cómo la historia nos llevó del punto al polígono. ¿Deseas que pasemos al **punto 1.2: Áreas de Aplicación**, explicando cómo estos polígonos se usan en arquitectura (como tu script del pasillo) o medicina?
