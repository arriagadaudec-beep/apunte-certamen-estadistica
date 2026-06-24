# Soluciones Listado 4 — Prueba de Hipótesis
## Estadística II (523226) · Primer Semestre 2026

> Documentación basada en las imágenes de la solución oficial (6 páginas manuscritas).
> Fuente: `solucion listado 4/` + enunciado `listado_4_2026_523226_2026_I.pdf`

---

## Ejercicio 1 · Sueldos por género

### Enunciado
En una empresa se afirma que el sueldo promedio de un hombre excede al de una mujer en **más de $20,00 por semana**. Los datos revelan:

| Grupo | n | X̄ ($) | S ($) |
|-------|---|--------|-------|
| Hombres | 60 | 292,50 | 15,60 |
| Mujeres | 60 | 266,10 | 18,20 |

¿Qué puede concluir a un nivel de significación del **1%**?

---

### Solución del profesor (páginas 1–4)

#### Definición de variables
- X₁: sueldo semanal del hombre · μ₁ = E{X₁} · σ₁² = Var{X₁}
- X₂: sueldo semanal de la mujer  · μ₂ = E{X₂} · σ₂² = Var{X₂}
- Muestra X₁: n₁ = 60, X̄₁ = 292,50, S₁ = 15,60
- Muestra X₂: n₂ = 60, X̄₂ = 266,10, S₂ = 18,20

#### Hipótesis principales
La empresa AFIRMA que μ₁ − μ₂ > 20 → se pone como H₀ (se verifica si puede rechazarse):

```
H₀: μ₁ − μ₂ ≥ 20,00   vs   H₁: μ₁ − μ₂ < 20,00   (cola izquierda)
```

#### Paso previo: Verificación de igualdad de varianzas (prueba F)
Las varianzas σ₁² y σ₂² son **desconocidas** → hay que verificar si son iguales o distintas.

```
H₀: σ₁²/σ₂² = 1   vs   H₁: σ₁²/σ₂² ≠ 1   (bilateral, α = 0,01)
```

Estadístico F observado:
```
F_obs = S₁²/S₂² = (15,60)² / (18,20)² = 243,36 / 331,24 = 0,735
```

Valores críticos (F con gl₁=59, gl₂=59 ≈ gl=60,60):
```
F_{60,60; 0,995} = 1,96
F_{60,60; 0,005} = 1 / F_{60,60; 0,995} = 1 / 1,96 = 0,510
```

Región de rechazo: F_obs > 1,96  O  F_obs < 0,510

Verificación:
```
0,510 < 0,735 < 1,96  →  F_obs está FUERA de la región de rechazo
```

Verificación alternativa (invirtiendo el cociente):
```
F_obs = S₂²/S₁² = (18,20)² / (15,60)² = 331,24 / 243,36 = 1,361
1,361 < 1,96  →  misma conclusión
```

**Conclusión del paso previo:** No se rechaza H₀: σ₁²/σ₂² = 1 al nivel del 1%.
→ Las varianzas son **desconocidas pero iguales** (σ₁² = σ₂²) → se usa varianza pooled Sp.

---

#### Cálculo de la varianza pooled Sp²

```
Sp² = [(n₁−1)·S₁² + (n₂−1)·S₂²] / (n₁ + n₂ − 2)
    = [(60−1)·(15,60)² + (60−1)·(18,20)²] / (60 + 60 − 2)
    = [59·243,36 + 59·331,24] / 118
    = [14.358,24 + 19.543,16] / 118
    = 33.901,40 / 118
    = 287,30

Sp = √287,30 = 16,95
```

---

#### Estadístico de prueba

Como n₁ = n₂ = **60 ≥ 30** → el TCL (Teorema Central del Límite) aplica → se usa **Z** (no t).

El profesor muestra ambas versiones y ambas dan 2,068:

**Versión t (con Sp pooled):**
```
T = [(X̄₁ − X̄₂) − δ₀] / [Sp · √(1/n₁ + 1/n₂)]
  = [(292,50 − 266,10) − 20,00] / [16,95 · √(1/60 + 1/60)]
  = [26,40 − 20,00] / [16,95 · √(2/60)]
  = 6,40 / [16,95 · 0,18257]
  = 6,40 / 3,094
  = 2,068
```

**Versión Z (con S₁²/n₁ + S₂²/n₂, por TCL):**
```
Z_obs = (X̄₁ − X̄₂ − δ₀) / √(S₁²/n₁ + S₂²/n₂)
      = (292,50 − 266,10 − 20,00) / √(243,36/60 + 331,24/60)
      = 6,40 / √(4,056 + 5,521)
      = 6,40 / √9,577
      = 6,40 / 3,095
      = 2,068
```

---

#### Valor crítico y región de rechazo

El profesor muestra dos comparaciones:

**Usando t (gl = 118):**
```
t_{118; 0,99} = 2,58
t_obs = 2,068 < 2,58  →  No se rechaza H₀
```

**Usando Z (por TCL, n ≥ 30):**
```
Z_{0,99} = 2,33
Región crítica (cola izquierda): Z < −Z_{0,99} = −2,33
Z_obs = 2,068  →  2,068 > −2,33  →  No está en la región de rechazo
```

**NOTA del profesor:** Z_obs = 2,068 es positivo, es decir, los datos van en el sentido
OPUESTO a H₁ (que dice μ₁−μ₂ < 20). El estadístico está claramente fuera de la zona
de rechazo (la cola izquierda).

---

#### Conclusión

> **No se rechaza H₀: μ₁ − μ₂ ≥ 20,00 al nivel del 1%.**
> Los hombres en media ganan **más de $20,00** que las mujeres.

---

## Ejercicio 2 · Resistencia de dos tipos de acero

### Enunciado
Se compara la resistencia a la tensión de dos tipos de acero. Muestras de tamaño 40 y 32, con medias 18,12 y 16,87 Kg/cm² respectivamente.

**a)** Si σ₁ = 1,6 y σ₂ = 1,4 (conocidas). ¿Hay diferencias en las resistencias medias? α = 0,01.

**b)** ¿Modificaría su respuesta en a) si solo se dispone de S₁ = 1,6 y S₂ = 1,4?

---

### Solución del profesor (páginas 4–5)

#### Definición de variables
- X₁: resistencia tensión acero tipo 1 · n₁ = 40 · X̄₁ = 18,12 Kg/cm²
- X₂: resistencia tensión acero tipo 2 · n₂ = 32 · X̄₂ = 16,87 Kg/cm²

---

#### Parte a) — σ₁ y σ₂ conocidas y distintas → Z bilateral

```
H₀: μ₁ = μ₂   vs   H₁: μ₁ ≠ μ₂   (bilateral)
(equivalente: H₀: μ₁−μ₂ = 0  vs  H₁: μ₁−μ₂ ≠ 0)
```

Estadístico (σ conocidas → Z directamente):
```
Z_obs = (X̄₁ − X̄₂ − Δ₀) / √(σ₁²/n₁ + σ₂²/n₂)
      = (18,12 − 16,87 − 0) / √((1,6)²/40 + (1,4)²/32)
      = 1,25 / √(2,56/40 + 1,96/32)
      = 1,25 / √(0,064 + 0,06125)
      = 1,25 / √0,12525
      = 1,25 / 0,35390
      = 3,53
```

Valor crítico bilateral (α = 0,01):
```
Z_{1−α/2} = Z_{0,995} = 2,58
Región de rechazo: |Z_obs| > 2,58
```

Verificación:
```
|3,53| = 3,53 > 2,58  ✓  →  Z_obs está en la región de rechazo
```

**Conclusión parte a):**
> Se rechaza H₀: μ₁ = μ₂ al nivel del 1%.
> Hay diferencias en las resistencias medias de los 2 tipos de acero al nivel del 1%.

---

#### Parte b) — Solo se dispone de S₁ y S₂ (no σ) → ¿cambia la respuesta?

Respuesta del profesor:

> **NO**, porque estamos considerando muestras suficientemente grandes:
> n₁ = 40 > 30  y  n₂ = 32 > 30.

Por el **Teorema Central del Límite**, con muestras grandes se puede usar Z aunque σ
sea desconocida, reemplazando σᵢ por Sᵢ:

```
Z_obs = (X̄₁ − X̄₂) / √(S₁²/n₁ + S₂²/n₂)
      = misma fórmula con S en lugar de σ
      = 3,53   (mismo valor, los números coinciden)
```

La conclusión NO cambia: se rechaza H₀ al 1%.

**Nota:** En este caso los valores numéricos de S₁ y S₂ son iguales a los de σ₁ y σ₂,
por lo que el estadístico es idéntico. En un caso general con S ≠ σ, el estadístico
cambiaría numéricamente pero el procedimiento sería el mismo (Z con S, TCL).

---

## Ejercicio 3 · Efectividad de anuncio en dos ciudades

### Enunciado
Un comerciante realizó un estudio comparando la efectividad de un anuncio en dos ciudades.
Encuesta de n = 1.000 personas en cada ciudad:

- p̂₁ = 0,18 (ciudad 1)
- p̂₂ = 0,14 (ciudad 2)

**a)** IC del 95% para la diferencia p₁ − p₂.

**b)** Concluir sobre H₀: p₁ = p₂ vs H₁: p₁ ≠ p₂ a partir del IC anterior.

**c)** Prueba de hipótesis: H₀: p₁ − p₂ ≤ 0,1 vs H₁: p₁ − p₂ > 0,1. α = 5%.

**d)** Conclusión en contexto según ítem c).

---

### Solución del profesor (página 6)

#### Parte a) — IC 95% para p₁ − p₂

Error estándar de la diferencia (proporciones separadas — NO combinadas, eso es solo para PH):
```
d.e.(p̂₁ − p̂₂) = √(p̂₁·q̂₁/n₁ + p̂₂·q̂₂/n₂)
                = √(0,18·0,82/1000 + 0,14·0,86/1000)
                = √(0,1476/1000 + 0,1204/1000)
                = √(0,0001476 + 0,0001204)
                = √0,000268
                = 0,0164
```

Intervalo:
```
IC 95%(p₁−p₂) = (p̂₁−p̂₂) ± Z_{0,025} · d.e.(p̂₁−p̂₂)
              = 0,04 ± 1,96 · 0,0164
              = 0,04 ± 0,0321
              = (0,0079 ; 0,0721)
              ≈ [0,01 ; 0,07]   (como escribe el profesor)
```

---

#### Parte b) — Concluir sobre H₀: p₁=p₂ desde el IC

```
El 0 NO pertenece al IC(p₁−p₂; 95%) = (0,0079 ; 0,0721)
→ Se rechaza H₀: p₁=p₂ al nivel del 5%
```

Razonamiento: Si el IC para p₁−p₂ no contiene el 0, hay evidencia de que las proporciones
son distintas (rechazamos la hipótesis de igualdad).

---

#### Parte c) — PH: H₀: p₁−p₂ ≤ 0,1 vs H₁: p₁−p₂ > 0,1 · α = 5%

Estadístico (cola derecha, δ₀ = 0,1):
```
Z_c = [(p̂₁ − p̂₂) − 0,1] / d.e.(p̂₁ − p̂₂)
    = (0,04 − 0,1) / 0,0164
    = −0,06 / 0,0164
    = −3,659  ≈  −3,65
```

Valor crítico (cola derecha, α = 0,05):
```
Z_{0,95} = 1,65
Región de rechazo: Z_c > Z_{0,95} = 1,65
```

Verificación:
```
Z_c = −3,65 < 1,65  →  No está en la región de rechazo
```

**Conclusión parte c):**
> No se rechaza H₀: p₁ − p₂ ≤ 0,1 al nivel del 5%.

---

#### Parte d) — Conclusión en contexto

> La diferencia de proporciones de personas que leyeron el anuncio entre ambas ciudades
> **no supera el 10%**. No hay evidencia suficiente para afirmar que la diferencia es
> mayor a 0,1 (10 puntos porcentuales).

---

## Resumen de decisiones clave del listado 4

| Ejercicio | n | σ conocida | Distribución usada | Resultado |
|-----------|---|------------|--------------------|-----------|
| 1 · medias | n₁=n₂=60 | NO (usa S) | **Z con Sp** (TCL, n≥30) + F test previo | No rechaza H₀ |
| 2a · medias | n₁=40, n₂=32 | SÍ (σ₁,σ₂ dados) | **Z** | Rechaza H₀ |
| 2b · medias | n₁=40, n₂=32 | NO (usa S) | **Z con S** (TCL, n≥30) | No cambia |
| 3a · IC proporciones | n=1000 | — | Z (proporción) | IC = (0,008 ; 0,072) |
| 3b · PH proporción | n=1000 | — | Inferencia desde IC | Rechaza H₀ |
| 3c · PH proporción | n=1000 | — | Z (δ₀=0,1, cola derecha) | No rechaza H₀ |

## Notas pedagógicas extraídas de la solución

1. **Ejercicio 1 tiene un paso extra:** aunque n≥30 (TCL), el profesor IGUAL verifica
   igualdad de varianzas con prueba F antes de calcular Sp. Es su metodología estándar
   para 2 poblaciones con σ desconocida.

2. **Ejercicio 1 usa δ₀ = 20 (no cero):** la fórmula del estadístico es
   `(X̄₁−X̄₂−20) / SE`, no `(X̄₁−X̄₂) / SE`. Ojo con esto en el certamen.

3. **La afirmación va en H₀ (no en H₁):** el profesor pone lo que la empresa AFIRMA
   como H₀ y prueba si puede rechazarse. Si no se rechaza, la afirmación es
   consistente con los datos.

4. **Ejercicio 2b es la aplicación directa de la regla n≥30:** la respuesta es
   "No cambia, porque n₁=40>30 y n₂=32>30". Es el ejemplo perfecto de por qué
   se estudia el TCL.

5. **Ejercicio 3b usa el IC para concluir PH:** si 0 ∉ IC(p₁−p₂), se rechaza
   H₀: p₁=p₂. Este atajo ahorra calcular el estadístico de prueba.
