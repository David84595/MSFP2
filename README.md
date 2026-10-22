# Práctica 2 — Sistema cardiovascular

Repositorio académico de la asignatura **Modelado de Sistemas Fisiológicos**, correspondiente al programa de **Ingeniería Biomédica** del Tecnológico Nacional de México / Instituto Tecnológico de Tijuana.

Esta práctica estudia un modelo simplificado del **sistema cardiovascular** mediante una analogía eléctrica. Se plantea un circuito con impedancia \(Z\), inductancia \(L\), resistencia \(R\) y capacitancia \(C\), y se analiza la relación entre la presión de entrada \(P_a(t)\) y la presión de salida \(P_p(t)\). Los cálculos incluyen el modelo integro-diferencial, la función de transferencia, el error en estado estacionario y el análisis de estabilidad para distintos casos fisiológicos.

**Docente:** Dr. Paul Antonio Valle Trujillo  
**Departamento:** Ingeniería Eléctrica y Electrónica  
**Institución:** Tecnológico Nacional de México / Instituto Tecnológico de Tijuana  
**Asignatura:** Modelado de Sistemas Fisiológicos  
**Programa:** Ingeniería Biomédica  
**Estudiante:** Nombre completo · Número de control · correo institucional

**Repositorio de la asignatura:** https://github.com/DrPaulValle/MSF-IBF1020

---

## Contenido

1. [Resumen](#resumen)
2. [Objetivos](#objetivos)
3. [Modelo físico y analogía eléctrica](#modelo-fisico)
4. [Modelo integro-diferencial](#modelo-integro-diferencial)
5. [Función de transferencia](#funcion-de-transferencia)
6. [Error en estado estacionario](#error)
7. [Estabilidad y polos](#estabilidad)
8. [Casos analizados](#casos)
9. [Procedimiento de trabajo](#procedimiento)
10. [Estructura del repositorio](#estructura)
11. [Conclusiones](#conclusiones)
12. [Referencias](#referencias)

---

<a id="resumen"></a>
## 1. Resumen

El objetivo de esta práctica es representar matemáticamente un sistema cardiovascular simplificado utilizando una analogía eléctrica. A partir del circuito proporcionado en los cálculos de la práctica, se establece una ecuación integro-diferencial y se obtiene una función de transferencia que relaciona las presiones \(P_a(s)\) y \(P_p(s)\).

Posteriormente se analiza el error en estado estacionario para una entrada escalón y se calculan los polos del sistema para tres configuraciones identificadas en los apuntes como **hipotenso, normotenso e hipertenso**. La comparación permite estudiar cómo cambia la respuesta dinámica del modelo al modificar el parámetro \(C\).

**Palabras clave:** sistema cardiovascular; modelado fisiológico; analogía eléctrica; función de transferencia; polos; estabilidad; MATLAB.

[Volver al contenido](#contenido)

---

<a id="objetivos"></a>
## 2. Objetivos

### Objetivo general

Obtener y analizar el modelo matemático de un sistema cardiovascular simplificado mediante una analogía eléctrica, determinando su función de transferencia, error en estado estacionario y estabilidad para diferentes parámetros.

### Objetivos específicos

- Identificar las variables y los elementos del circuito equivalente.
- Plantear el modelo integro-diferencial a partir de las relaciones del circuito.
- Obtener la función de transferencia mediante la transformada de Laplace.
- Calcular el error en estado estacionario ante una entrada escalón.
- Determinar los polos del sistema para los casos hipotenso, normotenso e hipertenso.
- Comparar los resultados obtenidos para los distintos valores de capacitancia.

[Volver al contenido](#contenido)

---

<a id="modelo-fisico"></a>
## 3. Modelo físico y analogía eléctrica

El circuito de la práctica utiliza los elementos \(Z\), \(L\), \(R\) y \(C\). Las variables de presión se representan mediante señales equivalentes del circuito, mientras que las relaciones entre los elementos permiten formular el comportamiento dinámico del sistema.

| Símbolo | Descripción en el modelo |
|---|---|
| \(P_a(t)\) | Presión de entrada |
| \(P_p(t)\) | Presión de salida |
| \(Z\) | Impedancia del elemento de entrada |
| \(L\) | Inductancia |
| \(R\) | Resistencia |
| \(C\) | Capacitancia |

La topología de referencia es la dibujada en los cálculos manuscritos incluidos con la práctica. Los parámetros utilizados para los tres casos se presentan en la sección [Casos analizados](#casos).

[Volver al contenido](#contenido)

---

<a id="modelo-integro-diferencial"></a>
## 4. Modelo integro-diferencial

De acuerdo con el desarrollo de los apuntes, la relación del circuito se expresa como:

\[
\frac{P_a(t)-P_p(t)}{Z}
+\frac{1}{L}\int [P_a(t)-P_p(t)]\,dt
=
C\frac{dP_p(t)}{dt}+\frac{P_p(t)}{R}
\]

Esta ecuación relaciona la presión de entrada con la presión de salida e incorpora los términos resistivo, inductivo y capacitivo del modelo.

Para el análisis algebraico en el dominio de Laplace, se consideran condiciones iniciales nulas, tal como se hace en la derivación de la función de transferencia.

[Volver al contenido](#contenido)

---

<a id="funcion-de-transferencia"></a>
## 5. Función de transferencia

Aplicando la transformada de Laplace y agrupando los términos de entrada y salida, el resultado obtenido en los cálculos es:

\[
\boxed{
\frac{P_p(s)}{P_a(s)}
=
\frac{LRs+RZ}
{CLRZs^2+L(Z+R)s+RZ}
}
\]

Por lo tanto, la función de transferencia del modelo es:

\[
\boxed{G(s)=\frac{LRs+RZ}{CLRZs^2+L(Z+R)s+RZ}}
\]

El denominador es de segundo orden, por lo que el comportamiento dinámico se estudia a partir de sus raíces o polos.

[Volver al contenido](#contenido)

---

<a id="error"></a>
## 6. Error en estado estacionario

Para una entrada escalón unitario:

\[
P_a(s)=\frac{1}{s}
\]

El error se define como la diferencia entre la entrada y la salida:

\[
e(t)=P_a(t)-P_p(t)
\]

En el dominio de Laplace, el error en estado estacionario se calcula mediante el teorema del valor final:

\[
e_{ss}=\lim_{s\to0}sP_a(s)\left[1-\frac{P_p(s)}{P_a(s)}\right]
\]

Al sustituir la función de transferencia obtenida en los cálculos, el resultado registrado es:

\[
\boxed{e_{ss}=0}
\]

Este resultado corresponde al análisis de una entrada escalón bajo las condiciones utilizadas en la práctica.

[Volver al contenido](#contenido)

---

<a id="estabilidad"></a>
## 7. Estabilidad y polos

Los polos se obtienen igualando a cero el denominador de la función de transferencia:

\[
CLRZs^2+L(Z+R)s+RZ=0
\]

Identificando los coeficientes de la ecuación cuadrática:

\[
a=CLRZ,\qquad b=L(Z+R),\qquad c=RZ
\]

Se aplica la fórmula general:

\[
\boxed{s_{1,2}=\frac{-L(Z+R)\pm\sqrt{L^2(Z+R)^2-4(CLRZ)(RZ)}}{2CLRZ}}
\]

Los polos permiten caracterizar la estabilidad y el tipo de respuesta dinámica del modelo. Para cada configuración se deben comparar sus valores y verificar si tienen parte real negativa.

[Volver al contenido](#contenido)

---

<a id="casos"></a>
## 8. Casos analizados

Los apuntes utilizan los siguientes valores de parámetros:

| Caso | \(Z\) | \(L\) | \(R\) | \(C\) |
|---|---:|---:|---:|---:|
| Hipotenso | 0.010 | 0.001 | 1.000 | 3500 |
| Normotenso | 0.010 | 0.001 | 1.000 | 1500 |
| Hipertenso | 0.010 | 0.001 | 1.000 | 1000 |

### Resultados de polos registrados en los cálculos

| Caso | Polo 1 | Polo 2 | Comportamiento indicado |
|---|---|---|---|
| Hipotenso | \(-14.429 + 8.8051i\) | \(-14.429 - 8.8051i\) | Estable y subamortiguado |
| Normotenso | \(-12.062\) | \(-55.272\) | Polos reales negativos |
| Hipertenso | \(-10.0\) | \(-10.0\) | Polos reales repetidos |

Los valores de esta tabla se transcriben de los cálculos manuscritos suministrados para la práctica. Conviene comprobarlos con MATLAB o con una calculadora antes de utilizarlos en un análisis numérico posterior.

[Volver al contenido](#contenido)

---

<a id="procedimiento"></a>
## 9. Procedimiento de trabajo

- [ ] Identificar los elementos y las variables del circuito cardiovascular.
- [ ] Plantear la ecuación integro-diferencial.
- [ ] Aplicar la transformada de Laplace con las condiciones iniciales indicadas.
- [ ] Despejar la función de transferencia.
- [ ] Calcular el error en estado estacionario para una entrada escalón.
- [ ] Igualar a cero el denominador y calcular los polos.
- [ ] Sustituir los parámetros de los casos hipotenso, normotenso e hipertenso.
- [ ] Comparar las raíces y describir el comportamiento dinámico de cada caso.
- [ ] Adjuntar los cálculos, las gráficas y el código de verificación si se utilizaron herramientas computacionales.

[Volver al contenido](#contenido)

---

<a id="estructura"></a>
## 10. Estructura del repositorio

Una estructura sugerida para organizar la entrega es:

```text
.
├── README.md
├── Modelado de sistemas fisiológicos.pdf
├── calculos/
│   └── calculos_practica_2.pdf
├── matlab/
│   └── analisis_sistema_cardiovascular.m
└── evidencias/
    ├── polos.png
    └── respuestas.png
```

Los nombres y las carpetas son sugerencias. Si se utilizan nombres diferentes, actualizar las rutas para que coincidan con los archivos que realmente se suban al repositorio.

[Volver al contenido](#contenido)

---

<a id="conclusiones"></a>
## 11. Conclusiones

En esta práctica se formuló un modelo cardiovascular simplificado mediante una analogía eléctrica. A partir de la ecuación integro-diferencial se obtuvo una función de transferencia de segundo orden, se determinó el error en estado estacionario ante una entrada escalón y se estudiaron los polos para tres conjuntos de parámetros.

La comparación de los casos permite observar que los parámetros del circuito modifican la ubicación de los polos y, por tanto, la dinámica del sistema. La conclusión definitiva debe complementarse con la verificación numérica de los cálculos y las gráficas obtenidas.

[Volver al contenido](#contenido)

---

<a id="referencias"></a>
## 12. Referencias

1. Valle Trujillo, P. A. *Modelado de Sistemas Fisiológicos*. Tecnológico Nacional de México / Instituto Tecnológico de Tijuana. Material de la asignatura.
2. Apuntes manuscritos de la **Práctica 2: Sistema cardiovascular**, proporcionados para la elaboración de este repositorio.

---

## Uso académico

Este README documenta el procedimiento y los cálculos proporcionados para la Práctica 2. Los resultados numéricos se atribuyen a los apuntes suministrados y deben distinguirse de cualquier simulación o medición adicional realizada por el estudiante.
