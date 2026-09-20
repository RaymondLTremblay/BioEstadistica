# Actividades del capítulo 10 (Supuestos)

Dos actividades independientes, diseñadas para asignarse en días distintos.
Cada una está calculada para **1 hora y 30 minutos**, incluyendo la lectura de
las secciones correspondientes del capítulo, los ejercicios y la entrega.

| Archivo | Tema | Supuestos que cubre |
|:---|:---|:---|
| `Actividad_1_Normalidad.Rmd` | Normalidad, simetría y valores atípicos | normalidad, simetría |
| `Actividad_2_Homogeneidad.Rmd` | Homogeneidad, residuales y colinealidad | homogeneidad, independencia (parcial), colinealidad |

## Datos

Ambas actividades usan únicamente conjuntos de datos del paquete **ggversa**
(`dipodium` y `SparrowsElphick`). No dependen de ningún archivo `.csv` ni de
rutas relativas, así que los archivos se pueden mover o distribuir por separado
sin romperse.

## Entrega

Los estudiantes completan los bloques marcados `# ESCRIBE TU CÓDIGO AQUÍ`,
escriben sus respuestas debajo de cada **Respuesta:**, compilan con *Knit* y
entregan el `.Rmd` y el `.html`. Cada actividad termina con una lista de cotejo.

## Antes de asignarlas: verificación pendiente

Estas actividades no se han compilado, porque el entorno donde se escribieron no
tiene R instalado. Antes de asignarlas conviene:

1. Compilar el capítulo `10-Supuestos.Rmd` completo.
2. Correr en R las líneas que los estudiantes van a necesitar, en particular:
   - `table(dipodium$pardalinum_or_roseum)` (ejercicio 3 de la Actividad 1),
     para confirmar que los dos grupos tienen suficientes observaciones.
   - `sum(cooks.distance(modelo) > 1)` con el modelo `Number_of_Flowers ~ DBH`
     (ejercicio 4 de la Actividad 2), para confirmar que el ejercicio de
     "remover la observación más influyente" produce un contraste visible.
   - `shapiro.test()` sobre las variables de la Actividad 1: si alguna tiene
     n > 200, conviene mencionarlo en clase por la advertencia del capítulo 12.
3. Decidir si quiere añadir una rúbrica de puntuación. Las actividades no la
   incluyen.

Ninguna pregunta de las actividades afirma de antemano cuál es la forma de la
distribución ni el resultado de una prueba: todas piden que el estudiante
describa lo que observa. Por lo tanto, los ejercicios funcionan aunque los
resultados numéricos no sean los que uno anticipa.

## Clave de respuestas

No se incluye clave. Siguiendo la convención de los exámenes de este curso, si
la quiere, va en un archivo aparte dentro de esta misma carpeta.
