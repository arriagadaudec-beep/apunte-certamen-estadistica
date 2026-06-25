# Plan: alinear el paso "Test F" — Hipótesis adopta el lenguaje de Intervalos

## Objetivo
`intervalos_2pob.html` (Caso F) ya usa el vocabulario correcto: **"F crítico"**
y **"cociente muestral"**. Se ajusta **`prueba_hipotesis.html`** (l4ej1, paso
previo "Prueba F de igualdad de varianzas") para que use ese mismo
vocabulario, y se reordenan sus pasos en un solo flujo continuo. Así
Hipótesis se lee como un calco de Intervalos.

No se toca la lógica matemática (ya es correcta) — solo se renombra y
reordena. `intervalos_2pob.html` Caso F **no se modifica**, es el modelo a
imitar.

## Cambios de vocabulario en `prueba_hipotesis.html` (l4ej1, ~líneas 627–669)

| Texto actual | Texto nuevo |
|---|---|
| "Límite superior" | **"F crítico superior"** |
| "Límite inferior" | **"F crítico inferior"** |
| "Intervalo de no rechazo" | mismo nombre, pero escrito como $(F_{crít,\,inf}\;;\;F_{crít,\,sup})$ |
| $F_{obs}=S_1^2/S_2^2$ | $F_{obs}\;(\text{cociente muestral})=S_1^2/S_2^2$ — la aclaración entre paréntesis se agrega cada vez que aparece $F_{obs}$ |

## Reordenamiento de pasos — ahora como "Paso 0"

Se renombra todo el bloque a **"Paso 0 · Verificar si las varianzas son
iguales"** (se ejecuta *antes* del Paso 1 de H₀/H₁ del test principal — de
ahí el número 0). Se usa **siempre que el enunciado no diga explícitamente
"varianzas iguales/distintas"**, es decir, cuando hay que averiguarlo con el
propio $F_{obs}$.

**Antes** (mezclado: una caja de fórmula con $F_{obs}$ aparece *antes* de los
grados de libertad, y luego una nota numerada 1–6 que junta grados de
libertad, percentiles, límites e intervalo, con la comparación final en una
tercera caja separada):

1. Hipótesis del paso previo
2. $F_{obs}$ (caja de fórmula aislada)
3. Grados de libertad (dentro de la nota)
4. Percentiles (dentro de la nota)
5. Límite superior (dentro de la nota)
6. Límite inferior (dentro de la nota)
7. Intervalo de no rechazo (dentro de la nota)
8. Comparación final (caja de fórmula aparte)

**Después** — un solo bloque "Paso 0", con 3 sub-pasos numerados 0.1, 0.2,
0.3 y luego la verificación final:

- **Paso 0 · Verificar si las varianzas son iguales o no (usando $F_{obs}$, cuando no te las dan)**
  - **0.1 — Dividir varianzas**: calcular el cociente muestral $F_{obs}=S_1^2/S_2^2$.
  - **0.2 — Calcular F crítico superior**: grados de libertad ($gl_1=n_1-1$, $gl_2=n_2-1$), percentil $1-\alpha/2$, lectura directa en la tabla F.
  - **0.3 — Calcular F crítico inferior**: propiedad reciproca, $F_{crít,\,inf}=1/F_{crít,\,sup}$.
  - **Verificación**: ¿$F_{obs}$ está entre $F_{crít,\,inf}$ y $F_{crít,\,sup}$? Si sí → varianzas iguales (usar $S_p$). Si no → varianzas distintas (Welch).

Las hipótesis formales del test F ($H_0^F:\sigma_1^2/\sigma_2^2=1$) quedan
como nota aclaratoria dentro de 0.1, no como un paso numerado aparte —
para no romper la secuencia 0.1 → 0.2 → 0.3 → verificación que pediste.

## Agregado puntual: notas cruzadas

En `prueba_hipotesis.html` (l4ej1, después de la conclusión del Test F):

> "Ver el mismo Test F resuelto como Intervalo de Confianza en
> [IC · 2 Pob. → Caso F](intervalos_2pob.html#casef)."

En `intervalos_2pob.html` (Caso F, al final), simétricamente:

> "Compara este procedimiento con el paso previo del Test F en
> [Prueba de Hipótesis → L4 Ejercicio 1](prueba_hipotesis.html#l4ej1):
> mismos pasos, mismo vocabulario."

## Alcance — qué NO cambia
- No se modifican los resultados numéricos (siguen siendo F_obs = 0,735,
  F crítico superior = 1,96, F crítico inferior = 0,510, conclusión: no se
  rechaza H₀).
- No se modifica el Caso F de `intervalos_2pob.html` ni los Ejemplos 1/2
  resueltos (asfalto, accidentes).
- No se toca `matriz_ph_ic.html` en este cambio.

## Archivos a editar
1. `prueba_hipotesis.html` — reescribir el bloque "Paso previo · Prueba F de
   igualdad de varianzas" en l4ej1 (vocabulario + reordenamiento) y agregar
   nota de enlace cruzado.
2. `intervalos_2pob.html` — agregar 1 nota de enlace cruzado en Caso F (sin
   tocar el resto de la sección).

¿Apruebas este plan para implementarlo?
