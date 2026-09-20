# Revisión del borrador: Exam_2206_1.qmd

Examen Parcial I, Biometría I, capítulos 02 a 08 (hasta *Estadística Descriptiva*).
Documento de revisión, 12 de septiembre de 2026.

---

## 1. Errores en la clave de respuestas (corregir primero)

Cinco de las 38 respuestas de la clave no corresponden a la pregunta. Son errores objetivos, no cuestiones de opinión.

| Pregunta | Clave actual | Correcta | Razón |
|:--|:--:|:--:|:--|
| 8 (nominal) | B | **A** | La respuesta es "Color de flor". "Nivel educativo" es ordinal |
| 9 (ordinal) | D | **B** | La respuesta es "Nivel educativo". "Número de hojas" es discreta |
| 12 (muestreo aleatorio) | C | **A** | "Reduce la posibilidad de sesgo de selección". La opción C dice que elimina la variación natural |
| 20 (tabla de colores) | C | **B** | Blanco = 15 es la frecuencia mayor. Amarillo = 5 es la menor |
| 35 (varianza grande) | A | **C** | Varianza grande = mayor dispersión. La opción A dice lo contrario |

Con estas correcciones la distribución de la clave queda A = 11, B = 10, C = 11, D = 6. La D está subutilizada.

---

## 2. Problemas de formato y de producción

1. **Pregunta 12: el enunciado está duplicado** (dos líneas idénticas).
2. **`\vspace{1cm}` y `\newpage` son LaTeX** y no producen nada en las salidas `html` ni `docx` declaradas en el YAML. Para el espacio de respuesta corta conviene una línea de guiones bajos o una tabla vacía; para el salto de página en `docx` se puede usar un div `{=openxml}` o simplemente publicar la clave en archivo aparte.
3. **La clave está en el mismo archivo que el examen.** Riesgo real de imprimir el examen con las respuestas. Sugerencia: mover la clave a `Clave_Exam_2206_1.qmd`, o envolverla en un parámetro (`params: key: false`) y un bloque condicional.
4. **Los diagramas `mermaid` (`xychart-beta`) son frágiles.** En `html` dependen de JavaScript; en `docx` Quarto necesita renderizarlos a imagen con un Chrome headless, y `xychart-beta` sigue siendo experimental. Para un examen impreso esto puede fallar el día antes. Recomendación: usar bloques de R con **ggplot2**, que es además lo que los estudiantes ven en el libro:

```{r, echo=FALSE, fig.height=2.5, fig.width=4}
library(ggplot2)
d <- data.frame(x = 1:7, f = c(2,5,9,11,9,5,2))
ggplot(d, aes(x, f)) + geom_col() +
  labs(title = "Figura 1", x = "Valor", y = "Frecuencia") + theme_classic()
```

5. **Marcador `---` duplicado** antes de la sección VI.
6. **Pregunta 27: las opciones (A, B, C, D) usan las mismas letras que las especies (A, B, C, D).** Confunde sin evaluar nada. Además el orden de las opciones está invertido respecto al eje. Renombrar las especies con nombres reales en itálicas, por ejemplo *Lepanthes rupestris*, *Lepanthes eltoroensis*, *Tectaria estremerana*, *Thelypteris verecunda*.
7. **Pregunta 21 está colocada en la sección V (Gráficos)** pero es una pregunta de tendencia central. Va en la sección VI.
8. **Figura 5 en la pregunta 35 es decorativa.** La pregunta no la usa. O se elimina la figura, o se cambia la pregunta para que dependa de ella (ver propuesta P4 abajo).

El total de puntos sí cuadra: 38 x 2 + 2 x 2 = 80.

---

## 3. Cobertura: lo que falta según los capítulos 02 a 08

Este es el problema principal. El examen se concentra en los capítulos 02 y 03 y casi no toca los capítulos 04, 07 y 08, que son los más extensos del material cubierto.

| Capítulo | Contenido | Preguntas actuales |
|:--|:--|:--:|
| 02 Introducción | proceso de investigación, hipótesis falsificable, correlación y causalidad, variable independiente y dependiente, niveles de medición | 5 items (solo niveles de medición) |
| 03 Población y Muestreo | población, muestra, parámetro contra estadístico (griego y latín), muestreo al azar, exactitud contra precisión | 8 items |
| 04 Inferencias e Hipótesis | inferencia, hipótesis nula y alterna, valor de p, error tipo I y II, poder | **0 items** |
| 05 Historia breve | Fisher, la dama degustando té, Gertrude Cox | **0 items** |
| 06 Tendencia central | media, mediana, moda, cuándo coinciden, relación con la asimetría | 6 items |
| 07 Dispersión | rango, varianza, desviación estándar, rango intercuartil, error estándar, intervalo de confianza 95% | 4 items (solo rango y varianza) |
| 08 Estadística descriptiva | resumen estadístico, cuantiles, oblicuidad (skewness), curtosis (kurtosis) | 1 item indirecto |

Vacíos concretos que conviene llenar:

- **Parámetro contra estadístico** y la notación griega frente a la latina (mu y x-barra, sigma y s). Es un capítulo entero del libro y no aparece.
- **Exactitud contra precisión** (error de muestreo).
- **Hipótesis nula y alterna, valor de p, error tipo I y tipo II.** Si el capítulo 04 entra en el examen, debería valer entre 6 y 8 puntos; si Ud. prefiere reservarlo para el segundo parcial, conviene decirlo en las instrucciones.
- **Desviación estándar** y su relación con la varianza, incluyendo unidades.
- **Rango intercuartil** y cuartiles.
- **Error estándar contra desviación estándar** y el efecto de *n*.
- **Interpretación de un intervalo de confianza de 95%.**
- **Oblicuidad y curtosis**, al menos el signo de la oblicuidad leído de una figura.
- **Por qué el denominador de la varianza muestral es n-1.**

Por otro lado, la sección V (Gráficos) evalúa material del capítulo 09, que queda fuera del alcance declarado. Las preguntas de forma de la distribución (24 a 26) sí se justifican porque las distribuciones y la oblicuidad se discuten en los capítulos 06 y 08, pero las preguntas 22 y 23 (histograma, diagrama de dispersión) pertenecen al capítulo 09. Conviene decidir explícitamente si el capítulo 09 entra o no.

---

## 4. Nivel cognitivo: el punto que Ud. plantea

Ud. quiere un examen de conceptos, donde el estudiante mire los datos y evalúe críticamente. El borrador actual no logra eso todavía.

- De 38 items de selección múltiple, **34 son recuerdo de definiciones** (nivel 1 de Bloom). Solo cuatro (24 a 27) requieren mirar algo, y la 27 se contesta leyendo la barra más alta.
- Hay **redundancia**: las preguntas 2 y 3 son la misma idea; 6 y 10 son la misma idea; 17 y 18 son la misma idea; 28, 29 y 30 son tres definiciones seguidas; 36 identifica la fórmula de la media después de que la 28 ya pidió su definición.
- **Distractores no plausibles.** En las preguntas 1, 4, 5, 11 y 16 los distractores son absurdos ("fenómenos astronómicos", "calcular hipótesis", "sustituir completamente a la población"). El estudiante los elimina sin saber el contenido, y el item deja de discriminar. Un buen distractor es un error real que los estudiantes cometen.
- **Sesgo de posición.** En los items definicionales la respuesta correcta está en A con demasiada frecuencia (1, 5, 13, 16, 22, 30, 38, más 8 y 12 corregidas). Además las preguntas 1 a 4 tienen clave A, B, C, D en secuencia. Conviene aleatorizar.
- La 39 y la 40 de respuesta corta **repiten** las preguntas 2, 3 y 12 de selección múltiple. Se pierden 4 puntos que podrían medir razonamiento.
- El prontuario dice que los exámenes serán de "selecciones múltiples, pareo, respuesta corta, y análisis de conceptos". El borrador es casi todo selección múltiple, sin pareo ni análisis.

**Meta sugerida:** aproximadamente 40% recuerdo, 40% interpretación de datos o figuras sin calculadora, 20% razonamiento o justificación escrita.

---

## 5. Items propuestos, todos resolubles mentalmente

Todos usan números escogidos para que el cómputo sea trivial o innecesario. No requieren calculadora ni R.

### P1. Media contra mediana con un valor extremo

Se midió la altura, en cm, de siete plántulas de *Lepanthes rupestris*:

`2, 3, 3, 4, 4, 5, 100`

¿Cuál afirmación es correcta?

A. La mediana es mayor que la media
B. La media es mayor que la mediana
C. La media y la mediana son iguales
D. La moda es mayor que la media

*Respuesta: B. Mediana = 4, media claramente mayor. No hace falta calcularla.*

### P2. Cuál conjunto tiene mayor dispersión

Dos parcelas, cinco mediciones de número de frutos cada una:

Parcela 1: `10, 10, 10, 10, 10`
Parcela 2: `6, 8, 10, 12, 14`

¿Cuál afirmación es correcta?

A. Ambas tienen la misma varianza
B. La Parcela 1 tiene mayor varianza
C. La Parcela 2 tiene mayor varianza
D. No se puede determinar sin calcular

*Respuesta: C. También sirve para la pregunta 34 actual, porque la varianza y el rango de la Parcela 1 son cero.*

### P3. Efecto de sumar una constante

A cada una de las 20 mediciones de un conjunto se le suma 5. Comparado con los datos originales:

A. La media aumenta y la desviación estándar aumenta
B. La media aumenta y la desviación estándar no cambia
C. La media no cambia y la desviación estándar aumenta
D. Ni la media ni la desviación estándar cambian

*Respuesta: B. Item clásico de concepto, imposible de contestar de memoria.*

### P4. Leer la forma de una distribución (reemplazo de la pregunta 35)

Observe la Figura 5, con frecuencias `5, 5, 6, 2, 6, 5, 5`. ¿Qué describe mejor esta distribución?

A. Simétrica y unimodal
B. Sesgada a la derecha
C. Aproximadamente simétrica pero con una depresión en el centro
D. Uniforme

*Respuesta: C. Así la figura deja de ser decorativa.*

### P5. Rango intercuartil

Para los datos ordenados `1, 2, 3, 4, 5, 6, 7, 8, 9`, el rango intercuartil es aproximadamente:

A. 8
B. 5
C. 4
D. 2

*Respuesta: C. Q1 = 2.5, Q3 = 6.5 aproximadamente, IQR = 4. Verifique el resultado con la definición de `quantile()` que usa el libro, capítulo 07, antes de fijar la clave.*

### P6. Parámetro contra estadístico

Se midió el largo de la hoja en 40 individuos de una población de *Lepanthes eltoroensis* que tiene miles de individuos. El promedio de esos 40 individuos es:

A. Un parámetro, y se simboliza con mu
B. Un estadístico, y se simboliza con x-barra
C. Un parámetro, y se simboliza con x-barra
D. Un estadístico, y se simboliza con sigma

*Respuesta: B. Cubre el capítulo 03, sección "Griego y latín".*

### P7. Exactitud contra precisión

Una balanza reporta el peso de la misma muestra cinco veces: `10.21, 10.22, 10.21, 10.22, 10.21` g. El peso verdadero es 12.00 g. La balanza es:

A. Exacta y precisa
B. Exacta pero no precisa
C. Precisa pero no exacta
D. Ni exacta ni precisa

*Respuesta: C.*

### P8. Desviación estándar y unidades

Se midió la altura de varias plantas en centímetros. Las unidades de la varianza y de la desviación estándar son, respectivamente:

A. cm y cm
B. cm y cm cuadrados
C. cm cuadrados y cm
D. Ninguna de las dos tiene unidades

*Respuesta: C. Explica por qué se reporta la desviación estándar y no la varianza.*

### P9. Error estándar contra desviación estándar

Si se aumenta el tamaño de la muestra de 25 a 100 individuos de la misma población, se espera que:

A. La desviación estándar disminuya y el error estándar se mantenga igual
B. El error estándar disminuya y la desviación estándar se mantenga aproximadamente igual
C. Ambos disminuyan por igual
D. Ambos se mantengan iguales

*Respuesta: B.*

### P10. Correlación y causalidad

En un estudio se observa que los meses con más venta de helado son también los meses con más picadas de mosquito. Se puede concluir que:

A. El helado atrae a los mosquitos
B. Las picadas aumentan el consumo de helado
C. Existe una asociación, pero no evidencia de causalidad
D. No existe ninguna relación entre las dos variables

*Respuesta: C. Capítulo 02, tipos de error de interpretación.*

### P11. Hipótesis falsificable

¿Cuál de las siguientes es una hipótesis falsificable?

A. Las orquídeas son las plantas más bellas del bosque
B. Existen especies aún no descritas en algún lugar del planeta
C. Las plantas que crecen a mayor elevación producen menos frutos
D. La naturaleza busca el equilibrio

*Respuesta: C. Capítulo 02.*

### P12. Variable dependiente e independiente

Se compara el número de semillas producidas por plantas creciendo bajo tres niveles de sombra. La variable dependiente es:

A. El nivel de sombra
B. El número de semillas
C. La especie estudiada
D. El número de plantas medidas

*Respuesta: B.*

### P13. Tabla de frecuencia con frecuencia acumulada

| Clase | Frecuencia |
|:--|--:|
| 0 a 9 | 5 |
| 10 a 19 | 15 |
| 20 a 29 | 20 |
| 30 a 39 | 10 |

¿Qué porcentaje de las observaciones cae por debajo de 20?

A. 20%
B. 40%
C. 60%
D. 80%

*Respuesta: B. n = 50, acumulado 20 de 50.*

### P14. Oblicuidad leída de una figura

Para una distribución con una cola larga hacia los valores altos, se espera que:

A. La media sea menor que la mediana y la oblicuidad sea negativa
B. La media sea mayor que la mediana y la oblicuidad sea positiva
C. La media y la mediana sean iguales y la oblicuidad sea cero
D. La oblicuidad no depende de la relación entre media y mediana

*Respuesta: B. Conecta los capítulos 06 y 08.*

### P15. Muestreo, con dos diseños comparados

Para estimar la altura promedio de los árboles de un bosque, un estudiante mide únicamente los árboles que puede alcanzar desde el sendero. El problema principal es que:

A. La muestra es demasiado pequeña
B. La muestra no es representativa de la población
C. La varianza será igual a cero
D. No se puede calcular la media

*Respuesta: B. Mejor que la pregunta 14 actual, porque el distractor A también es tentador.*

### P16. Pareo, formato que pide el prontuario

Parear cada índice con lo que mide.

| Índice | | Mide |
|:--|--|:--|
| 1. Media | | a. Dispersión en unidades originales |
| 2. Mediana | | b. Valor más frecuente |
| 3. Moda | | c. Promedio aritmético |
| 4. Desviación estándar | | d. Valor central de los datos ordenados |
| 5. Rango intercuartil | | e. Amplitud del 50% central de los datos |

*Respuestas: 1c, 2d, 3b, 4a, 5e.*

### P17 y P18. Respuesta corta, en sustitución de las preguntas 39 y 40

**P17 (2 puntos).** Un compañero le dice: "calculé la media de mis datos y salió 45, así que la mayoría de mis plantas mide cerca de 45 cm". Explique en dos o tres oraciones por qué esa conclusión puede ser incorrecta, y qué índice adicional pediría Ud. para evaluarla.

*Se busca: la media sola no describe la dispersión ni la forma; pedir la desviación estándar, el rango o la mediana; mencionar valores extremos o distribución bimodal.*

**P18 (2 puntos).** Observe estos dos conjuntos de datos, ambos con media 10:

Conjunto A: `9, 10, 10, 10, 11`
Conjunto B: `2, 5, 10, 15, 18`

¿Cuál conjunto tiene mayor desviación estándar y por qué? No calcule, justifique.

*Se busca: el B, porque las observaciones se alejan más de la media.*

---

## 6. Estructura sugerida para la versión final

Manteniendo los 80 puntos y la regla de no usar calculadora:

| Sección | Formato | Items | Puntos |
|:--|:--|--:|--:|
| I. Conceptos fundamentales y proceso de investigación (cap. 02) | selección múltiple | 5 | 10 |
| II. Variables y niveles de medición (cap. 02) | selección múltiple | 4 | 8 |
| III. Población, muestreo, parámetro contra estadístico, exactitud y precisión (cap. 03) | selección múltiple | 6 | 12 |
| IV. Inferencia e hipótesis (cap. 04) | selección múltiple | 4 | 8 |
| V. Tablas de frecuencia y lectura de datos | selección múltiple con datos | 4 | 8 |
| VI. Tendencia central (cap. 06) | selección múltiple, la mitad con datos | 5 | 10 |
| VII. Dispersión (cap. 07) | selección múltiple, la mitad con datos | 6 | 12 |
| VIII. Forma de la distribución y descriptiva (cap. 08) | figuras | 3 | 6 |
| IX. Pareo | pareo | 1 bloque de 5 | 5 |
| X. Respuesta corta y análisis | 2 preguntas | 2 | 6 |
| **Total** | | | **85** |

Si prefiere quedarse exactamente en 80, elimine dos items de selección múltiple de las secciones I o II, que son las más saturadas de recuerdo. Si el capítulo 04 no entra en este parcial, elimine la sección IV y añada dos items de dispersión y uno de descriptiva.

---

## 7. Lista de verificación antes de imprimir

- [ ] Corregir las cinco claves erróneas (8, 9, 12, 20, 35)
- [ ] Eliminar el enunciado duplicado de la pregunta 12
- [ ] Mover la clave a un archivo aparte
- [ ] Sustituir `mermaid` por bloques de ggplot2 y renderizar a `docx` para verificar que las figuras salen
- [ ] Sustituir `\vspace` y `\newpage` por equivalentes válidos en html y docx
- [ ] Mover la pregunta 21 a la sección VI
- [ ] Renombrar las especies de la pregunta 27 y poner los nombres en itálicas
- [ ] Aleatorizar la posición de las respuestas correctas, subiendo el uso de la D
- [ ] Verificar que el total de puntos coincide con el encabezado
- [ ] Decidir y declarar si los capítulos 04, 05 y 09 entran en este parcial
