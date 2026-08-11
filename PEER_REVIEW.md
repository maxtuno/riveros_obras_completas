# Revisión matemática / Mathematical Peer Review

**Español:** Revisión desde cero sobre extracciones `pdftotext -layout -enc UTF-8` de los 5 PDFs originales. Cada documento fue leído íntegramente y auditado teorema por teorema, definición por definición, prueba por prueba.

**English:** Review from scratch over `pdftotext -layout -enc UTF-8` extractions of the 5 original PDFs. Each document was read in full and audited theorem by theorem, definition by definition, proof by proof.

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

### Tabla consolidada

| Documento | Errores | Gaps | Defectos menores | Rigor global |
|-----------|---------|------|-----------------|--------------|
| A Unique Encoding | 0 | 0 | 1 (typo autor) | Correcto |
| Autorreferencia Segura | 0 | 0 | 2 (forward ref, definiciones sobrantes) | Riguroso |
| Coherent Flow | 0 | 0 | 0 | Riguroso |
| Continuous Epistemic Geometry | 0 | 0 | 0 | Riguroso |
| Epistemic Geometry of Closure | 0 | 0 | 0 | Riguroso |

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

### Consolidated table

| Document | Errors | Gaps | Minor defects | Global rigor |
|-----------|---------|------|-----------------|--------------|
| A Unique Encoding | 0 | 0 | 1 (author typo) | Correct |
| Autorreferencia Segura | 0 | 0 | 2 (forward ref, leftover definitions) | Rigorous |
| Coherent Flow | 0 | 0 | 0 | Rigorous |
| Continuous Epistemic Geometry | 0 | 0 | 0 | Rigorous |
| Epistemic Geometry of Closure | 0 | 0 | 0 | Rigorous |

---

*Revisión completada el 10 de agosto de 2026 sobre extracciones `pdftotext -layout -enc UTF-8` de los PDFs originales. / Review completed on August 10, 2026 over `pdftotext -layout -enc UTF-8` extractions of the original PDFs.*
