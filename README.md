# Cálculo Estocástico

## I. Propósito

Este repositorio documenta el trabajo desarrollado en el curso de **Cálculo Estocástico Aplicado a Finanzas**. El objetivo central fue comprender cómo modelar fenómenos financieros bajo incertidumbre utilizando herramientas probabilísticas continuas, procesos estocásticos y métodos numéricos de valuación.

Mientras que las Series de Tiempo estudian patrones observados en datos históricos, el Cálculo Estocástico busca modelar la evolución futura de variables aleatorias mediante ecuaciones diferenciales estocásticas. Constituye el fundamento matemático de las Finanzas Cuantitativas modernas y de gran parte de la teoría de valuación de derivados.

Los temas estudiados abarcan Movimiento Browniano, Lema de Itô, Movimiento Browniano Geométrico, Black-Scholes, simulación Monte Carlo, árboles binomiales, opciones americanas, Longstaff-Schwartz y opciones exóticas como las opciones parisinas.

---

# II. Teorema Fundamental del Cálculo Estocástico: La incertidumbre puede modelarse

La piedra angular de las Finanzas Cuantitativas es reconocer que los precios futuros son inciertos.

Sin embargo, esa incertidumbre no implica ausencia de estructura.

El objetivo del Cálculo Estocástico consiste en construir procesos matemáticos capaces de representar la evolución probabilística de activos financieros.

Un activo financiero no sigue una trayectoria determinística.

Sigue una familia de trayectorias posibles.

Cada trayectoria tiene una probabilidad asociada.

La teoría financiera moderna surge precisamente del intento de modelar dichas trayectorias.

---

# III. Teorema del Movimiento Browniano

El Movimiento Browniano constituye el proceso estocástico más importante de las Finanzas Cuantitativas.

Representa una caminata aleatoria continua en el tiempo.

Formalmente, un proceso (B_t) es un Movimiento Browniano estándar si cumple:

* (B_0 = 0)
* Incrementos independientes
* Incrementos normales
* Trayectorias continuas

Los incrementos satisfacen:

```math
B_t-B_s \sim N(0,t-s)
```

para:

```math
0 \leq s < t
```

La importancia del Movimiento Browniano radica en que sirve como bloque fundamental para construir modelos más complejos.

---

# IV. Teorema de los Incrementos Independientes

Uno de los resultados más importantes del Movimiento Browniano es la independencia de sus incrementos.

Esto implica que:

```math
B_t-B_s
```

no depende de lo ocurrido antes de (s).

Financieramente, esta propiedad se relaciona con la hipótesis de mercados eficientes, donde la información pasada ya se encuentra incorporada en los precios.

---

# V. Teorema de la Variación Cuadrática

El Movimiento Browniano posee una propiedad que lo distingue de las funciones tradicionales.

Su variación cuadrática satisface:

```math
[B]_t=t
```

Esta característica hace que el cálculo diferencial clásico no sea suficiente.

Por ello surge el Cálculo Estocástico.

---

# VI. Teorema Fundamental del Cálculo Estocástico: El Lema de Itô

Así como el Teorema Fundamental del Cálculo conecta derivadas e integrales, el Lema de Itô conecta funciones y procesos estocásticos.

Es posiblemente el resultado más importante del curso.

Si:

```math
dX_t=\mu_tdt+\sigma_tdB_t
```

y:

```math
f=f(X_t,t)
```

entonces:

```math
df=
\left(
\frac{\partial f}{\partial t}
+
\mu_t\frac{\partial f}{\partial x}
+
\frac{1}{2}\sigma_t^2
\frac{\partial^2 f}{\partial x^2}
\right)dt
+
\sigma_t
\frac{\partial f}{\partial x}
dB_t
```

El término adicional:

```math
\frac{1}{2}\sigma^2
\frac{\partial^2 f}{\partial x^2}
```

es precisamente la consecuencia de la variación cuadrática del Movimiento Browniano.

---

# VII. Teorema del Movimiento Browniano Geométrico

El modelo financiero más importante estudiado en el curso fue el Movimiento Browniano Geométrico (GBM).

Su dinámica se expresa como:

```math
dS_t=\mu S_tdt+\sigma S_tdB_t
```

donde:

* (S_t): precio del activo.
* (\mu): deriva.
* (\sigma): volatilidad.

Este modelo garantiza que los precios permanezcan positivos.

---

# VIII. Teorema de la Solución Exacta del GBM

Aplicando Itô a:

```math
\ln(S_t)
```

se obtiene:

```math
S_t=
S_0
\exp
\left[
\left(
\mu-\frac12\sigma^2
\right)t
+
\sigma B_t
\right]
```

Esta ecuación permite simular trayectorias futuras de precios.

Fue la base del Laboratorio 1.

---

# IX. Teorema de la Deriva y la Volatilidad

Todo proceso financiero bajo GBM depende de dos parámetros fundamentales:

## Deriva

Representa la tendencia esperada.

```math
\mu
```

## Volatilidad

Representa la magnitud de la incertidumbre.

```math
\sigma
```

La volatilidad es el parámetro más importante en valuación de derivados.

---

# X. Teorema de la Simulación Monte Carlo

Monte Carlo consiste en aproximar cantidades desconocidas mediante simulación repetida.

La idea es simple:

1. Simular miles de escenarios.
2. Calcular el resultado de interés.
3. Promediar.

La Ley de los Grandes Números garantiza convergencia.

---

# XI. Teorema de la Medida Neutral al Riesgo

Uno de los resultados más elegantes de Finanzas Cuantitativas es que los derivados pueden valuarse sin conocer las preferencias de los inversionistas.

Bajo la medida neutral al riesgo:

```math
dS_t=rS_tdt+\sigma S_tdB_t^Q
```

La deriva deja de ser:

```math
\mu
```

y se convierte en:

```math
r
```

Esto permite descontar flujos esperados a la tasa libre de riesgo.

---

# XII. Teorema Fundamental de Valuación de Activos

El precio de un derivado es:

```math
V_0=
e^{-rT}
E^Q[Payoff]
```

Este resultado conecta probabilidad, arbitraje y valuación.

Es el fundamento de Black-Scholes, Monte Carlo y Árboles Binomiales.

---

# XIII. Teorema de Black-Scholes

Black-Scholes constituye el modelo más famoso de Finanzas.

Para una call europea:

```math
C=
S_0N(d_1)
-
Ke^{-rT}N(d_2)
```

donde:

```math
d_1=
\frac
{
\ln(S_0/K)
+
(r+\sigma^2/2)T
}
{\sigma\sqrt{T}}
```

```math
d_2=d_1-\sigma\sqrt{T}
```

Este resultado transforma un problema probabilístico complejo en una fórmula cerrada.

---

# XIV. Teorema de las Griegas

Las Griegas miden sensibilidad.

## Delta

Sensibilidad al precio.

## Gamma

Sensibilidad del Delta.

## Vega

Sensibilidad a volatilidad.

## Theta

Sensibilidad al tiempo.

## Rho

Sensibilidad a tasas.

Estas métricas son fundamentales para gestión de riesgo.

---

# XV. Teorema de la Cobertura Delta

La cobertura Delta busca neutralizar cambios pequeños en el precio del subyacente.

Si:

```math
\Delta=
\frac{\partial V}{\partial S}
```

entonces puede construirse un portafolio aproximadamente libre de riesgo.

Este concepto fue central en varios ejercicios del capítulo 15.

---

# XVI. Teorema del Árbol Binomial

El modelo Cox-Ross-Rubinstein aproxima el comportamiento continuo mediante movimientos discretos.

Cada periodo permite:

* Subir
* Bajar

Factores:

```math
u=e^{\sigma\sqrt{\Delta t}}
```

```math
d=e^{-\sigma\sqrt{\Delta t}}
```

Probabilidad neutral al riesgo:

```math
p=
\frac
{
e^{r\Delta t}-d
}
{
u-d
}
```

---

# XVII. Teorema de la Inducción Hacia Atrás

La valuación binomial se realiza mediante backward induction.

Se parte del payoff terminal.

Posteriormente se descuenta nodo por nodo hasta llegar al presente.

Este procedimiento fue la base del Proyecto 5.

---

# XVIII. Teorema de la Opción Europea

Una opción europea sólo puede ejercerse al vencimiento.

Call:

```math
\max(S_T-K,0)
```

Put:

```math
\max(K-S_T,0)
```

Su valuación es más sencilla porque no existe decisión intermedia.

---

# XIX. Teorema de la Opción Americana

Una opción americana puede ejercerse en cualquier momento.

Esto introduce un problema de optimización dinámica.

El valor se define como:

```math
V=
\max
(
Ejercicio,
Continuación
)
```

---

# XX. Teorema de la Prima por Ejercicio Temprano

Las opciones americanas deben valer al menos lo mismo que las europeas.

```math
V_{Am}
\geq
V_{Eu}
```

La diferencia recibe el nombre de prima por ejercicio temprano.

---

# XXI. Teorema de Longstaff-Schwartz

Longstaff-Schwartz aproxima el valor de continuación mediante regresión.

La metodología consiste en:

1. Simular trayectorias.
2. Identificar estados in-the-money.
3. Estimar valor de continuación.
4. Comparar contra ejercicio inmediato.

Fue el fundamento del Laboratorio 4.

---

# XXII. Teorema de la Regresión de Continuación

La regresión suele construirse mediante polinomios.

Ejemplo:

```math
F(S)
=
\beta_0
+
\beta_1S
+
\beta_2S^2
```

La comparación entre:

* Continuar.
* Ejercer.

determina la política óptima.

---

# XXIII. Teorema de las Opciones Dependientes de Trayectoria

Las opciones exóticas dependen no sólo del precio final.

También dependen del camino seguido por el activo.

Ejemplos:

* Asian
* Barrier
* Lookback
* Parisian

---

# XXIV. Teorema de la Opción Parisina

Las opciones parisinas incorporan memoria temporal.

No basta con cruzar una barrera.

Debe permanecer cierto tiempo debajo o encima de ella.

Esto introduce una dimensión adicional al problema.

---

# XXV. Teorema del Reloj de Barrera

El reloj parisino acumula tiempo.

Si:

```math
S_t<H
```

durante un número suficiente de periodos consecutivos, la opción puede desactivarse.

Si el precio regresa por encima de la barrera, el reloj se reinicia.

---

# XXVI. Teorema de la Probabilidad de Supervivencia

En opciones parisinas aparecen dos probabilidades clave:

## Survival Probability

Probabilidad de seguir activa.

## Knock-Out Probability

Probabilidad de quedar desactivada.

Estas probabilidades determinan gran parte del valor del derivado.

---

# XXVII. Teorema de la Volatilidad

La volatilidad es el principal determinante del valor de las opciones.

Mayor volatilidad implica:

* Mayor dispersión.
* Mayor incertidumbre.
* Mayor valor opcional.

Por ello Vega suele ser una sensibilidad crítica.

---

# XXVIII. Aplicaciones Desarrolladas

Durante el curso se desarrollaron:

* Simulación GBM.
* Estimación de volatilidad.
* Monte Carlo.
* Black-Scholes.
* Árbol Binomial CRR.
* Longstaff-Schwartz.
* Opciones Americanas.
* Opciones Parisinas.
* Cobertura Delta.
* Interpretación de Griegas.

---

# XXIX. Herramientas Utilizadas

* Python
* NumPy
* Pandas
* SciPy
* Matplotlib
* yfinance
* Google Colab
* LaTeX
* GitHub

---

# XXX. Bibliografía Fundamental

* Shreve
* Hull
* Björk
* Baxter & Rennie
* Glasserman
* Cox, Ross & Rubinstein
* Longstaff & Schwartz
* Black & Scholes

---

# XXXI. Autor

**Sofia Escamilla**

Licenciatura en Finanzas

Universidad Panamericana

Curso: Cálculo Estocástico Aplicado a Finanzas

