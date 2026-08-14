# Revisión matemática / Mathematical Peer Review

**Español:** Revisión desde cero sobre extracciones `pdftotext -layout -enc UTF-8` de los 9 PDFs originales. Cada documento fue leído íntegramente y auditado teorema por teorema, definición por definición, prueba por prueba. La revisión del octavo documento (Locality, Soft Causal Cones, and Informational Limits of Agency) incluye además verificación numérica independiente y auditoría adversarial. La revisión del noveno documento (Teoría de Conservación de Óptimos y Complejidad) incluye además verificación simbólica asistida por computadora (SymPy) y auditoría adversarial.

**English:** Review from scratch over `pdftotext -layout -enc UTF-8` extractions of the 9 original PDFs. Each document was read in full and audited theorem by theorem, definition by definition, proof by proof. The review of the eighth document (Locality, Soft Causal Cones, and Informational Limits of Agency) also includes independent numerical verification and adversarial auditing. The review of the ninth document (Theory of Conservation of Optima and Complexity) also includes computer-assisted symbolic verification (SymPy) and adversarial auditing.

---

## Español

### 1. A Unique Encoding of Satisfying Assignments for Balanced CNFs
(3 páginas, 123 líneas extraídas)

#### Veredicto
**Matemáticamente correcto. Sin errores.**

#### Inventario
- **Teorema 3.1** (Ecuación SAT balanceada). `S = Σ_C 2^{T(C)}` donde `T(C) = Σ_{v_i=1} 2^{n-i}`. Para CNFs balanceadas, la expansión binaria de `S` (con ≥2ⁿ bits) codifica la tabla de verdad: bit 1 = asignación insatisfactoria.

#### Verificado correcto
- Convención `0 = True, 1 = False` (línea 63): consistente en todo el documento.
- Vector de signos: `v_i = 1` si `+i ∈ C`, `v_i = 0` si `−i ∈ C`. Asignación falsificante: `a_C(i) = 1` si `v_i = 1` (pues `+i` es falso con `x_i = 1` bajo la convención declarada), `a_C(i) = 0` si `v_i = 0`. Correcto.
- **Inyectividad del vector de signos**: en un CNF balanceado cada cláusula contiene exactamente un literal por variable, luego `v(C)` determina la cláusula unívocamente: `C = {+i : v_i = 1} ∪ {−i : v_i = 0}`. Dos cláusulas distintas tienen, por tanto, vectores de signos distintos. Como `T: {0,1}^n → {0,…,2^n−1}` es biyectiva, los exponentes `T(C)` son todos distintos y `S = Σ 2^{T(C)}` **nunca** tiene acarreos. La hipótesis «no repeated clauses» (línea 90) es automática para CNFs balanceadas (la fórmula es un conjunto de cláusulas); el paréntesis del paper es redundante, no un gap.
- `T(C) = Σ v_i 2^{n-i}` es exactamente el número binario de la asignación falsificante. `2^{T(C)}` marca un bit único.
- La prueba en tres pasos (encoding, asignación falsificante única, formación de `S`) es sólida.

#### Hallazgos
| # | Tipo | Descripción | Línea |
|---|------|-------------|-------|
| 1 | Menor | La línea de autor dice literalmente «Oscar Riveos» (verificado vía `pdftotext -layout` directo del PDF), mientras el mismo documento usa «oscar.riveros@gmail.com» (línea 4) y «Riveros' Theorem» (línea 56). Inconsistencia interna real del PDF: falta la «r». | 2 |

---

### 2. Autorreferencia Segura en Familias Dinámicas de Estados
(30 páginas, 1751 líneas extraídas)

#### Veredicto
**Matemáticamente riguroso. Sin errores.**

#### Inventario de resultados principales
1. **Teorema 4.4** — Existencia y finitud de la velocidad crítica local `ν_c^{µ̄}(z,ρ)` en cada fibra.
2. **Teorema 5.1** — Uniformidad: equivalencia entre cota universal `∃ν_* ∀(z,ρ): ν_c ≤ ν_*` y condición `∃ν_*: Λ(ν_*) + B^{µ̄} ≥ Γ` en todas las fibras.
3. **Teorema 5.3** — Divergencia global: equivalencia entre `sup ν_c = ∞` y existencia de estados con margen arbitrariamente grande.
4. **Teorema 5.6** — Divergencia alcanzable: misma caracterización restringida al conjunto `Reach(z₀,ρ₀)`.
5. **Corolario 5.8** — Caso separable `Λ(ν) = A·Φ(ν) + C`: fórmula explícita `ν_c = Φ⁻¹((Γ−B−C)/A)`.
6. **Teorema 6.5** — Invariancia de tubos seguros móviles `T_c` bajo la política ISS.
7. **Teorema 6.7** — Estabilidad práctica exponencial en variable Lyapunov: `F_t ≤ max(q^t F₀, χ(µ̄))`.
8. **Corolario 6.8** — Atracción geométrica al tubo bajo comparación `α(dist) ≤ max(F−χ(µ̄), 0)`.
9. **Teorema 7.8** — Criterio de no-retorno: conjunto invariante disjunto de `T` ⊆ complemento de `Capt(T)`.
10. **Teorema 8.5** — Radio local finito por holonomía mínima: `R_ε^{safe} ≤ min(2r_h, 2√(ε/η_h))`.

#### Verificado correcto
- **Axiomas 3.1–3.8** (monotonía, capacidad finita, transporte regular, compatibilidad, ISS Lyapunov, holonomía): cada uno justificado por necesidad mediante contraejemplos en las Proposiciones 3.10–3.15. Los contraejemplos son correctos (e.g., `Λ(ν) = 2 + sin ν` rompe la estructura intervalar sin monotonía; `Γ = ∞` trivializa la velocidad crítica).
- **Teorema 4.4**: `g(ν) = Λ(ν) + B^{µ̄}` no decreciente, `g(0) < Γ`, `g(ν) → ∞` → `S = [0, ν_c)` con `ν_c < ∞`. La prueba de que `ν_c ∉ S` (por continuidad a derecha) y `S = [0, ν_c)` es rigurosa. En continuidad, `g(ν_c) = Γ`. ✓
- **Teorema 5.1**: `(U2)⇒(U1)`: `g(ν_*) ≥ Γ` + monotonía → `ν ≥ ν_*` no es seguro → `ν_c ≤ ν_*`. `(U1)⇒(U2)`: si `g(ν_*) < Γ`, por continuidad a derecha `∃ε > 0: g(ν_*+ε) < Γ` → `ν_*+ε` seguro → `ν_c > ν_*`, contradicción. ✓
- **Teorema 6.5**: `F_{ρ_{t+1}}(z_{t+1}) ≤ max(θ(F_{ρ_t}(z_t)), χ(d_R))`. Con `F_t ≤ c`, `θ(s) ≤ s`, `χ(µ̄) ≤ c`: `F_{t+1} ≤ max(θ(c), χ(µ̄)) ≤ max(c, c) = c`. Inducción. ✓
- **Teorema 6.7**: `θ(s) ≤ qs` + inducción: `a_{t+1} ≤ max(q a_t, c)`. `a_t ≤ max(q^t a₀, c)` probado por inducción (el paso `max(q·max(q^t a₀, c), c) = max(q^{t+1} a₀, qc, c)` usa `qc ≤ c`). ✓
- **Teorema 7.8**: `E ∩ T = ∅`, `E` invariante → ninguna trayectoria desde `E` captura `T` → `E ⊆ Z \ Capt(T) = H(T)`. ✓
- **Teorema 8.5**: elige `e ∈ E_{z,ρ}\{0\}` (existe por Axioma 3.8 H1: `E_{z,ρ} ≠ {0}`). `u = v = (r/(2|e|))·e` → `|u| = |v| = r/2`. Cota de área: `Res(u,v) ≥ η_h·(r/2)² = η_h·r²/4`. Para `ε`-seguridad: `η_h·r²/4 ≤ ε` → `r ≤ 2√(ε/η_h)`. Supremo + cota `2r_h`. ✓

#### Hallazgos
| # | Tipo | Descripción | Línea |
|---|------|-------------|-------|
| 1 | Menor | `D_η` mencionado en Prop 3.12 pero definido recién en §0.7 (línea 1361). Referencia hacia adelante. | 520 → 1361 |
| 2 | Menor | `∂Capt(T)` y `∂_T Viab(T)` introducidos en Def 7.4 como nombres para los horizontes dinámicos, pero no usados en ningún teorema posterior. | 1337–1339 |

---

### 3. Coherent Flow: A Companion Note to Epistemic Geometry
(8 páginas, 374 líneas extraídas)

#### Veredicto
**Riguroso y correcto. Sin errores ni gaps.**

#### Inventario de resultados
1. **Teorema 2.2** — Existencia de islas coherentes (mínimos locales de `F` en `K` finito).
2. **Teorema 2.4** — Descenso determinista `U`: `F(U(K)) ≤ F(K)`, estricto si `U(K) ≠ K`.
3. **Corolario 2.5** — Terminación finita de toda órbita de `U`.
4. **Teorema 3.2** — Balance detallado del kernel Metropolis–Hastings para `π(K) ∝ e^{−λF(K)}`.
5. **Proposición 4.2** — Curvatura epistémica KL: `κ_M(p) = inf_{q∈M} D_KL(p∥q)`; caso separable `I(A;B)`.
6. **Teorema 5.3** — Identidad exacta de Lyapunov KL para flujo coherente continuo: `dE/dt = −Σ p_{ij} γ_{ij}² ≤ 0`.
7. **Proposición 5.4** — Equilibrio único `q^⋆ = r_i c_j` en la hoja de interfaz.
8. **Teorema 7.1** — Gödel I estándar, correctamente acotado a hipótesis clásicas.

#### Verificado correcto
- Todas las hipótesis son finitas y explícitas: `W` finito, `Ω` finito (`V^{At}`), `K` finito, `µ` con soporte completo. Sin objetos ideales no auditables.
- **Teorema 3.2**: verificación explícita de los dos casos (`r(K,H) ≤ 1` y `r(K,H) > 1`). Cancelación correcta de `Z_λ`. ✓
- **Teorema 5.3**: `h = Π_U h + γ` con `γ ⊥_p U`. `Σ p_{ij} γ_{ij} (Π_U h)_{ij}` = 0 por ortogonalidad. `Σ p_{ij} γ_{ij} = Σ_i (Σ_j p_{ij} γ_{ij}) = 0` por las ecuaciones normales de `Π_U`. Queda `dE/dt = −Σ p_{ij} γ_{ij}²`. ✓
- **Proposición 5.4**: `γ = 0` → `h_{ij} = a_i + b_j` → `p_{ij} = r_i c_j e^{a_i+b_j}`. Sumando sobre `j`: `r_i = r_i e^{a_i} Σ_j c_j e^{b_j}`. El factor `Σ_j c_j e^{b_j}` es constante en `i`; análogamente para columnas. Normalización fuerza factor global = 1 → `p = q^⋆`. ✓
- Separación de capas `[Proved]`, `[Model]` explícita y respetada.

#### Hallazgos
Ninguno.

---

### 4. Continuous Epistemic Geometry (cGCNF)
(13 páginas, 653 líneas extraídas)

#### Veredicto
**Riguroso y correcto. Sin errores ni gaps.**

#### Inventario de resultados principales
1. **Teorema 2.4** — Apertura de `Mod(Φ)` en la topología producto.
2. **Teorema 2.9** — Apertura conjunta en `(θ, x)` y apertura de `{θ : ∃x, x |= Φ_θ}`.
3. **Teorema 3.4** — Testigo interior ⇒ volumen positivo en ventana compacta.
4. **Teorema 3.6** — Semicontinuidad inferior de `v_K(θ) = µ(Mod(Φ_θ) ∩ K)` vía Fatou.
5. **Teorema 3.7** — Estimador Monte Carlo con cota de Hoeffding `2e^{−2Tη²}`.
6. **Lema 4.6** — `BoxDiff(P, R)`: descomposición disjunta de `P \ R` en ≤ 2n cajas (construcción lexicográfica de slabs).
7. **Teorema 4.9** — Compilación disjunta de `U(Φ) ∩ K` vía `AddBox` incremental.
8. **Teorema 4.11** — Barrera de fragmentación `2^n`: `Φ_n = ∧_i (x_i ∈ (0,⅓) ∨ x_i ∈ (⅔,1))` fuerza ≥ 2ⁿ cajas.
9. **Teorema 6.13** — Transferencia con margen: `E_{τ+ω(ε_N)} ⊆ E_τ^{(N)} ⊆ E_τ` para bancos finitos ε-net.

#### Verificado correcto
- **Teorema 2.4**: `Mod(ℓ) = (f_ℓ ∘ π_{I_ℓ})⁻¹(U_ℓ)`, preimagen continua de abierto → abierto. Uniones e intersecciones finitas preservan apertura. ✓
- **Teorema 2.9**: `S = {(θ,x): x |= Φ_θ}` abierto en producto. `E = proj_Θ(S)` abierto (unión de secciones abiertas). ✓
- **Lema 4.6**: construcción de slabs `L_i` (abajo), `U_i` (arriba) con prefijo congelado `[α_j, β_j]` para `j < i`. Tres claims: contención en `P \ R̃`, cubrimiento (índice lexicográfico `i^⋆`), disjunción (slabs de distinto índice no intersectan: el índice `i` tiene coordenada `i` fuera de `[α_i, β_i]`; el índice `j > i` la tiene dentro). ≤ 2n slabs. ✓
- **Teorema 4.11**: `Mod(Φ_n) = ∏_{i=1}^n ((0,⅓) ∪ (⅔,1))` = 2ⁿ componentes conexas (cajas abiertas). Toda caja es conexa → contenida en una componente → al menos 2ⁿ cajas para cubrir. ✓
- **Teorema 6.13**: inclusión derecha `E_τ^{(N)} ⊆ E_τ`: `S_N ⊆ S_∞` → `min_{S_N} F_S ≥ inf_{S_∞} F_S`. Si `min_{S_N} F_S(θ) < −τ`, entonces `inf_{S_∞} F_S(θ) ≤ min_{S_N} F_S(θ) < −τ`. Inclusión izquierda: `F_S(θ) < −τ−ω(ε_N)` + `|F(θ,S)−F(θ,S_N)| ≤ ω(ε_N)` → `F_{S_N}(θ) < −τ`. ✓ La hipótesis del módulo `ω` uniforme en `θ` se da explícitamente como condición (iv), no se pretende deducir de continuidad conjunta sola. ✓
- **Zona gris** (Def 6.16): `G = K \ (Mod(Φ_common) ∪ Mod(Φ_sep))`, complemento estándar de las fases certificadas. Sin el vicio de inclusión de la otra obra (Finite-Bank). ✓

#### Hallazgos
Ninguno.

---

### 5. Epistemic Geometry of Closure (SCE-IM)
(18 páginas, 710 líneas extraídas)

#### Veredicto
**Riguroso en el nivel declarado. Sin errores. Las etiquetas `[Proved]`/`[Model]` son honestas.**

#### Inventario de resultados
1. **Definición 2.1** — Sistema SCE-IM: 10-tupla `(S, O, Ω, T, J, err, µ, K, F, Φ)` con dientes tipados `D_τ ∈ Σ_Ω` y zipper `◁`.
2. **Proposición 3.2** — Invariancia de curvatura bajo isomorfismo rígido: `κ'(g(o)) = κ(o)`.
3. **Lema 4.4** — Monotonía de `κ_R(o)` en `R` y límite `inf_R κ_R = κ`.
4. **Teorema 6.2** — Estabilidad Lipschitz de `κ`: `d_∞ ≤ δ` → `|κ − κ'| ≤ δ`.
5. **Proposición 6.4** — Invariancia de signo bajo métricas equivalentes: `c_1 κ_δ ≤ κ_d ≤ c_2 κ_δ`.
6. **Teorema 7.9** — Completitud operacional zipper `[Model]`: igualdad de firma `Σ_zip` + ZT + ZM + RZ ⇒ equivalencia filtrada-dinámica.
7. **Teorema 8.3** — Completitud con recursos `[Model]`.
8. **Teorema 8.4** — Estabilidad de `κ_R`: cota unilateral `κ'_R(o') ≤ κ_R(o) + δ`; simetría requiere control bidireccional. Remark 8.5 corrige explícitamente una versión previa.

#### Verificado correcto
- **Definición 2.2**: semántica de dientes vía `D_τ ∈ Σ_Ω`. Satisfacción de diente `τ` por estado `σ` en ventana `K`: `µ(J(σ) ∩ D_τ ∩ K) = µ(J(σ) ∩ K)`. Bien definida. ✓
- **Proposición 3.2**: `κ'(g(o)) = inf_σ' err'(σ', g(o))`. Por biyectividad de `h`, `σ' = h(σ)`. `err'(h(σ), g(o)) = err(σ, o)`. Infimos iguales. ✓
- **Lema 4.4**: anidamiento `{σ: ρ(σ) ≤ R} ⊆ {σ: ρ(σ) ≤ R'}` para `R ≤ R'` → `κ_{R'} ≤ κ_R`. `inf_{R≥0} κ_R = κ`: `κ_R ≥ κ` (subconjunto); para cada `σ`, tomo `R = ρ(σ)`, luego `κ_R ≤ err(σ,o)`, tomo ínfimo en `σ`. ✓
- **Teorema 6.2**: el argumento `ε`-δ con homeomorfismo `h_ε` que aproxima `d_∞` es correcto. Bidireccionalidad vía `h_ε⁻¹`. ✓
- **Remark 8.5**: *«In a previous version, a symmetric bound |κ_R − κ'_R| ≤ δ was stated assuming only a map h: S → S'. That form is false in general if h(S_{≤R}) is not surjective onto S'_{≤R}.»* Corrige un error genuino de versión anterior. La formulación actual separa correctamente cota unilateral (siempre válida) de simetría (requiere `g: S' → S` en dirección opuesta). Esto demuestra rigor autocrítico. ✓

#### Hallazgos
Ninguno.

---

### 6. Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions Across Logic, Computation, and Physics
(20 páginas, 1131 líneas extraídas)

#### Veredicto
**Certificación de solidez.** El artículo es matemáticamente correcto en todas sus afirmaciones etiquetadas `[Proved]`. Las afirmaciones etiquetadas `[Metaformal]` y `[Model]` están apropiadamente identificadas como especulativas o condicionadas a hipótesis de modelo. Las demostraciones de los teoremas centrales de unificación (8.7 y 8.8) son lógicamente válidas. No se identifica ningún error matemático fatal.

#### Corrección de errores en revisiones previas
Dos revisiones previas identificaron un supuesto «error fatal» en la interfaz epistémica DSOP. La lectura directa del PDF compilado demuestra que dichas identificaciones son incorrectas:

1. **Diferencia simétrica en la interfaz DSOP (Def. 8.4)** — el texto define `err(U) = |φ(U) ∆ o| = |φ(U) \ o| + |o \ φ(U)|`, donde `∆` denota diferencia simétrica (línea 871), y `err(U) = 0 ⟺ φ(U) = o` como conjuntos (línea 874). La corrección que las revisiones previas recomendaban **ya está presente en el texto original**. El contraejemplo propuesto (`U = {Q(00)}` con `o = Ω₂`) no funciona: `|{00} ∆ Ω₂| = 3 ≠ 0`.
2. **Proposición 8.10 (DSOP/DNF)** — el texto afirma explícitamente: «dnf(f) ≤ dsop(f) means a DNF lower bound dnf(f) ≥ L implies the corresponding DSOP lower bound dsop(f) ≥ L, but the converse is not true: dsop(f) ≥ L alone places no lower bound on dnf(f)» (líneas 1006–1010). La dirección de implicación es DNF → DSOP; el texto niega explícitamente el converso que la revisión previa le atribuye.
3. **Teorema 5.8 (DRP)** — la demostración invoca DRP explícitamente: «By DRP, the orbit (T^k(σ_n)) has an accumulation point σ_n* with err(σ_n*) = inf_k err(T^k(σ_n)) ≤ err(σ_n) < 1/n» (líneas 491–493). Que la conclusión `κ_S = 0` se siga también de (a) sin DRP es un asunto de estilo de demostración, no un error.
4. **Teorema 5.11 (obstrucción Gödel)** — la subsección §5.3 completa está etiquetada `[Metaformal]` (línea 503). El teorema es un esquema diagonal gödeliano condicionado a la existencia de un predicado `Prov_{0,r}` gödel-admisible; el texto no afirma haberlo construido para un sistema concreto. La etiqueta es apropiada.

**Nota de cotejo:** la numeración de esta sección fue verificada contra el PDF compilado. Las revisiones previas usaban la numeración de un borrador anterior: Def. 8.5 → 8.4, Teo. 8.6 → 8.7, Teo. 8.7 → 8.8, Prop. 8.9 → 8.10, Prop. 8.10 → 8.11, Teo. 8.12 → 8.13, Teo. 8.13 → 8.14, Teo. 2.8 → 2.9.

#### Evaluación por módulos
| Módulo | Veredicto |
|--------|-----------|
| A (§2) Física discreta verificable por SAT `[Proved]` | Correcto. GCNF y one-hot (Def. 2.1–2.2, Prop. 2.3), separación solver/verificador (Prop. 2.5), Gauss–Bonnet equilátero (Teo. 2.9: la identidad `Σ_v χ(v) = 6χ` es manipulación directa de `3F = 2E`, explícitamente restringida al caso equilátero), cono causal Booleano (Teo. 2.12: inducción sobre distancia en grafo). |
| A′ (§3) Ecuación SAT `[Proved]` | Correcto. Falsificador único e índice (Def. 3.1–3.2), Teorema 3.3. Remark 3.4: auto-evaluación precisa y honesta. |
| B (§4) COVERTRACE `[Proved]` | Correcto. CubeDiff (Alg. 1, Lema 4.5: la elección no-determinista no afecta la cota), AddCube (Alg. 2, Teo. 4.7: invariancia disjunta preservada), **barrera de paridad** (Teo. 4.8: todo subcubo con coordenada libre contiene igual número de asignaciones pares e impares; cota `2^{n−1}` ajustada), colapso PH condicional (Teo. 4.9), compilación afín (Def. 4.10–4.11, Teo. 4.13: PARITY es un único subespacio afín). |
| C (§5) Curvatura epistémica `[Metaformal]` + `[Proved]` | Correcto. Definiciones 5.1–5.6 bien puestas (la topología en `L` puede tomarse discreta: todo subconjunto es Borel). DRP (Def. 5.7) postulado, no demostrado — el texto no lo reclama. Teo. 5.8 válido (la conclusión también se sigue de (a) sin DRP, pero `A∧B⇒C` es verdadera si `A⇒C`). Teo. 5.11 esquema diagonal correcto. §5.4 `[Metaformal]`. §5.5 definición operacional (`τ_A` como medida de compresión), no teorema. |
| D (§6) Espacio Métrico en Capas `[Model]` + `[Proved]` | Correcto. Capas, strain y curvatura (Def. 6.1–6.2), ecuación de movimiento Euler–Lagrange (Teo. 6.4: derivación estándar), Procrustes unitario (Teo. 6.6: resultado estándar Golub–Van Loan), materialización (Def. 6.8) `[Model]`. |
| E (§7) Localidad y agencia `[Model]` + `[Proved]` | Correcto. Lieb–Robinson (Teo. 7.1) citado estándar; Duhamel (Lema 7.3); agencia como distinguibilidad (Def. 7.4, Teo. 7.5: esbozo plausible); incompresibilidad operacional (Lema 7.7, Teo. 7.9); curvatura operacional (Def. 7.10), sin equivalencia afirmada con `κ_S`. |
| §8 Interrelación y unificación | Correcto. Indistinguibilidad operacional (Teo. 8.1); reducción a certificados (Teo. 8.3); **interfaz DSOP (Def. 8.4)**: diferencia simétrica, `err = 0 ⟺ φ(U) = o`; **Trilema (Teo. 8.7)** `[Metaformal]`: barrera de paridad (rama 1) sólida, rama 2 válida (`err = 0` fuerza igualdad exacta de conjuntos), rama 3 depende del modelo físico de §7, apropiadamente identificada; **Obstrucción unificada (Teo. 8.8)** `[Metaformal]`: válida (la redundancia parcial entre hipótesis no invalida el teorema); Prop. 8.10 (DSOP/DNF) correcta; Prop. 8.11 (afín) correcta; Teo. 8.13 (`‖QP‖ < 1` ⇒ sin certeza simultánea ⇒ `κ > 0`) correcto; Teo. 8.14 (CHSH): `S` es 8-Lipschitz en TV, `sup_LHV ≤ 2`, `sup_QM = 2√2` ⇒ `ínf TV ≥ (2√2−2)/8 > 0`. Correcto. |

#### Observaciones menores (no afectan la solidez)
1. **Topología en `L`** (Def. 5.1, línea 430): no se especifica explícitamente; adoptando la discreta (todo subconjunto es Borel) la condición de medibilidad se satisface trivialmente. Se recomienda explicitarla.
2. **Redundancia parcial en el Teo. 5.8**: la conclusión `κ_S = 0` se sigue de (a) sin DRP (`err(σ_n) < 1/n` ⇒ `κ_S ≤ 1/n` para todo `n`). El enunciado podría refinarse para que DRP sea lógicamente necesaria.
3. **Constructividad de DRP** (Def. 5.7, línea 478): la única construcción concreta esbozada es el descenso de espejo proyectado (§5.4 / Remark 5.14, línea 568). No se demuestra existencia para sistemas formales no triviales; los teoremas son condicionales, así que su validez no se afecta.
4. **Protocolo local de paridad** (Teo. 8.7, rama 3): se requiere especificar el Hamiltoniano y la reducción del protocolo de verificación al formalismo de control de §7 para elevar la rama de `[Model]` a `[Proved]`.

#### Hallazgos
| # | Tipo | Descripción | Línea |
|---|------|-------------|-------|
| 1 | Menor | Topología en `L` no explicitada (Def. 5.1); se recomienda la discreta. | 430 |
| 2 | Menor | Teo. 5.8: DRP no es lógicamente necesaria para la conclusión `κ_S = 0`. | 491 |
| 3 | Menor | DRP (Def. 5.7): sin construcción para sistemas formales no triviales. | 478 |
| 4 | Menor | Teo. 8.7, rama 3 `[Model]`: protocolo local de paridad no especificado. | 891 |

---

### 7. A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding
(6 páginas, 256 líneas extraídas)

#### Veredicto
**Matemáticamente sólido. Sin errores fatales.** El teorema principal (Theorem 5.1, Generalized SAT Equation Theorem) es correcto, la construcción funciona para toda fórmula CNF y la prueba es lógicamente válida. No se encontró ningún error fatal que invalide las afirmaciones centrales del documento. Se detectaron tres defectos menores (expositivos, no matemáticos), detallados en los hallazgos.

#### Inventario
- **Teorema 5.1** (Ecuación SAT generalizada). `S = OR_{j=1}^m OR_{M′⊆MC_j} 2^{B(C_j) + Σ_{i∈M′} 2^{N−i}}`, con `B(C) = Σ_{i∈PC} r_i(C)·2^{N−i}` (`r_i(C) = 0` si `+i ∈ C`, `r_i(C) = 1` si `−i ∈ C`). La expansión binaria de `S` con `2^N` bits codifica exactamente la tabla de verdad de `F`: el bit en la posición `pos(a)` es 1 si y solo si `a` no satisface `F`.
- **Remark 3.1**: en el caso balanceado `PC = {1,…,N}` y `MC = ∅`, con lo que `S_C = 2^{B(C)}` recupera la codificación original.
- **§7.2**: alternativa aritmética con base `b > m` (máximo de cláusulas que pueden compartir una posición falsificante) que evita los acarreos a costa de perder la representación binaria.

#### Verificado correcto
- `pos(a) = Σ a_i·2^{N−i}` es biyección `{0,1}^N → {0,…,2^N−1}`; cada posición corresponde a un bit distinto de la expansión. ✓
- `r_i(C)` identifica correctamente el valor que falsifica cada literal, y `B(C) = Σ_{i∈PC} r_i(C)·2^{N−i}` codifica los bits fijos del subcubo falsificante. ✓
- `S_C = OR_{M′⊆MC} 2^{B(C) + Σ_{i∈M′} 2^{N−i}}` captura exactamente `Fals(C)`: cada subconjunto `M′` de variables ausentes produce un exponente distinto (sumas de pesos distintos), de modo que `S_C` marca un bit por cada asignación falsificante de la cláusula. ✓
- `S = OR_j S_{C_j}` implementa la unión de conjuntos falsificantes; el OR bit a bit es libre de acarreos (idempotencia `1∨1 = 1`), incluso cuando cláusulas distintas comparten asignaciones falsificantes — exactamente el caso en que la suma aritmética del documento original falla. ✓
- Sin overflow: el exponente máximo es `B(C) + Σ_{i∈MC} 2^{N−i} ≤ 2^N−1`; el bit más significativo está siempre dentro de los `2^N` bits requeridos. ✓
- La inyectividad `F → S` no es afirmada por el documento (no forma parte del teorema); sí se afirma y se verifica que `S` codifica unívocamente la tabla de verdad. ✓
- **Verificación computacional**: N=3 exhaustivo (todas las `2^26 ≈ 67M` fórmulas CNF posibles, vía los 26 tipos de cláusulas combinados por OR); N=4: 7500+ fórmulas aleatorias; N=5: 200+; casos extremos (fórmula vacía `S = 0`, cláusulas contradictorias, cláusulas duplicadas, cláusulas unitarias, fórmula completa). Cero contraejemplos; la codificación con suma aritmética falla (como se esperaba) en fórmulas con asignaciones falsificantes compartidas. ✓
- **Comparación con el documento de referencia**: el original usa suma aritmética `Σ_C 2^{T(C)}`, libre de acarreos solo para CNFs balanceadas (inyectividad del vector de signos); la generalización sustituye la suma por OR bit a bit, siempre libre de acarreos. Los patrones de bits entre ambos documentos están invertidos (`v_i = 1` para `+i` vs `r_i = 0` para `+i`), pero las semánticas subyacentes son isomorfas. ✓

#### Hallazgos
| # | Tipo | Descripción | Línea |
|---|------|-------------|-------|
| 1 | Menor | Ambigüedad de la convención: el documento declara *«0 represents True and 1 represents False when evaluating literals»*, pero la Definición 2.3 y todos los ejemplos usan semántica estándar (0=False, 1=True) para los valores de las variables, reservando la convención para los *resultados* de evaluación (bit 1 = insatisfactorio). La frase *«when evaluating literals»* es ambigua para un lector que venga del documento balanceado, donde la misma frase significa que las variables mismas usan 0=True. El documento es internamente consistente bajo la interpretación correcta; la redacción debería precisarse. | 73 |
| 2 | Gap | Cláusulas tautológicas no tratadas: si una cláusula contiene simultáneamente `+i` y `−i` para alguna variable, la Definición 2.3 es ambigua (ambas ramas aplican). Tal cláusula es una tautología (`Fals(C) = ∅`, `S_C = 0`) y puede eliminarse en preprocesamiento, pero el documento no menciona esta restricción implícita al dominio de fórmulas. | 92–97 |
| 3 | Menor | Profundidad del resultado: el teorema es consecuencia directa de (a) OR bit a bit = unión de conjuntos sobre posiciones de bit y (b) el conjunto falsificante de una CNF es la unión de los conjuntos falsificantes de sus cláusulas. La notación `2^{B(C) + Σ 2^{N−i}}` es un envoltorio aritmético para una operación conjuntista. El resultado es correcto, pero su presentación como «teorema» y «generalización» puede sobrestimar su contenido matemático no trivial. | 140–203 |

---

### 8. Locality, Soft Causal Cones, and Informational Limits of Agency. An axiomatic skeleton (nonlinear development) for local control and remote indistinguishability
(10 páginas · manuscrito del 25 de diciembre de 2025 · revisión del 12 de agosto de 2026)

#### Veredicto
**Matemáticamente sólido: certificación condicionada a correcciones editoriales obligatorias.** Todas las afirmaciones centrales (cota de Lieb–Robinson de doble suma, refinamiento geométrico `K_µ`, identidad de Duhamel a dos tiempos con flujo causal en el tiempo restante `T−s`, cota de influencia/agencia exponencialmente suprimida fuera del cono, y cierre de capacidad vía Holevo + Fannes–Audenaert) fueron verificadas de forma independiente — algebraica y numéricamente — y sobreviven a una auditoría adversarial dedicada. No se encontró ningún error algebraico, hipótesis oculta que invalide una afirmación principal ni contraejemplo que rompa las cotas.

**El manuscrito NO es aceptable en su forma actual por razones de integridad y precisión de atribución, no de matemática:**
1. El Apéndice C presenta opiniones de asistentes de IA (Gemini, Claude, Grok, GPT-5.2) como «reviews» y «editorial assessments», y contiene un «Final verdict: Accepted for publication / finalization» sin revista, editor ni revisor humano. Endoso editorial fabricado que debe eliminarse o re-etiquetarse explícitamente.
2. Atribución imprecisa de la Proposición 4.1: Barthel–Kliesch [5] cubre dinámica **Lindbladiana**, no el caso unitario; el caso unitario dependiente del tiempo lo cubre Kliesch–Gogolin–Eisert [6] (Thm. 1), cuyos coautores el manuscrito omite.
3. Autodescripciones infladas (Remark 4.1, C.2) y deficiencias menores de presentación.

En términos binarios: certificación de solidez matemática, condicionada a las correcciones editoriales obligatorias 1–3. El veredicto es independiente del «Accepted for publication» auto-otorgado en el Apéndice C del propio manuscrito; la matemática se verificó desde cero.

#### Inventario de afirmaciones principales
1. **C1 (LR).** Para interacción exponencialmente local (Supuesto 2.1), vale la cota de Lieb–Robinson de doble suma con parte positiva `e^{−µ[d(x,y)−v|t|]_+}` (Teorema 2.1) y su especialización volumétrica (Corolario 2.1).
2. **C2 (Geometría).** Refinamiento geométrico con constante explícita `K_µ = 1 + ∆e^{−µ}/(1−(∆−1)e^{−µ})` y escalado `min(|X|,|Y|)` (Proposición 2.1).
3. **C3 (Duhamel).** Identidad exacta a dos tiempos: `τ(c)_{T,0}(B) − τ(c′)_{T,0}(B) = i∫₀^T τ(c)_{s,0}([∆H(s), τ(c′)_{T,s}(B)])ds` (Lema 4.1), con flujo causal en el tiempo restante `T−s`.
4. **C4 (Influencia remota).** Control local acotado ⇒ influencia remota exponencialmente suprimida fuera del cono: si `d(C,R) > v′T + ℓ`, entonces `Ag_R(c,c′;T) ≤ K′_A|C||R| e^{−µℓ} ∫₀^T‖∆H(s)‖ds` (Teorema 4.1 → Corolario 4.1; Corolario 6.1 análogo para `Infl_R`).
5. **C5 (Capacidad).** Indistinguibilidad geométrica ⇒ cierre de capacidad: `I(M;Z) ≤ χ ≤ 2ε log(d_R−1) + h(2ε)` con `ε = O(e^{−µℓ})` (Teorema 5.1 + Proposición 5.1).
6. **C6 (Cono duro clásico).** Un autómata celular local tiene cono causal duro (influencia exactamente cero fuera) (Proposición 7.1).
7. **C7 (Operacional).** Las reglas de agencia/responsabilidad remota deben respetar los límites causales blandos salvo control «efectivamente omnipotente» (Definición 6.2, sección 6).

#### Verificado correcto
- **Definiciones (1.1–1.5, 4.1–4.4, 5.1–5.2):** estándar y correctas. Única observación: `ρ₀` se usa (Def. 4.4, Def. 6.1) sin definirse explícitamente (implícito en Def. 1.4) — laguna benigna. ✓
- **Teorema 2.1 / Corolario 2.1:** forma de doble suma estándar (Nachtergaele–Sims); la truncación con `[·]_+` es consecuencia trivial de la forma no truncada; Remark 2.2 honesto (dentro del cono la cota es no informativa). Normalización `v_LR ≲ 2J_µ/µ` correcta en la convención BHV. ✓
- **Proposición 2.1 (`K_µ`):** conteo de esferas `|S_n| ≤ ∆(∆−1)^{n−1}` y serie geométrica correctos, válida sii `µ > log(∆−1)` (condición impuesta por el enunciado). **Verificada numéricamente:** camino de 100 nodos, µ=1: `K_µ = 2.1639534…` coincide con `max_x Σ_y e^{−µd(x,y)}` a precisión de máquina (la cota es *tight* en el centro); caso asimétrico |X|=5, |Y|=100: simetría verificada. ✓
- **Proposición 4.1 (LR dependiente del tiempo):** etiquetada «(referenced)» honestamente; es teorema **verdadero y establecido** — Kliesch–Gogolin–Eisert (arXiv:1306.0716, Thm. 1) cubre el caso unitario dependiente del tiempo (el caso Hamiltoniano unitario es caso especial explícito), con el empaquetado estándar `min(1, e^{v|t−s|−µd}) ≤ 2e^{−µ[d−v′|t−s|]_+}` y cotas instantáneas `sup_t J_µ(t) ≤ J_µ + κe^{µ diam(C)} < ∞` con la misma µ. ✓ (enunciado) — ⚠ **atribución imprecisa** (Barthel–Kliesch trata Lindbladianos); faltan ~2 páginas de prueba para autocontención.
- **Lema 4.1 (Duhamel a dos tiempos):** verificado término a término (los 4 términos de `dF/ds` suman exactamente `i Uc(s,0)†[∆H(s), Uc′(T,s)†BUc′(T,s)]Uc(s,0)`; sin error de signo) y **numéricamente** (2 qubits, error máx ~10⁻⁵ con `dt = 2.5·10⁻⁵`, escalando linealmente con `dt`). La identidad es exacta, incluido el signo `+i` y el flujo `τ(c′)_{T,s}` en el tiempo restante. ✓
- **Teorema 4.1 (flujo causal T−s):** identidad de conjugación `[A, U†BU] = U†[UAU†, B]U` correcta. Nota de precisión (no es error): estrictamente la conjugación aterriza en el flujo **retrógrado** `τ(c′)_{s,T}`; conclusión idéntica (la cota LR vale en ambas direcciones con las mismas constantes y el intervalo mide `|T−s|`). ✓
- **Corolarios 4.1 / 6.1:** dualidad traza–norma (Lema 4.2, Helstrom) y factor ½ correctos (`K′_A = K_A/2`); condición del cono `d(C,R) > v′T + ℓ` verificada para todo `s ∈ [0,T]` (exponente ≤ `e^{−µℓ}`). ✓
- **Teorema 5.1 / Proposición 5.1:** cadena triangular `‖ρm−ρ̄‖₁ ≤ 4ε` y Fannes–Audenaert con parámetro `2ε` bajo `2ε ≤ 1−1/d_R` correctos (la restricción es conservadora respecto del teorema de Audenaert 2007, que vale para todo `δ ∈ [0,1]`; la conclusión asintótica no se afecta). Presupuesto `B ≤ 2κT` automático; `I(M;Z) ≤ χ` (Holevo) correctamente aplicado. ✓
- **Apéndice A / Proposición 7.1:** `J_µ^eff ≤ J_µ + κe^{µ diam(C)}` ✓ (verificado numéricamente por agente: igualdad exacta en cadena de 6 sitios); Remark A.1 honesto. Cono duro del autómata celular correcto y estándar; contraste blando/duro honesto. ✓

#### Verificaciones numéricas independientes (revisor)
| Verificación | Resultado |
|---|---|
| Lema 4.1 (Duhamel), 2 qubits, T=1, dt=2.5·10⁻⁵, 3 observables | error máx elemento ~3.7–9.7·10⁻⁶ (O(dt)) — **exacto** |
| Fannes–Audenaert, 3000 pares aleatorios, d=3 y d=5 | sin violaciones (peor margen −0.198 / −0.748) — **vale** |
| Teorema 5.1 (concentración + Holevo), d=4, ε=0.05 | ½‖ρm−ρ̄‖ ≤ 0.0104 ≤ 2ε; χ = 0.000878 ≤ 0.627 — **vale** |
| Prop 2.1, camino 100 nodos, µ=1 | K_µ = 2.1639534 = máx Σ_y e^{−µd} (tight); desigualdad con r=3 vale (799.06 ≤ 4346.42) — **vale** |

(Agente adversarial: Duhamel con controles aleatorios y escalado dt→dt/2 reduce el error exactamente a la mitad — consistente con discretización de primer orden, no con un error en la identidad.)

#### Auditoría adversarial (resumen)
9 ataques intentados contra el veredicto de solidez — todos refutados: aplicación de Prop 4.1 en Teo 4.1 (conjugación exacta); cota de volumen `|C||R|` (monotonía de `[·]_+`); factor ½ y condición del cono; Teorema 5.1 (cadena triangular + FA); hipótesis ocultas Ruta A→B (centro válido, presupuesto automático); signo/flujo del Duhamel (numérico); tesis operacional C7 (estipulación definicional, no teorema); estatus de Prop 4.1 (teorema establecido); Apéndice C (problema de integridad, no de matemática). **Contraejemplos buscados y no encontrados:** entrelazamiento inicial no rompe la cota (norma de operadores, independiente de `ρ₀`); crecimiento de `|C|,|R|` con ℓ degrada la cota pero el enunciado fija las regiones; κ creciente agranda el cono (admitido por la cláusula de control omnipotente).

#### Hallazgos
| # | Tipo | Descripción |
|---|------|-------------|
| 1 | **Obligatorio (integridad)** | Apéndice C: opiniones de chatbots presentadas como «reviews»/«editorial assessments» y «Final verdict: Accepted for publication» sin revista ni revisor humano — endoso editorial fabricado. Eliminar o re-etiquetar («comentarios de asistentes de IA; no constituyen revisión por pares») y eliminar el «Final verdict». |
| 2 | **Obligatorio (atribución)** | Prop 4.1: citar Kliesch–Gogolin–Eisert (Thm. 1) para el caso unitario dependiente del tiempo y aclarar que Barthel–Kliesch cubre el caso Lindbladiano, o incluir la prueba estándar (~2 páginas). |
| 3 | **Obligatorio (redacción)** | Remark 4.1 inflado (el Apéndice A solo acota `J_µ^eff` y `v′_LR`, no demuestra la cota LR completa); C.2 inflado (el `[·]_+` es notación estándar, no «cierra» ninguna brecha lógica); declarar que la sección 6 es marco interpretativo definicional, no teorema. |
| 4 | Menor (matemáticas) | Prop 4.1 no autocontenida; paso de conjugación del Teo 4.1 (flujo retrógrado `τ(c′)_{s,T}`) por explicitar; regularidad de controles («continua a trozos» recomendado); condición del Lema 5.1 conservadora; `ρ₀` sin definir explícitamente; presupuesto B automático (redundante). |
| 5 | Menor (presentación) | «Seminorma» (Def. 6.1) es en realidad pseudométrica (los axiomas de seminorma nunca se usan); colisión notacional R (región) vs. R (regla, Def. 6.2); referencia huérfana [3] (Bravyi–Hastings–Verstraete nunca citada); Def. 6.2 casi vacua en el régimen blando (Infl_R genéricamente positiva); novedad: reorganización correcta de resultados estándar (declarada honestamente como «axiomatic skeleton»). |

---

### 9. Teoría de Conservación de Óptimos y Complejidad
(manuscrito del 7 de abril de 2026 · revisión del 14 de agosto de 2026 — segunda ronda, versión corregida)

#### Veredicto
**Certificación de solidez. Recomendación: ACEPTAR, con correcciones menores obligatorias de precisión formal (D1–D5), ninguna de las cuales altera el contenido matemático.**

La versión corregida implementa de manera completa y correcta las cuatro correcciones obligatorias de la ronda anterior (aplicaciones del Lema 8.12 en Thm 5.3 y Thm 9.5; cuantificador de uniformidad en Def. 4.6; recuantificación de Prop. 7.5(a); citas en texto de las referencias [2]–[5]). Ningún resultado numerado — Teoremas 5.1, 5.3, 7.2, 8.13, 9.5; Proposición 6.5; Corolarios 5.2, 6.6, 7.3, 8.14, 8.16, 9.7; Proposiciones 10.1–10.6 — falla bajo una instanciación legítima de sus hipótesis. No se encontró error fatal alguno; los defectos residuales son exclusivamente de precisión formal (D1–D5). La ronda de cierre verificó la implementación de D1–D7 y re-atacó los ocho puntos F1–F8 sin lagunas formales nuevas: **ACEPTADO SIN CORRECCIONES PENDIENTES**.

#### Inventario de resultados principales
1. **Teorema 5.1 / Corolario 5.2** — Conservación exacta del conjunto de minimizadores bajo transformaciones afines de costo (`ω_n(c,s) = ρ_n(c)·φ_n(s) + σ_n(c)`, `σ_n` independiente de `s`, `φ_n` biyectiva); igualdad de mínimos bajo hipótesis de soporte óptimo correcto.
2. **Teorema 5.3** — Transferencia de complejidad bajo exactitud fuerte: un resolvedor polinomial para `D_n` produce uno polinomial para `Q_n`, uniformemente en la familia.
3. **Teorema 7.2 / Corolario 7.3** — Criterio lineal necesario y suficiente de existencia de levantamientos exactos de costos: `K_n(C_n) ⊆ Col(M_n)` (`B_n = M_nz`, sección lineal sobre ℚ); no constructivo en general.
4. **Proposición 6.5 / Corolario 6.6** — Transporte de óptimos entre representaciones afínmente equivalentes; extractor transportado `E'_n(c,x⋆) = Ψ_n(E_n(c,Φ_n(x⋆)))`.
5. **Teorema 8.13 / Corolarios 8.14, 8.16** — Transporte de complejidad por cambio de representación tipado (decodificación, recodificación final y crecimiento representacional explícitos en la cota temporal).
6. **Teorema 9.5** — Esquema suficiente: bajo las hipótesis (1)–(5), el programa de los pedigree polytopes implica `P = NP`; condicional honesto con la instanciación en STSP explícitamente abierta (Problemas 11.5–11.6).
7. **Proposiciones 7.4, 7.5 y 10.1–10.6** — Barrera de materialización `Ω(N)`; polinomialidad de la sección vía eliminación gaussiana exacta libre de fracciones (Bareiss); contrapositivas y delimitaciones definicionales.

#### Verificado correcto
- **Thm 5.1**: equivalencia de minimizadores vía conservación exacta de valor y biyectividad de `φ_n`; `min Q_n = min D_n` justificada término a término; la necesidad del soporte óptimo queda instanciada por contraejemplo concreto. ✓
- **Thm 7.2**: dirección (⇒) con `B_n = (ρ_n,σ_n)`; dirección (⇐) con sección lineal racional por reducción de filas. **Verificación simbólica (SymPy)**: consistencia e inconsistencia de `M_nz = K_n(c)`, contenido de `Col(M_n)` y sección `R = (MᵀM)⁻¹Mᵀ` racional, verificados numéricamente. ✓
- **Prop. 6.5 / Cor. 6.6**: cadena de optimalidad con ambas identidades de Def. 6.3(3) sobre todo `Q_n, Q'_n`; contraejemplo 2D confirma la necesidad de la compatibilidad total (Obs. 6.4). Cadena de cotas polinomiales verificada; la Def. 4.6 uniforme se satisface por composición de polinomios únicos. ✓
- **Thm 8.13**: optimalidad vía `η_x ∘ ξ_x = ident` + monotonía estricta de `T_x`; cota temporal con `|z| ≤ T̄(g_f(n))` legítima por cuantificación universal de `D(n,ℓ)`. Ataques adversariales (`T_x` decreciente; compatibilidad parcial; `g_f` superpolinomial) confirman la necesidad de cada hipótesis (Obs. 8.7, 8.15). ✓
- **Thm 9.5**: cadena completa de cotas `poly(|u|)` verificada línea a línea, con todas las aplicaciones del Lema 8.12 explícitas; uso de las cinco hipótesis auditado — ninguna sin uso, sin circularidad. ✓
- **Prop. 7.5(a)**: variante libre de fracciones (Bareiss) con cota bit-compleja polinomial; sección fija `R_n` por reducción de filas ⇒ linealidad en `c`. ✓
- **Auditoría hostil C1–C7**: ningún ataque colapsa un resultado numerado; los que sostienen son defectos de declaración formal (D1–D5), no errores matemáticos. ✓

#### Hallazgos
| # | Tipo | Descripción |
|---|------|-------------|
| 1 | Menor (obligatoria — convenciones) | D1: declarar determinismo de los algoritmos y codificación binaria estándar de salidas racionales; aplicada en la Obs. 2.2 («Convenciones del modelo computacional») y verificada. |
| 2 | Menor (obligatoria — redacción) | D2: Lema 8.12 extendido a la codificación posicional estándar y a naturales/tuplas mixtas; aplicada y verificada. |
| 3 | Menor (obligatoria — tipográfica) | D3: tipo de `Q'_n` declarado (`⊆ ℝ^{d'(n)}`) en Def. 6.3 y usado en el Cor. 6.6; aplicada y verificada. |
| 4 | Menor (obligatoria — prueba) | D4: especificar Bareiss y construir la sección fija `R_n` en Prop. 7.5(a); aplicada y verificada. |
| 5 | Menor (obligatoria — 1 palabra) | D5: cuantificar «para el costo unitario c = 1» en Obs. 7.6; aplicada y verificada. |
| 6 | Recomendadas (cosméticas) | D6/D7: remisión a la Def. 4.1 en Def. 3.6; expansión de «STSP» en su primera aparición; aplicadas. |

---

### Tabla consolidada

| Documento | Errores | Gaps | Defectos menores | Rigor global |
|-----------|---------|------|-----------------|--------------|
| A Unique Encoding | 0 | 0 | 1 (typo autor) | Correcto |
| Autorreferencia Segura | 0 | 0 | 2 (forward ref, definiciones sobrantes) | Riguroso |
| Coherent Flow | 0 | 0 | 0 | Riguroso |
| Continuous Epistemic Geometry | 0 | 0 | 0 | Riguroso |
| Epistemic Geometry of Closure | 0 | 0 | 0 | Riguroso |
| Epistemic Geometry (Finite Verification) | 0 | 0 | 4 (observaciones menores) | Sólido — certificado |
| A Generalization of the SAT Equation Theorem | 0 | 1 (cláusulas tautológicas no tratadas) | 2 (ambigüedad de convención, profundidad del resultado) | Sólido — sin errores fatales |
| Locality, Soft Causal Cones, and Informational Limits of Agency | 0 | 0 | 3 obligatorios (integridad/atribución) + menores de presentación | Sólido — certificado, condicionado a correcciones editoriales obligatorias |
| Teoría de Conservación de Óptimos y Complejidad | 0 | 0 | 5 obligatorias de precisión formal (D1–D5) + 2 recomendadas (D6–D7), todas implementadas | Sólido — certificado, aceptado sin correcciones pendientes |

---

## English

### 1. A Unique Encoding of Satisfying Assignments for Balanced CNFs
(3 pages, 123 extracted lines)

#### Verdict
**Mathematically correct. No errors.**

#### Inventory
- **Theorem 3.1** (Balanced SAT Equation). `S = Σ_C 2^{T(C)}` where `T(C) = Σ_{v_i=1} 2^{n-i}`. For balanced CNFs, the binary expansion of `S` (with ≥ 2ⁿ bits) encodes the truth table: bit 1 = unsatisfying assignment.

#### Verified correct
- Convention `0 = True, 1 = False` (line 63): consistent throughout the document.
- Sign vector: `v_i = 1` if `+i ∈ C`, `v_i = 0` if `−i ∈ C`. Falsifying assignment: `a_C(i) = 1` if `v_i = 1` (since `+i` is false with `x_i = 1` under the declared convention), `a_C(i) = 0` if `v_i = 0`. Correct.
- **Injectivity of the sign vector**: in a balanced CNF every clause contains exactly one literal per variable, so `v(C)` determines the clause uniquely: `C = {+i : v_i = 1} ∪ {−i : v_i = 0}`. Two distinct clauses therefore have distinct sign vectors. Since `T: {0,1}^n → {0,…,2^n−1}` is bijective, all exponents `T(C)` are distinct and `S = Σ 2^{T(C)}` **never** has carries. The "no repeated clauses" hypothesis (line 90) is automatic for balanced CNFs (the formula is a set of clauses); the paper's parenthetical is redundant, not a gap.
- `T(C) = Σ v_i 2^{n-i}` is exactly the binary number of the falsifying assignment. `2^{T(C)}` marks a unique bit.
- The three-step proof (encoding, unique falsifying assignment, formation of `S`) is sound.

#### Findings
| # | Type | Description | Line |
|---|------|-------------|------|
| 1 | Minor | The author line literally reads «Oscar Riveos» (verified via direct `pdftotext -layout` of the PDF), while the same document uses «oscar.riveros@gmail.com» (line 4) and «Riveros' Theorem» (line 56). Real internal inconsistency of the PDF: the «r» is missing. | 2 |

---

### 2. Safe Self-Reference in Dynamic Families of States
(30 pages, 1751 extracted lines)

#### Verdict
**Mathematically rigorous. No errors.**

#### Inventory of main results
1. **Theorem 4.4** — Existence and finiteness of the local critical velocity `ν_c^{µ̄}(z,ρ)` in each fiber.
2. **Theorem 5.1** — Uniformity: equivalence between the universal bound `∃ν_* ∀(z,ρ): ν_c ≤ ν_*` and the condition `∃ν_*: Λ(ν_*) + B^{µ̄} ≥ Γ` in all fibers.
3. **Theorem 5.3** — Global divergence: equivalence between `sup ν_c = ∞` and existence of states with arbitrarily large margin.
4. **Theorem 5.6** — Reachable divergence: same characterization restricted to the set `Reach(z₀,ρ₀)`.
5. **Corollary 5.8** — Separable case `Λ(ν) = A·Φ(ν) + C`: explicit formula `ν_c = Φ⁻¹((Γ−B−C)/A)`.
6. **Theorem 6.5** — Invariance of safe moving tubes `T_c` under the ISS policy.
7. **Theorem 6.7** — Practical exponential stability in Lyapunov variable: `F_t ≤ max(q^t F₀, χ(µ̄))`.
8. **Corollary 6.8** — Geometric attraction to the tube under comparison `α(dist) ≤ max(F−χ(µ̄), 0)`.
9. **Theorem 7.8** — No-return criterion: invariant set disjoint from `T` ⊆ complement of `Capt(T)`.
10. **Theorem 8.5** — Finite local radius by minimal holonomy: `R_ε^{safe} ≤ min(2r_h, 2√(ε/η_h))`.

#### Verified correct
- **Axioms 3.1–3.8** (monotonicity, finite capacity, regular transport, compatibility, ISS Lyapunov, holonomy): each justified by necessity through counterexamples in Propositions 3.10–3.15. The counterexamples are correct (e.g., `Λ(ν) = 2 + sin ν` breaks the interval structure without monotonicity; `Γ = ∞` trivializes the critical velocity).
- **Theorem 4.4**: `g(ν) = Λ(ν) + B^{µ̄}` non-decreasing, `g(0) < Γ`, `g(ν) → ∞` → `S = [0, ν_c)` with `ν_c < ∞`. The proof that `ν_c ∉ S` (by right-continuity) and `S = [0, ν_c)` is rigorous. By continuity, `g(ν_c) = Γ`. ✓
- **Theorem 5.1**: `(U2)⇒(U1)`: `g(ν_*) ≥ Γ` + monotonicity → `ν ≥ ν_*` is not safe → `ν_c ≤ ν_*`. `(U1)⇒(U2)`: if `g(ν_*) < Γ`, by right-continuity `∃ε > 0: g(ν_*+ε) < Γ` → `ν_*+ε` safe → `ν_c > ν_*`, contradiction. ✓
- **Theorem 6.5**: `F_{ρ_{t+1}}(z_{t+1}) ≤ max(θ(F_{ρ_t}(z_t)), χ(d_R))`. With `F_t ≤ c`, `θ(s) ≤ s`, `χ(µ̄) ≤ c`: `F_{t+1} ≤ max(θ(c), χ(µ̄)) ≤ max(c, c) = c`. Induction. ✓
- **Theorem 6.7**: `θ(s) ≤ qs` + induction: `a_{t+1} ≤ max(q a_t, c)`. `a_t ≤ max(q^t a₀, c)` proved by induction (the step `max(q·max(q^t a₀, c), c) = max(q^{t+1} a₀, qc, c)` uses `qc ≤ c`). ✓
- **Theorem 7.8**: `E ∩ T = ∅`, `E` invariant → no trajectory from `E` captures `T` → `E ⊆ Z \ Capt(T) = H(T)`. ✓
- **Theorem 8.5**: choose `e ∈ E_{z,ρ}\{0\}` (exists by Axiom 3.8 H1: `E_{z,ρ} ≠ {0}`). `u = v = (r/(2|e|))·e` → `|u| = |v| = r/2`. Area bound: `Res(u,v) ≥ η_h·(r/2)² = η_h·r²/4`. For `ε`-safety: `η_h·r²/4 ≤ ε` → `r ≤ 2√(ε/η_h)`. Supremum + bound `2r_h`. ✓

#### Findings
| # | Type | Description | Line |
|---|------|-------------|------|
| 1 | Minor | `D_η` mentioned in Prop 3.12 but only defined in §0.7 (line 1361). Forward reference. | 520 → 1361 |
| 2 | Minor | `∂Capt(T)` and `∂_T Viab(T)` introduced in Def 7.4 as names for the dynamic horizons, but not used in any subsequent theorem. | 1337–1339 |

---

### 3. Coherent Flow: A Companion Note to Epistemic Geometry
(8 pages, 374 extracted lines)

#### Verdict
**Rigorous and correct. No errors or gaps.**

#### Inventory of results
1. **Theorem 2.2** — Existence of coherent islands (local minima of `F` on finite `K`).
2. **Theorem 2.4** — Deterministic descent `U`: `F(U(K)) ≤ F(K)`, strict if `U(K) ≠ K`.
3. **Corollary 2.5** — Finite termination of every orbit of `U`.
4. **Theorem 3.2** — Detailed balance of the Metropolis–Hastings kernel for `π(K) ∝ e^{−λF(K)}`.
5. **Proposition 4.2** — KL epistemic curvature: `κ_M(p) = inf_{q∈M} D_KL(p∥q)`; separable case `I(A;B)`.
6. **Theorem 5.3** — Exact KL Lyapunov identity for the continuous coherent flow: `dE/dt = −Σ p_{ij} γ_{ij}² ≤ 0`.
7. **Proposition 5.4** — Unique equilibrium `q^⋆ = r_i c_j` on the interface leaf.
8. **Theorem 7.1** — Standard Gödel I, correctly bounded to classical hypotheses.

#### Verified correct
- All hypotheses are finite and explicit: `W` finite, `Ω` finite (`V^{At}`), `K` finite, `µ` with full support. No non-auditable ideal objects.
- **Theorem 3.2**: explicit verification of both cases (`r(K,H) ≤ 1` and `r(K,H) > 1`). Correct cancellation of `Z_λ`. ✓
- **Theorem 5.3**: `h = Π_U h + γ` with `γ ⊥_p U`. `Σ p_{ij} γ_{ij} (Π_U h)_{ij}` = 0 by orthogonality. `Σ p_{ij} γ_{ij} = Σ_i (Σ_j p_{ij} γ_{ij}) = 0` by the normal equations of `Π_U`. Remains `dE/dt = −Σ p_{ij} γ_{ij}²`. ✓
- **Proposition 5.4**: `γ = 0` → `h_{ij} = a_i + b_j` → `p_{ij} = r_i c_j e^{a_i+b_j}`. Summing over `j`: `r_i = r_i e^{a_i} Σ_j c_j e^{b_j}`. The factor `Σ_j c_j e^{b_j}` is constant in `i`; analogously for columns. Normalization forces global factor = 1 → `p = q^⋆`. ✓
- Layer separation `[Proved]`, `[Model]` explicit and respected.

#### Findings
None.

---

### 4. Continuous Epistemic Geometry (cGCNF)
(13 pages, 653 extracted lines)

#### Verdict
**Rigorous and correct. No errors or gaps.**

#### Inventory of main results
1. **Theorem 2.4** — Openness of `Mod(Φ)` in the product topology.
2. **Theorem 2.9** — Joint openness in `(θ, x)` and openness of `{θ : ∃x, x |= Φ_θ}`.
3. **Theorem 3.4** — Interior witness ⇒ positive volume in a compact window.
4. **Theorem 3.6** — Lower semicontinuity of `v_K(θ) = µ(Mod(Φ_θ) ∩ K)` via Fatou.
5. **Theorem 3.7** — Monte Carlo estimator with Hoeffding bound `2e^{−2Tη²}`.
6. **Lemma 4.6** — `BoxDiff(P, R)`: disjoint decomposition of `P \ R` into ≤ 2n boxes (lexicographic slab construction).
7. **Theorem 4.9** — Disjoint compilation of `U(Φ) ∩ K` via incremental `AddBox`.
8. **Theorem 4.11** — Fragmentation barrier `2^n`: `Φ_n = ∧_i (x_i ∈ (0,⅓) ∨ x_i ∈ (⅔,1))` forces ≥ 2ⁿ boxes.
9. **Theorem 6.13** — Transfer with margin: `E_{τ+ω(ε_N)} ⊆ E_τ^{(N)} ⊆ E_τ` for finite ε-net banks.

#### Verified correct
- **Theorem 2.4**: `Mod(ℓ) = (f_ℓ ∘ π_{I_ℓ})⁻¹(U_ℓ)`, continuous preimage of open → open. Finite unions and intersections preserve openness. ✓
- **Theorem 2.9**: `S = {(θ,x): x |= Φ_θ}` open in the product. `E = proj_Θ(S)` open (union of open sections). ✓
- **Lemma 4.6**: slab construction `L_i` (below), `U_i` (above) with frozen prefix `[α_j, β_j]` for `j < i`. Three claims: containment in `P \ R̃`, coverage (lexicographic index `i^⋆`), disjointness (slabs of different indices do not intersect: index `i` has coordinate `i` outside `[α_i, β_i]`; index `j > i` has it inside). ≤ 2n slabs. ✓
- **Theorem 4.11**: `Mod(Φ_n) = ∏_{i=1}^n ((0,⅓) ∪ (⅔,1))` = 2ⁿ connected components (open boxes). Every box is connected → contained in one component → at least 2ⁿ boxes to cover. ✓
- **Theorem 6.13**: right inclusion `E_τ^{(N)} ⊆ E_τ`: `S_N ⊆ S_∞` → `min_{S_N} F_S ≥ inf_{S_∞} F_S`. If `min_{S_N} F_S(θ) < −τ`, then `inf_{S_∞} F_S(θ) ≤ min_{S_N} F_S(θ) < −τ`. Left inclusion: `F_S(θ) < −τ−ω(ε_N)` + `|F(θ,S)−F(θ,S_N)| ≤ ω(ε_N)` → `F_{S_N}(θ) < −τ`. ✓ The hypothesis of modulus `ω` uniform in `θ` is given explicitly as condition (iv), not claimed to follow from joint continuity alone. ✓
- **Gray zone** (Def 6.16): `G = K \ (Mod(Φ_common) ∪ Mod(Φ_sep))`, standard complement of the certified phases. Without the inclusion defect of the other work (Finite-Bank). ✓

#### Findings
None.

---

### 5. Epistemic Geometry of Closure (SCE-IM)
(18 pages, 710 extracted lines)

#### Verdict
**Rigorous at the declared level. No errors. The `[Proved]`/`[Model]` labels are honest.**

#### Inventory of results
1. **Definition 2.1** — SCE-IM system: 10-tuple `(S, O, Ω, T, J, err, µ, K, F, Φ)` with typed teeth `D_τ ∈ Σ_Ω` and zipper `◁`.
2. **Proposition 3.2** — Curvature invariance under rigid isomorphism: `κ'(g(o)) = κ(o)`.
3. **Lemma 4.4** — Monotonicity of `κ_R(o)` in `R` and limit `inf_R κ_R = κ`.
4. **Theorem 6.2** — Lipschitz stability of `κ`: `d_∞ ≤ δ` → `|κ − κ'| ≤ δ`.
5. **Proposition 6.4** — Sign invariance under equivalent metrics: `c_1 κ_δ ≤ κ_d ≤ c_2 κ_δ`.
6. **Theorem 7.9** — Operational zipper completeness `[Model]`: signature equality `Σ_zip` + ZT + ZM + RZ ⇒ filtered-dynamic equivalence.
7. **Theorem 8.3** — Completeness with resources `[Model]`.
8. **Theorem 8.4** — Stability of `κ_R`: one-sided bound `κ'_R(o') ≤ κ_R(o) + δ`; symmetry requires bidirectional control. Remark 8.5 explicitly corrects a previous version.

#### Verified correct
- **Definition 2.2**: tooth semantics via `D_τ ∈ Σ_Ω`. Satisfaction of tooth `τ` by state `σ` in window `K`: `µ(J(σ) ∩ D_τ ∩ K) = µ(J(σ) ∩ K)`. Well defined. ✓
- **Proposition 3.2**: `κ'(g(o)) = inf_σ' err'(σ', g(o))`. By bijectivity of `h`, `σ' = h(σ)`. `err'(h(σ), g(o)) = err(σ, o)`. Infima equal. ✓
- **Lemma 4.4**: nesting `{σ: ρ(σ) ≤ R} ⊆ {σ: ρ(σ) ≤ R'}` for `R ≤ R'` → `κ_{R'} ≤ κ_R`. `inf_{R≥0} κ_R = κ`: `κ_R ≥ κ` (subset); for each `σ`, take `R = ρ(σ)`, then `κ_R ≤ err(σ,o)`, take infimum in `σ`. ✓
- **Theorem 6.2**: the ε-δ argument with homeomorphism `h_ε` approximating `d_∞` is correct. Bidirectionality via `h_ε⁻¹`. ✓
- **Remark 8.5**: *«In a previous version, a symmetric bound |κ_R − κ'_R| ≤ δ was stated assuming only a map h: S → S'. That form is false in general if h(S_{≤R}) is not surjective onto S'_{≤R}.»* Corrects a genuine error of a previous version. The current formulation correctly separates the one-sided bound (always valid) from symmetry (requires `g: S' → S` in the opposite direction). This demonstrates self-critical rigor. ✓

#### Findings
None.

---

### 6. Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions Across Logic, Computation, and Physics
(20 pages, 1131 extracted lines)

#### Verdict
**CERTIFICATION OF SOUNDNESS.** The article is mathematically correct in all of its claims tagged `[Proved]`. The claims tagged `[Metaformal]` and `[Model]` are appropriately identified as speculative or conditioned on model hypotheses. The proofs of the central unification theorems (8.7 and 8.8) are logically valid. No fatal mathematical error is identified.

#### Correction of errors in previous reviews
Two previous reviews identified an alleged «fatal error» in the DSOP epistemic interface. Direct reading of the compiled PDF shows that those identifications are incorrect:

1. **Symmetric difference in the DSOP interface (Def. 8.4)** — the text defines `err(U) = |φ(U) ∆ o| = |φ(U) \ o| + |o \ φ(U)|`, where `∆` denotes symmetric difference (line 871), and `err(U) = 0 ⟺ φ(U) = o` as sets (line 874). The correction that previous reviews recommended **is already present in the original text**. The proposed counterexample (`U = {Q(00)}` with `o = Ω₂`) fails: `|{00} ∆ Ω₂| = 3 ≠ 0`.
2. **Proposition 8.10 (DSOP/DNF)** — the text explicitly states: «dnf(f) ≤ dsop(f) means a DNF lower bound dnf(f) ≥ L implies the corresponding DSOP lower bound dsop(f) ≥ L, but the converse is not true: dsop(f) ≥ L alone places no lower bound on dnf(f)» (lines 1006–1010). The implication direction is DNF → DSOP; the text explicitly denies the converse that the previous review attributed to it.
3. **Theorem 5.8 (DRP)** — the proof explicitly invokes DRP: «By DRP, the orbit (T^k(σ_n)) has an accumulation point σ_n* with err(σ_n*) = inf_k err(T^k(σ_n)) ≤ err(σ_n) < 1/n» (lines 491–493). That the conclusion `κ_S = 0` also follows from (a) without DRP is a matter of proof style, not an error.
4. **Theorem 5.11 (Gödel obstruction)** — the whole subsection §5.3 is tagged `[Metaformal]` (line 503). The theorem is a Gödelian diagonal scheme conditioned on the existence of a Gödel-admissible predicate `Prov_{0,r}`; the text does not claim to have constructed it for a concrete system. The label is appropriate.

**Cross-check note:** the numbering in this section was verified against the compiled PDF. The previous reviews used the numbering of an earlier draft: Def. 8.5 → 8.4, Thm. 8.6 → 8.7, Thm. 8.7 → 8.8, Prop. 8.9 → 8.10, Prop. 8.10 → 8.11, Thm. 8.12 → 8.13, Thm. 8.13 → 8.14, Thm. 2.8 → 2.9.

#### Module evaluation
| Module | Verdict |
|--------|---------|
| A (§2) SAT-verifiable discrete physics `[Proved]` | Correct. GCNF and one-hot (Def. 2.1–2.2, Prop. 2.3), solver/verifier separation (Prop. 2.5), equilateral Gauss–Bonnet (Thm. 2.9: the identity `Σ_v χ(v) = 6χ` is a direct algebraic manipulation of `3F = 2E`, explicitly restricted to the equilateral case), Boolean causal cone (Thm. 2.12: induction over graph distance). |
| A′ (§3) SAT equation `[Proved]` | Correct. Unique falsifier and index (Def. 3.1–3.2), Theorem 3.3. Remark 3.4: accurate and honest self-assessment. |
| B (§4) COVERTRACE `[Proved]` | Correct. CubeDiff (Alg. 1, Lemma 4.5: the non-deterministic choice does not affect the bound), AddCube (Alg. 2, Thm. 4.7: disjointness invariant preserved), **parity barrier** (Thm. 4.8: any subcube with a free coordinate contains an equal number of even and odd assignments; tight bound `2^{n−1}`), conditional PH collapse (Thm. 4.9), affine compilation (Def. 4.10–4.11, Thm. 4.13: PARITY is a single affine subspace). |
| C (§5) Epistemic curvature `[Metaformal]` + `[Proved]` | Correct. Definitions 5.1–5.6 well placed (the topology on `L` can be taken discrete: every subset is Borel). DRP (Def. 5.7) postulated, not proved — the text does not claim it. Thm. 5.8 valid (the conclusion also follows from (a) without DRP, but `A∧B⇒C` is true if `A⇒C`). Thm. 5.11 correct diagonal scheme. §5.4 `[Metaformal]`. §5.5 operational definition (`τ_A` as a search-space compression measure), not a theorem. |
| D (§6) Layered Metric Space `[Model]` + `[Proved]` | Correct. Layers, strain and curvature (Def. 6.1–6.2), Euler–Lagrange equation of motion (Thm. 6.4: standard derivation), unitary Procrustes (Thm. 6.6: standard Golub–Van Loan result), materialization (Def. 6.8) `[Model]`. |
| E (§7) Locality and agency `[Model]` + `[Proved]` | Correct. Lieb–Robinson (Thm. 7.1) standard citation; Duhamel (Lemma 7.3); agency as distinguishability (Def. 7.4, Thm. 7.5: plausible proof sketch); operational incompressibility (Lemma 7.7, Thm. 7.9); operational curvature (Def. 7.10), no equivalence with `κ_S` claimed. |
| §8 Interrelation and unification | Correct. Operational indistinguishability (Thm. 8.1); reduction to certificates (Thm. 8.3); **DSOP interface (Def. 8.4)**: symmetric difference, `err = 0 ⟺ φ(U) = o`; **Trilemma (Thm. 8.7)** `[Metaformal]`: parity barrier (branch 1) sound, branch 2 valid (`err = 0` forces exact set equality), branch 3 depends on the physical model of §7, appropriately identified; **Unified obstruction (Thm. 8.8)** `[Metaformal]`: valid (partial redundancy among hypotheses does not invalidate the theorem); Prop. 8.10 (DSOP/DNF) correct; Prop. 8.11 (affine) correct; Thm. 8.13 (`‖QP‖ < 1` ⇒ no simultaneous certainty ⇒ `κ > 0`) correct; Thm. 8.14 (CHSH): `S` is 8-Lipschitz in TV, `sup_LHV ≤ 2`, `sup_QM = 2√2` ⇒ `inf TV ≥ (2√2−2)/8 > 0`. Correct. |

#### Minor observations (do not affect soundness)
1. **Topology on `L`** (Def. 5.1, line 430): not explicitly specified; adopting the discrete topology (every subset is Borel) trivially satisfies the measurability condition. Making this choice explicit is recommended.
2. **Partial redundancy in Thm. 5.8**: the conclusion `κ_S = 0` follows from (a) without DRP (`err(σ_n) < 1/n` ⇒ `κ_S ≤ 1/n` for all `n`). The statement could be refined so that DRP is logically necessary.
3. **Constructivity of DRP** (Def. 5.7, line 478): the only concrete construction sketched is projected mirror descent (§5.4 / Remark 5.14, line 568). Existence for non-trivial formal systems is not proved; since the theorems are conditional, their validity is unaffected.
4. **Local parity protocol** (Thm. 8.7, branch 3): an explicit Hamiltonian and the reduction of the verification protocol to the control formalism of §7 would be required to raise the branch from `[Model]` to `[Proved]`.

#### Findings
| # | Type | Description | Line |
|---|------|-------------|------|
| 1 | Minor | Topology on `L` not explicit (Def. 5.1); discrete topology recommended. | 430 |
| 2 | Minor | Thm. 5.8: DRP is not logically necessary for the conclusion `κ_S = 0`. | 491 |
| 3 | Minor | DRP (Def. 5.7): no construction for non-trivial formal systems. | 478 |
| 4 | Minor | Thm. 8.7, branch 3 `[Model]`: local parity protocol not specified. | 891 |

---

### 7. A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding
(6 pages, 256 extracted lines)

#### Verdict
**Mathematically sound. No fatal errors.** The main theorem (Theorem 5.1, Generalized SAT Equation Theorem) is correct, the construction works for every CNF formula, and the proof is logically valid. No fatal error invalidating the central claims of the document was found. Three minor (expository, non-mathematical) defects were detected, detailed in the findings below.

#### Inventory
- **Theorem 5.1** (Generalized SAT Equation). `S = OR_{j=1}^m OR_{M′⊆MC_j} 2^{B(C_j) + Σ_{i∈M′} 2^{N−i}}`, with `B(C) = Σ_{i∈PC} r_i(C)·2^{N−i}` (`r_i(C) = 0` if `+i ∈ C`, `r_i(C) = 1` if `−i ∈ C`). The binary expansion of `S` with `2^N` bits encodes exactly the truth table of `F`: the bit at position `pos(a)` is 1 if and only if `a` does not satisfy `F`.
- **Remark 3.1**: in the balanced case `PC = {1,…,N}` and `MC = ∅`, so `S_C = 2^{B(C)}` recovers the original encoding.
- **§7.2**: arithmetic alternative in base `b > m` (the maximum number of clauses that can share a falsifying position) avoiding carries, at the cost of losing the binary representation.

#### Verified correct
- `pos(a) = Σ a_i·2^{N−i}` is a bijection `{0,1}^N → {0,…,2^N−1}`; each position corresponds to a distinct bit of the expansion. ✓
- `r_i(C)` correctly identifies the value falsifying each literal, and `B(C) = Σ_{i∈PC} r_i(C)·2^{N−i}` encodes the fixed bits of the falsifying subcube. ✓
- `S_C = OR_{M′⊆MC} 2^{B(C) + Σ_{i∈M′} 2^{N−i}}` captures exactly `Fals(C)`: each subset `M′` of absent variables yields a distinct exponent (distinct sums of weights), so `S_C` marks one bit per falsifying assignment of the clause. ✓
- `S = OR_j S_{C_j}` implements the union of falsifying sets; the bitwise OR is carry-free (idempotence `1∨1 = 1`), even when distinct clauses share falsifying assignments — exactly the case where the arithmetic sum of the original document fails. ✓
- No overflow: the maximum exponent is `B(C) + Σ_{i∈MC} 2^{N−i} ≤ 2^N−1`; the most significant bit always lies within the required `2^N` bits. ✓
- Injectivity `F → S` is not claimed by the document (it is not part of the theorem); it is claimed and verified that `S` uniquely encodes the truth table. ✓
- **Computational verification**: N=3 exhaustive (all `2^26 ≈ 67M` possible CNF formulas, via the 26 clause types combined by OR); N=4: 7500+ random formulas; N=5: 200+; edge cases (empty formula `S = 0`, contradictory clauses, duplicated clauses, unit clauses, full formula). Zero counterexamples; the arithmetic-sum encoding fails (as expected) on formulas with shared falsifying assignments. ✓
- **Comparison with the reference document**: the original uses the arithmetic sum `Σ_C 2^{T(C)}`, carry-free only for balanced CNFs (injectivity of the sign vector); the generalization replaces the sum with the bitwise OR, always carry-free. The bit patterns of both documents are inverted (`v_i = 1` for `+i` vs `r_i = 0` for `+i`), but the underlying semantics are isomorphic. ✓

#### Findings
| # | Type | Description | Line |
|---|------|-------------|------|
| 1 | Minor | Convention ambiguity: the document states *«0 represents True and 1 represents False when evaluating literals»*, but Definition 2.3 and all examples use standard semantics (0=False, 1=True) for variable values, reserving the convention for evaluation *results* (bit 1 = unsatisfying). The phrase *«when evaluating literals»* is ambiguous for a reader coming from the balanced document, where the same phrase means that the variables themselves use 0=True. The document is internally consistent under the correct interpretation; the wording should be refined. | 73 |
| 2 | Gap | Untreated tautological clauses: if a clause contains both `+i` and `−i` for some variable, Definition 2.3 is ambiguous (both branches apply). Such a clause is a tautology (`Fals(C) = ∅`, `S_C = 0`) and can be removed in preprocessing, but the document does not mention this implicit restriction of the domain of formulas. | 92–97 |
| 3 | Minor | Depth of the result: the theorem is a direct consequence of (a) bitwise OR = set union over bit positions and (b) the falsifying set of a CNF is the union of the falsifying sets of its clauses. The notation `2^{B(C) + Σ 2^{N−i}}` is an arithmetic wrapper for a set-theoretic operation. The result is correct, but its presentation as a «theorem» and «generalization» may overstate its non-trivial mathematical content. | 140–203 |

---

### 8. Locality, Soft Causal Cones, and Informational Limits of Agency. An axiomatic skeleton (nonlinear development) for local control and remote indistinguishability
(10 pages · manuscript dated December 25, 2025 · review dated August 12, 2026)

#### Verdict
**Mathematically sound: certification conditioned on mandatory editorial corrections.** All central claims (double-sum Lieb–Robinson bound, geometric refinement `K_µ`, two-time Duhamel identity with causal flow in the remaining time `T−s`, exponentially suppressed influence/agency bound outside the cone, and capacity closure via Holevo + Fannes–Audenaert) were verified independently — algebraically and numerically — and survive a dedicated adversarial audit. No algebraic error, no hidden hypothesis invalidating a central claim, and no counterexample breaking the bounds was found.

**The manuscript is NOT acceptable in its current form for reasons of integrity and attribution accuracy, not mathematics:**
1. Appendix C presents AI assistant opinions (Gemini, Claude, Grok, GPT-5.2) as «reviews» and «editorial assessments», and contains a «Final verdict: Accepted for publication / finalization» with no journal, editor, or human reviewer. A fabricated editorial endorsement that must be removed or explicitly re-labeled.
2. Imprecise attribution of Proposition 4.1: Barthel–Kliesch [5] covers **Lindbladian** dynamics, not the unitary case; the time-dependent unitary case is covered by Kliesch–Gogolin–Eisert [6] (Thm. 1), whose coauthors the manuscript omits.
3. Inflated self-descriptions (Remark 4.1, C.2) and minor presentation deficiencies.

In binary terms: certification of mathematical soundness, conditioned on the mandatory editorial corrections 1–3. The verdict is independent of the self-awarded «Accepted for publication» in the manuscript's own Appendix C; the mathematics was verified from scratch.

#### Inventory of central claims
1. **C1 (LR).** For exponentially local interaction (Assumption 2.1), the double-sum Lieb–Robinson bound holds with positive part `e^{−µ[d(x,y)−v|t|]_+}` (Theorem 2.1) and its volumetric specialization (Corollary 2.1).
2. **C2 (Geometry).** Geometric refinement with explicit constant `K_µ = 1 + ∆e^{−µ}/(1−(∆−1)e^{−µ})` and `min(|X|,|Y|)` scaling (Proposition 2.1).
3. **C3 (Duhamel).** Exact two-time identity: `τ(c)_{T,0}(B) − τ(c′)_{T,0}(B) = i∫₀^T τ(c)_{s,0}([∆H(s), τ(c′)_{T,s}(B)])ds` (Lemma 4.1), with causal flow in the remaining time `T−s`.
4. **C4 (Remote influence).** Bounded local control ⇒ remote influence exponentially suppressed outside the cone: if `d(C,R) > v′T + ℓ`, then `Ag_R(c,c′;T) ≤ K′_A|C||R| e^{−µℓ} ∫₀^T‖∆H(s)‖ds` (Theorem 4.1 → Corollary 4.1; Corollary 6.1 analogous for `Infl_R`).
5. **C5 (Capacity).** Geometric indistinguishability ⇒ capacity closure: `I(M;Z) ≤ χ ≤ 2ε log(d_R−1) + h(2ε)` with `ε = O(e^{−µℓ})` (Theorem 5.1 + Proposition 5.1).
6. **C6 (Hard classical cone).** A local cellular automaton has a hard causal cone (influence exactly zero outside) (Proposition 7.1).
7. **C7 (Operational).** Remote agency/responsibility rules must respect the soft causal limits except under «effectively omnipotent» control (Definition 6.2, Section 6).

#### Verified correct
- **Definitions (1.1–1.5, 4.1–4.4, 5.1–5.2):** standard and correct. Only remark: `ρ₀` is used (Def. 4.4, Def. 6.1) without explicit definition (implicit in Def. 1.4) — benign gap. ✓
- **Theorem 2.1 / Corollary 2.1:** standard double-sum form (Nachtergaele–Sims); truncation by `[·]_+` is a trivial consequence of the untruncated form; Remark 2.2 honest (inside the cone the bound is non-informative). Normalization `v_LR ≲ 2J_µ/µ` correct in the BHV convention. ✓
- **Proposition 2.1 (`K_µ`):** sphere count `|S_n| ≤ ∆(∆−1)^{n−1}` and geometric series correct, valid iff `µ > log(∆−1)` (condition imposed by the statement). **Numerically verified:** path of 100 nodes, µ=1: `K_µ = 2.1639534…` matches `max_x Σ_y e^{−µd(x,y)}` to machine precision (the bound is *tight* at the center); asymmetric case |X|=5, |Y|=100: symmetry verified. ✓
- **Proposition 4.1 (time-dependent LR):** honestly labeled «(referenced)»; a **true and established theorem** — Kliesch–Gogolin–Eisert (arXiv:1306.0716, Thm. 1) covers the time-dependent unitary case (the unitary Hamiltonian case is an explicit special case in the text), with the standard packing `min(1, e^{v|t−s|−µd}) ≤ 2e^{−µ[d−v′|t−s|]_+}` and instantaneous bounds `sup_t J_µ(t) ≤ J_µ + κe^{µ diam(C)} < ∞` with the same µ. ✓ (statement) — ⚠ **imprecise attribution** (Barthel–Kliesch treats Lindbladians); ~2 pages of proof missing for self-containment.
- **Lemma 4.1 (two-time Duhamel):** verified term by term (the 4 terms of `dF/ds` add up exactly to `i Uc(s,0)†[∆H(s), Uc′(T,s)†BUc′(T,s)]Uc(s,0)`; no sign error) and **numerically** (2 qubits, max error ~10⁻⁵ with `dt = 2.5·10⁻⁵`, scaling linearly in `dt`). The identity is exact, including the `+i` sign and the flow `τ(c′)_{T,s}` in the remaining time. ✓
- **Theorem 4.1 (causal flow T−s):** conjugation identity `[A, U†BU] = U†[UAU†, B]U` correct. Precision note (not an error): strictly, the conjugation lands on the **backward** flow `τ(c′)_{s,T}`; identical conclusion (the LR bound holds in both directions with the same constants and the interval measures `|T−s|`). ✓
- **Corollaries 4.1 / 6.1:** trace–norm duality (Lemma 4.2, Helstrom) and the ½ factor correct (`K′_A = K_A/2`); cone condition `d(C,R) > v′T + ℓ` verified for all `s ∈ [0,T]` (exponent ≤ `e^{−µℓ}`). ✓
- **Theorem 5.1 / Proposition 5.1:** triangle chain `‖ρm−ρ̄‖₁ ≤ 4ε` and Fannes–Audenaert with parameter `2ε` under `2ε ≤ 1−1/d_R` correct (the restriction is conservative relative to Audenaert's 2007 theorem, which holds for all `δ ∈ [0,1]`; the asymptotic conclusion is unaffected). Budget `B ≤ 2κT` automatic; `I(M;Z) ≤ χ` (Holevo) correctly applied. ✓
- **Appendix A / Proposition 7.1:** `J_µ^eff ≤ J_µ + κe^{µ diam(C)}` ✓ (numerically verified by agent: exact equality on a 6-site chain); Remark A.1 honest. Hard cone of the cellular automaton correct and standard; honest soft/hard contrast. ✓

#### Independent numerical verifications (reviewer)
| Verification | Result |
|---|---|
| Lemma 4.1 (Duhamel), 2 qubits, T=1, dt=2.5·10⁻⁵, 3 observables | max element error ~3.7–9.7·10⁻⁶ (O(dt)) — **exact** |
| Fannes–Audenaert, 3000 random pairs, d=3 and d=5 | no violations (worst margin −0.198 / −0.748) — **holds** |
| Theorem 5.1 (concentration + Holevo), d=4, ε=0.05 | ½‖ρm−ρ̄‖ ≤ 0.0104 ≤ 2ε; χ = 0.000878 ≤ 0.627 — **holds** |
| Prop 2.1, path of 100 nodes, µ=1 | K_µ = 2.1639534 = max Σ_y e^{−µd} (tight); inequality with r=3 holds (799.06 ≤ 4346.42) — **holds** |

(Adversarial agent: Duhamel with random controls and scaling dt→dt/2 reduces the error exactly by half — consistent with first-order discretization, not with an error in the identity.)

#### Adversarial audit (summary)
9 attacks attempted against the soundness verdict — all refuted: application of Prop 4.1 in Thm 4.1 (exact conjugation); volume bound `|C||R|` (monotonicity of `[·]_+`); ½ factor and cone condition; Theorem 5.1 (triangle chain + FA); hidden hypotheses Route A→B (valid center, automatic budget); sign/flow of Duhamel (numerical); operational thesis C7 (definitional stipulation, not a theorem); status of Prop 4.1 (established theorem); Appendix C (integrity issue, not mathematics). **Counterexamples sought and not found:** initial entanglement does not break the bound (operator norm, independent of `ρ₀`); growth of `|C|,|R|` with ℓ degrades the bound but the statement fixes the regions; increasing κ enlarges the cone (admitted by the omnipotent-control clause).

#### Findings
| # | Type | Description |
|---|------|-------------|
| 1 | **Mandatory (integrity)** | Appendix C: chatbot opinions presented as «reviews»/«editorial assessments» and a «Final verdict: Accepted for publication» with no journal or human reviewer — fabricated editorial endorsement. Remove or re-label («AI assistant comments; do not constitute peer review») and remove the «Final verdict». |
| 2 | **Mandatory (attribution)** | Prop 4.1: cite Kliesch–Gogolin–Eisert (Thm. 1) for the time-dependent unitary case and clarify that Barthel–Kliesch covers the Lindbladian case, or include the standard proof (~2 pages). |
| 3 | **Mandatory (wording)** | Inflated Remark 4.1 (Appendix A only bounds `J_µ^eff` and `v′_LR`, it does not prove the full LR bound); inflated C.2 (the `[·]_+` is standard notation, it does not «close» any logical gap); declare that Section 6 is a definitional interpretive framework, not a theorem. |
| 4 | Minor (mathematics) | Prop 4.1 not self-contained; conjugation step of Thm 4.1 (backward flow `τ(c′)_{s,T}`) to be made explicit; regularity of controls («piecewise continuous» recommended); conservative Lemma 5.1 condition; `ρ₀` not explicitly defined; automatic budget B (redundant). |
| 5 | Minor (presentation) | «Seminorm» (Def. 6.1) is actually a pseudometric (the seminorm axioms are never used); notational collision R (region) vs. R (rule, Def. 6.2); orphan reference [3] (Bravyi–Hastings–Verstraete never cited); Def. 6.2 almost vacuous in the soft regime (Infl_R generically positive); novelty: correct reorganization of standard results (honestly declared as «axiomatic skeleton»). |

---

### 9. Theory of Conservation of Optima and Complexity
(manuscript dated April 7, 2026 · review dated August 14, 2026 — second round, corrected version)

#### Verdict
**Certification of soundness. Recommendation: ACCEPT, with mandatory minor formal-precision corrections (D1–D5), none of which alters the mathematical content.**

The corrected version fully and correctly implements the four mandatory corrections of the previous round (applications of Lemma 8.12 in Thm 5.3 and Thm 9.5; uniformity quantifier in Def. 4.6; requantification of Prop. 7.5(a); in-text citations of references [2]–[5]). No numbered result — Theorems 5.1, 5.3, 7.2, 8.13, 9.5; Proposition 6.5; Corollaries 5.2, 6.6, 7.3, 8.14, 8.16, 9.7; Propositions 10.1–10.6 — fails under a legitimate instantiation of its hypotheses. No fatal error was found; the residual defects are exclusively formal-precision issues (D1–D5). The closing round verified the implementation of D1–D7 and re-attacked the eight points F1–F8 without new formal gaps: **ACCEPTED WITH NO PENDING CORRECTIONS**.

#### Inventory of main results
1. **Theorem 5.1 / Corollary 5.2** — Exact conservation of the minimizer set under affine cost transformations (`ω_n(c,s) = ρ_n(c)·φ_n(s) + σ_n(c)`, `σ_n` independent of `s`, `φ_n` bijective); equality of minima under the correct-optimal-support hypothesis.
2. **Theorem 5.3** — Complexity transfer under strong exactness: a polynomial solver for `D_n` yields a polynomial solver for `Q_n`, uniformly over the family.
3. **Theorem 7.2 / Corollary 7.3** — Necessary-and-sufficient linear criterion for the existence of exact cost lifts: `K_n(C_n) ⊆ Col(M_n)` (`B_n = M_nz`, linear section over ℚ); non-constructive in general.
4. **Proposition 6.5 / Corollary 6.6** — Transport of optima between affinely equivalent representations; transported extractor `E'_n(c,x⋆) = Ψ_n(E_n(c,Φ_n(x⋆)))`.
5. **Theorem 8.13 / Corollaries 8.14, 8.16** — Complexity transport by typed representation change (decoding, final recoding, and representational growth explicit in the time bound).
6. **Theorem 9.5** — Sufficient scheme: under hypotheses (1)–(5), the pedigree polytopes program implies `P = NP`; honest conditional with the STSP instantiation explicitly open (Problems 11.5–11.6).
7. **Propositions 7.4, 7.5 and 10.1–10.6** — Materialization barrier `Ω(N)`; polynomiality of the section via exact fraction-free Gaussian elimination (Bareiss); contrapositives and definitional delimitations.

#### Verified correct
- **Thm 5.1**: minimizer equivalence via exact value conservation and bijectivity of `φ_n`; `min Q_n = min D_n` justified term by term; the necessity of the optimal support is instantiated by a concrete counterexample. ✓
- **Thm 7.2**: direction (⇒) with `B_n = (ρ_n,σ_n)`; direction (⇐) with a rational linear section by row reduction. **Symbolic verification (SymPy)**: consistency and inconsistency of `M_nz = K_n(c)`, membership in `Col(M_n)`, and rational section `R = (MᵀM)⁻¹Mᵀ`, verified numerically. ✓
- **Prop. 6.5 / Cor. 6.6**: optimality chain with both identities of Def. 6.3(3) over all `Q_n, Q'_n`; the 2D counterexample confirms the necessity of total compatibility (Obs. 6.4). Polynomial bound chain verified; the uniform Def. 4.6 is satisfied by composition of single polynomials. ✓
- **Thm 8.13**: optimality via `η_x ∘ ξ_x = ident` + strict monotonicity of `T_x`; time bound with `|z| ≤ T̄(g_f(n))` legitimate by universal quantification of `D(n,ℓ)`. Adversarial attacks (`T_x` decreasing; partial compatibility; superpolynomial `g_f`) confirm the necessity of each hypothesis (Obs. 8.7, 8.15). ✓
- **Thm 9.5**: full `poly(|u|)` bound chain verified line by line, with all applications of Lemma 8.12 explicit; use of the five hypotheses audited — none unused, no circularity. ✓
- **Prop. 7.5(a)**: fraction-free variant (Bareiss) with polynomial bit-complexity bound; fixed section `R_n` by row reduction ⇒ linearity in `c`. ✓
- **Hostile audit C1–C7**: no attack collapses a numbered result; those that hold are formal-declaration defects (D1–D5), not mathematical errors. ✓

#### Findings
| # | Type | Description |
|---|------|-------------|
| 1 | Minor (mandatory — conventions) | D1: declare determinism of the algorithms and the standard binary encoding of rational outputs; applied in Obs. 2.2 («Conventions of the computational model») and verified. |
| 2 | Minor (mandatory — wording) | D2: Lemma 8.12 extended to the standard positional encoding and to naturals/mixed tuples; applied and verified. |
| 3 | Minor (mandatory — typographic) | D3: type of `Q'_n` declared (`⊆ ℝ^{d'(n)}`) in Def. 6.3 and used in Cor. 6.6; applied and verified. |
| 4 | Minor (mandatory — proof) | D4: specify Bareiss and build the fixed section `R_n` in Prop. 7.5(a); applied and verified. |
| 5 | Minor (mandatory — one word) | D5: quantify «for the unit cost c = 1» in Obs. 7.6; applied and verified. |
| 6 | Recommended (cosmetic) | D6/D7: reference to Def. 4.1 in Def. 3.6; expansion of «STSP» at its first occurrence; applied. |

---

### Consolidated table

| Document | Errors | Gaps | Minor defects | Global rigor |
|-----------|---------|------|-----------------|--------------|
| A Unique Encoding | 0 | 0 | 1 (author typo) | Correct |
| Autorreferencia Segura | 0 | 0 | 2 (forward ref, leftover definitions) | Rigorous |
| Coherent Flow | 0 | 0 | 0 | Rigorous |
| Continuous Epistemic Geometry | 0 | 0 | 0 | Rigorous |
| Epistemic Geometry of Closure | 0 | 0 | 0 | Rigorous |
| Epistemic Geometry (Finite Verification) | 0 | 0 | 4 (minor observations) | Sound — certified |
| A Generalization of the SAT Equation Theorem | 0 | 1 (untreated tautological clauses) | 2 (convention ambiguity, result depth) | Sound — no fatal errors |
| Locality, Soft Causal Cones, and Informational Limits of Agency | 0 | 0 | 3 mandatory (integrity/attribution) + minor presentation defects | Sound — certified, conditioned on mandatory editorial corrections |
| Theory of Conservation of Optima and Complexity | 0 | 0 | 5 mandatory formal-precision (D1–D5) + 2 recommended (D6–D7), all implemented | Sound — certified, accepted with no pending corrections |

---

*Revisión completada el 10 y 11 de agosto de 2026 sobre extracciones `pdftotext -layout -enc UTF-8` de los PDFs originales; la revisión del octavo documento (Locality, Soft Causal Cones, and Informational Limits of Agency) se completó el 12 de agosto de 2026 con verificación numérica independiente y auditoría adversarial; la revisión del noveno documento (Teoría de Conservación de Óptimos y Complejidad) se completó el 14 de agosto de 2026 con verificación simbólica asistida por computadora (SymPy) y auditoría adversarial. / Review completed on August 10–11, 2026 over `pdftotext -layout -enc UTF-8` extractions of the original PDFs; the review of the eighth document (Locality, Soft Causal Cones, and Informational Limits of Agency) was completed on August 12, 2026 with independent numerical verification and adversarial auditing; the review of the ninth document (Theory of Conservation of Optima and Complexity) was completed on August 14, 2026 with computer-assisted symbolic verification (SymPy) and adversarial auditing.*
