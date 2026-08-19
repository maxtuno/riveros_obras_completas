# Revisión matemática / Mathematical Peer Review

**Español:** Revisión desde cero sobre extracciones `pdftotext -layout -enc UTF-8` de los 11 PDFs originales, de la versión corregida del undécimo documento y del `.tex` revisado (con su paquete de artefactos) del duodécimo documento y del `.tex` revisado del decimotercero. Cada documento fue leído íntegramente y auditado teorema por teorema, definición por definición, prueba por prueba. La revisión del octavo documento (Locality, Soft Causal Cones, and Informational Limits of Agency) incluye además verificación numérica independiente y auditoría adversarial. La revisión del noveno documento (Teoría de Conservación de Óptimos y Complejidad) incluye además verificación simbólica asistida por computadora (SymPy) y auditoría adversarial. La revisión del décimo documento (COVERTRACE-SAT como Compilación de Conocimiento por Subcubos Disjuntos, documento unificado del Vol. I) incluye además revisión multiagente, verificación computacional independiente (Python 3.13) y auditorías adversariales. La revisión del undécimo documento (nota unificadora Conexiones entre el Teorema de la Ecuación SAT y COVERTRACE-SAT, versión corregida) incluye además segunda ronda de revisión por pares con re-verificación computacional independiente de todas las identidades (aritmética exacta). La revisión del duodécimo documento (Epistemic Closure Nets: Curvature, Holonomy, Certification, and Meta-Closure in an Expansive Network Formalism, versión corregida) incluye además revisión multiagente en dos rondas (seis revisores independientes y un auditor adversario), verificación numérica independiente del nodo experimental P1★ (Python 3.13/numpy) y re-verificación post-corrección (compilación `pdflatex` y auditoría de referencias con 0 problemas). La revisión del decimotercero (Physical Observer Geometry, Protocol Holonomy, Order by Non-Closure, and Spectral Obstructions, versión corregida) incluye además segunda ronda de revisión por pares con re-verificación simbólica (SymPy) y auditorías adversariales cláusula por cláusula.

**English:** Review from scratch over `pdftotext -layout -enc UTF-8` extractions of the 11 original PDFs, of the corrected version of the eleventh document, and of the reviewed `.tex` (with its artifact package) of the twelfth document and of the reviewed `.tex` of the thirteenth. Each document was read in full and audited theorem by theorem, definition by definition, proof by proof. The review of the eighth document (Locality, Soft Causal Cones, and Informational Limits of Agency) also includes independent numerical verification and adversarial auditing. The review of the ninth document (Theory of Conservation of Optima and Complexity) also includes computer-assisted symbolic verification (SymPy) and adversarial auditing. The review of the tenth document (COVERTRACE-SAT as Disjoint-Subcube Knowledge Compilation, unified document of Vol. I) also includes multi-agent review, independent computational verification (Python 3.13), and adversarial audits. The review of the eleventh document (unifying note Connections between the SAT Equation Theorem and COVERTRACE-SAT, corrected version) also includes a second peer-review round with independent computational re-verification of all identities (exact arithmetic). The review of the twelfth document (Epistemic Closure Nets: Curvature, Holonomy, Certification, and Meta-Closure in an Expansive Network Formalism, corrected version) also includes a two-round multi-agent review (six independent reviewers and one adversarial auditor), independent numerical verification of the experimental node P1★ (Python 3.13/numpy), and post-correction re-verification (`pdflatex` compilation and reference audit with 0 problems). The review of the thirteenth document (Physical Observer Geometry, Protocol Holonomy, Order by Non-Closure, and Spectral Obstructions, corrected version) also includes a second peer-review round with symbolic re-verification (SymPy) and clause-by-clause adversarial audits.

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

### 10. COVERTRACE-SAT como Compilación de Conocimiento por Subcubos Disjuntos (Documento Unificado, Vol. I)
(Parte I en inglés, enero de 2026, y Parte II en español, versión corregida · revisión del 14 de agosto de 2026 · `COVERTRACE_SAT_Disjoint_Subcube_Unificado.tex`, 1061 líneas)

#### Veredicto
**CERTIFICADO COMO MATEMÁTICAMENTE SÓLIDO — no se encontró falla fatal.** Todas las afirmaciones centrales de ambas partes fueron verificadas por reconstrucción formal de las pruebas desde primeros principios, verificación computacional exhaustiva e independiente (Python 3.13) y auditorías adversariales orientadas a refutar cada cota, desigualdad e invariante, sin contraejemplos. Los defectos encontrados son exclusivamente de citación, notación y presentación y **no invalidan ninguna afirmación matemática**. La certificación se emite con la condición de corregir las citas (hallazgos 1–5) antes de publicación: defectos bibliográficos, no matemáticos.

#### Inventario de resultados principales
**Parte I (inglés):**
1. **COVERTRACE** (CubeDiff/AddCube): compilación de ¬F en subcubos disjuntos con conteo exacto #SAT y extracción de testigos (Teo. 4.1, Prop. 4.2); cota `O((T+m)·c(n))` (Prop. 5.1).
2. **Cota inferior de paridad:** `χ(O_n) = 2^{n−1}` (Lema 6.1 / Teo. 6.2).
3. **Compilación DSOP y colapso condicional:** compilador polinomial con codificación polinomial ⇒ `PH = P` (Teo. 7.4); certificados UNSAT verificables en polinomio ⇒ `NP = coNP` (§7.5).
4. **Extensión afín** (cosetos de ker A) con compresión exponencial de paridad (Sección 8).
5. **Lema volumétrico 9.2** y **cota por influencia** (Cor. 9.5) para χ; Problema 9.6 declarado abierto; punto de vista GCT (Sección 10).

**Parte II (español):**
6. **Lema del invariante de contención** de COVERTRACE.
7. **Desigualdad `S_part(F) ≤ S_tr(F)`** para toda F insatisfacible (Teo. 2.1) y **contraejemplo explícito verificado `S_part = 6 < 7 = S_tr`** (Prop. 2.2); degradación honesta de PHP a problema abierto con cota 4 (Cor. 2.6).
8. **Cota espectral de Fourier–Walsh:** `χ(S) ≥ 2^d · max_{|α|=d} |f̂(α)|` (Sección 3).
9. **Certificado poliédrico y codificación exacta** `φ_n`/`κ_n` (Sección 4).
10. **Delimitación del Problema 9.6** (Sección 5) y nota de corrección del 14 de agosto verificada contra el cuerpo.

#### Verificado correcto
- **Algoritmos nucleares:** los tres casos de CubeDiff son exhaustivos y mutuamente excluyentes; terminación por decrecimiento estricto. **Exhaustivo n=4 (6561 pares) y n=5 (59049 pares): 0 fallos.** Lema 3.2 verificado bajo sus hipótesis (la cota incondicional falla y el lema la excluye). COVERTRACE: 500 CNFs n=4 y 200 n=5 verificadas tras cada cláusula por fuerza bruta: 0 fallos. Testigos: 259/259 válidos. ✓
- **Cota de paridad:** `χ(O_n) = 2, 4, 8` para n=2,3,4 por DP exacto; ajustada. ✓
- **Colapso condicional:** cada implicación (Valiant, Toda) verificada; el carácter condicional está declarado; §7.5 sólido y completo con verificabilidad `O(K²n + Kmn)`. ✓
- **Lema 9.2:** los 255 subconjuntos no vacíos de {0,1}³, 0 violaciones (87 ajustados). **Cor. 9.5:** 254 exhaustivos n=3 + 200 muestrales n=4: 0 violaciones. ✓
- **Desigualdad `S_part ≤ S_tr`:** 34.071 CNFs insatisfacibles n=3 (≤5 cláusulas) + 254 n=4: 0 violaciones. **Prop. 2.2 (6<7):** confirmada por tres implementaciones independientes, DP de recubrimiento exacto sobre los 2^16 subconjuntos, punto fijo de resolución arbórea `D(⊥) = 7` (equivalencia BKPS en 61 instancias, 0 discrepancias) y **enumeración exhaustiva de todos los árboles con ≤6 hojas sobre 4 variables (26.657 propios + 46.949 con reconsultas: 0 refutantes)**. ✓
- **Cota espectral:** 256×4 desigualdades n=3, 0 fallos, ajustada; ejemplos paridad y mayoría verificados numéricamente. ✓
- **Certificado poliédrico y codificación:** verificación punto a punto (n=4, 16 puntos); contraejemplo fraccional verificado; restricción a integralidad necesaria y declarada en el texto. ✓
- **Auditorías adversariales:** ninguna hipótesis de refutación (error algebraico, conclusión que no se sigue, contraejemplos a cotas o invariantes) sobrevivió a su propio escrutinio. ✓

#### Hallazgos
| # | Tipo | Descripción |
|---|------|-------------|
| 1 | **Obligatoria (citación)** | `kmr15`: los autores impresos (Kothari, Meka, Raghavendra) no corresponden al artículo citado; el real es Kothari–Racicot-Desloges–Santha, *Separating Decision Tree Complexity from Subcube Partition Complexity*, APPROX/RANDOM 2015, LIPIcs 40:915–930. |
| 2 | **Obligatoria (citación)** | `hegyvari24` no existe como está impresa (revista y título erróneos); el real es N. Hegyvári, *The complexity of subcube partition relates to the additive structure of the support*, Information and Computation 299:105170 (2024). |
| 3 | **Obligatoria (citación)** | `koriche13`: título mal citado (real: *Knowledge Compilation for Model Counting: Affine Decision Trees*, IJCAI 2013); además nunca se invoca en el texto. |
| 4 | **Obligatoria (citación)** | Falta la entrada de Valiant para la #P-completitud de #SAT, invocada en la prueba del Teo. 7.4. |
| 5 | **Obligatoria (citación)** | Ningún `\cite` en todo el documento; varias entradas nunca mencionadas en el texto (ms01, ms08, bi25, dip19, lucas14, bbbv97, koriche13, hegyvari24, Ben-Sasson–Wigderson 2001). |
| 6 | Menor (presentación) | «Teoremas 4.1–4.3» incluye la Observación 4.2 en el rango; el resumen dice generalizar la Prop. 9.4 cuando corresponde al Cor. 9.5; hipótesis del Lema 3.2 elididas en el resumen; Remark 4.3 de la Parte I con redacción laxa; cobro esquemático en Prop. 5.1 (explicitar el conteo ≤ T+m); anotación de Urquhart 1987 que menciona PHP (corresponde a Haken 1985/folclore); notación x_0..x_3 vs x_1..x_n; índice de «bi25» sin número de artículo; costo de suma de volúmenes O(K) a nivel de palabra (O(Kn) a nivel de bits, sigue polinomial). |
| 7 | Observación de originalidad | `S_part ≤ S_tr` es consecuencia directa de la equivalencia clásica resolución arbórea ↔ árboles de decisión (Beame–Karp–Pitassi–Saks 2002, citada) y `χ(O_n) = 2^{n−1}` es folclórica; la novedad genuina reside en el contraejemplo explícito verificado (6<7), las cotas espectrales ajustadas y la delimitación honesta del Problema 9.6. |

---

### 11. Conexiones entre el Teorema de la Ecuación SAT y COVERTRACE-SAT (Nota Unificadora)
(11 páginas, 8 referencias · nota del 15 de agosto de 2026 · segunda ronda de revisión, versión corregida · `Conexiones_SAT_Equation_COVERTRACE_ES.tex`)

#### Veredicto
**ACEPTADO (CERTIFICACIÓN).** La versión corregida pasa la revisión por pares. Todas las correcciones obligatorias (C1–C4) y recomendadas (C5–C6) del informe anterior fueron aplicadas, y el defecto fatal (el lema de volteo falso) quedó eliminado: el lema ahora enuncia la identidad correcta de volteo (XOR), con prueba válida y un párrafo que documenta explícitamente la diferencia con la suma aritmética. La verificación computacional independiente se repitió por completo: **todas las afirmaciones del documento corregido se verifican exactas** (0 fallos en cada suite), y el documento compila sin errores ni referencias sin resolver.

#### Inventario de resultados principales
1. **Identidad fundamental:** `popcnt(S(F)) = |U(F)| = Σ_{u∈U} vol(u)` — la bitmask entera densa de `2ⁿ` bits (Ecuación SAT) y la familia disjunta de subcubos (DSOP de ¬F, COVERTRACE) codifican el mismo objeto: la región prohibida `U(F) ⊆ Ω_n`.
2. **Dualidad acarreo–disyunción:** los acarreos de la suma aritmética son exactamente los solapamientos que el invariante disjunto de COVERTRACE elimina; el OR bit a bit es su idempotización.
3. **Lema de volteo (XOR):** `t(k⊕2^j) = 1 − t(k)` para todo k,j, probado vía la paridad de `popcnt`; el texto advierte explícitamente que la versión de adición `t(k+2^j) = 1 − t(k)` es falsa (30,9 % de contraejemplos).
4. **Paridad como número de Thue–Morse:** el entero de la Ecuación SAT de la paridad es el número de Thue–Morse: su expansión binaria es la palabra de Thue–Morse de longitud `2ⁿ`; `popcnt(S_n) = 2^(n−1) = χ_⊔(O_n)`, igualando también la cota espectral de Fourier–Walsh de la Parte II.
5. **Forma cerrada:** `S_C = 2^B · Π(1 + 2^{2^(n−i)})`; dualidad (c): OR = AddCube bit a bit; multiplicidades en base b.
6. **Corolario de la representación densa:** el mayor subcubo en `O_n` tiene tamaño 1 → cobertura óptima por singletons, `χ_⊔(O_n) = 2^(n−1)`.
7. **Comparación densa–dispersa** (conteo, pertenencia, extracción de testigos, actualización) y reformulación de los problemas abiertos del corpus en el lenguaje de la bitmask.

#### Verificado correcto (aritmética exacta, re-verificación independiente)
- **Lema de volteo XOR** `t(k⊕2^j) = 1−t(k)`, n=1..10: 0 fallos; contraste con la identidad de adición `t(k+2^j) = 1−t(k)`, k<2^10: 2845/9217 fallos = 30,9 % (coincide con el texto). ✓
- **Corolario:** mayor subcubo en `O_n`, n=1..4: tamaño 1 (cobertura óptima por singletons). ✓
- **Forma cerrada** `S_C = 2^B·Π(1+2^{2^(n−i)})`: cláusula unitaria 15, balanceada 12, vacía 255, mixta 20560 — todas iguales al OR directo. ✓
- **Thue–Morse:** recursión = fórmula producto, n=0..8: `S_1=2, S_2=6, S_3=150, S_4=27030, S_5=2523490710, S_6=7608434000728254870`; `popcnt(S_n)=2^(n−1)`, n=1..8: 1,2,4,8,16,32,64,128; morfismo `W_(n+1)=W_n·W̄_n` y `μ⁴(0)=W_4=0110100110010110`. ✓
- **Factorización de Walsh:** todo `α⊆[n]`, n=1..7: 254/254 casos. ✓
- **Cota espectral:** `F̂f([n])=−½`, `2^n·|F̂|=2^(n−1)`, n=1..9: −1/2; 1,2,4,…,256. ✓
- **Identidad fundamental (CubeDiff/AddCube):** 200 CNFs, 0 fallos (disyuntividad, cobertura bit a bit, popcnt=Σvol). **Dualidad (c):** OR = AddCube bit a bit, 200 CNFs, 0 fallos. **Multiplicidades base b:** 50 CNFs, 0 fallos. ✓
- **Contraejemplo de la Parte II:** UNSAT, S(F)=65535, certificado de 6 cubos (vol. 16), árbol de 7 hojas; `S_part = 6 < 7 = S_tr`. **Convenciones:** `T(C)+B(C)=2^n−1`. ✓

#### Hallazgos
Todas las correcciones de la primera ronda fueron aplicadas y verificadas en la versión corregida:

| # | Tipo | Descripción | Estado |
|---|------|-------------|--------|
| C1–C2 | Obligatoria (matemática) | Lema de volteo: `+` → `⊕`, prueba corregida («voltear el bit j cambia popcnt(k) en ±1») | Aplicada (líneas 224–234) |
| — | Aclaratoria | Párrafo que documenta el contraejemplo 3+2=5 y la condición exacta de la identidad de adición | Añadido (línea 236) |
| C3 | Obligatoria | Justificación del Corolario reparada (lema corregido + derivación alternativa: cota espectral + cobertura trivial de singletons) | Aplicada (línea 260) |
| C4/C4b | Obligatoria | «Todas las identidades…» cualificada a la lista efectivamente verificada; 4 nuevos ítems de verificación añadidos | Aplicada (líneas 399–417) |
| C5 | Obligatoria (citación) | `\cite` para las 8 entradas bibliográficas; autores de `kmr15` corregidos (Kothari–Racicot-Desloges–Santha) | Aplicada |
| C6 | Obligatoria | Prop. Sección 8.1: O(mn) precisado (forma de patrón; materializar cuesta 2ⁿ bits) | Aplicada (línea 359) |
| M1–M7 | Menores | Notación prestada definida; «fragmentación es nula» → «lineal en el número de cláusulas»; convención MSB/LSB aclarada; hipótesis no tautológica reemplazada; alcance del acarreo cualificado; sondas de palabra; exponente base b | Aplicadas |

**Estado del documento:** compila con `pdftotext`-verificado `pdflatex` (3 pasadas) sin errores, sin advertencias de referencias sin resolver ni citas sin definir; 11 páginas; las 8 entradas bibliográficas quedan citadas en el cuerpo. **Sin regresiones:** las verificaciones de los resultados no tocados (Thue–Morse, Walsh, espectral, identidad fundamental, base b, contraejemplo de la Parte II) se repitieron y pasaron íntegras.

---

### 12. Epistemic Closure Nets: Curvature, Holonomy, Certification, and Meta-Closure in an Expansive Network Formalism
(manuscrito de febrero de 2026 · revisión del 17 de agosto de 2026 · `Epistemic_Closure_Net - Riveros.tex`, 1898 líneas en la versión revisada y 1965 tras aplicar las correcciones de la Adenda §7, más el paquete de artefactos `artifact/`)

#### Veredicto

**CERTIFICACIÓN DE SOLIDEZ — sin falla fatal.** Todas las afirmaciones esenciales del manuscrito (contribuciones C1–C6) y todos los resultados etiquetados `[Proved]` están correctamente sustentados por las definiciones, axiomas, demostraciones, datos y artefactos presentados. El manuscrito **no debía publicarse en su forma original** sin cuatro correcciones obligatorias (defectos D1–D4), pero se demostró que ninguna de ellas invalida o revierte conclusión alguna del documento: todas son brechas de especificación/etiquetado reparables en una pasada de revisión, y las afirmaciones centrales sobreviven a cualquier completación razonable de esas definiciones.

Este veredicto sobrevivió una auditoría adversaria dedicada: un revisor con la hipótesis explícita de que el manuscrito contenía una falla fatal intentó elevar cada defecto candidato a falla fatal y, en cada caso, demostró que la afirmación esencial correspondiente permanece en pie.

**Estado actual (post-corrección):** las correcciones obligatorias D1–D4 y todas las menores accionables ya fueron aplicadas al manuscrito y al artefacto, y el documento corregido fue re-verificado (Adenda §7): compila sin errores, las referencias internas auditan con 0 problemas y los valores numéricos del artefacto no cambiaron. La certificación de solidez se mantiene, ahora **sin correcciones pendientes obligatorias**. Los números de línea citados se refieren a la versión revisada original; la Adenda §7 detalla los cambios aplicados y su re-verificación.

#### Metodología de la revisión

La revisión se ejecutó con un equipo multiagente en dos rondas y verificación computacional independiente del revisor principal:

- **Ronda 1 (6 revisores independientes, dimensiones disjuntas):** (i) consistencia interna y numeración de referencias cruzadas; (ii) verificación línea por línea de todas las demostraciones `[Proved]`; (iii) validez estadística y verificación numérica del nodo experimental P1★; (iv) caza adversarial de fallas fatales; (v) completitud de definiciones, notación, metateoría y cumplimiento de las reglas de auditabilidad A1–A5; (vi) mapeo de afirmaciones-entregas, fundamentación bibliográfica y reproducibilidad de artefactos.
- **Ronda 2 (1 auditor adversario):** verificación adversaria del veredicto emergente de certificación, intentando escalar cada defecto candidato a falla fatal.
- **Verificación numérica independiente:** reconstrucción analítica del arnés P1★ desde las Definiciones 9.16–9.18 y el Remark 9.4, con ejecución de código propio (Python 3.13/numpy), además de la ejecución del artefacto entregado.
- No se buscó en la web discusión previa sobre este manuscrito; solo se usó trasfondo matemático/estadístico estándar.

#### Verificación positiva (evidencia de solidez)

**Consistencia axiomática.** El Teorema 4.2 (`[Proved]`) exhibe un modelo explícito de los Axiomas 3.1–3.9. Se verificó **axioma por axioma** que el modelo los satisface: 3.1 (observable trivial que factoriza por `X/Sim`), 3.2 (sonido vacuo con `Cert ≡ 0`), 3.3 (zipper vacío, `T = ∅`), 3.4 (`err ≡ 0` semicontinua inferiormente), 3.5 (`μ(Ω) = 1 < ∞`, medibilidad trivial), 3.6 (i)–(iv) con `S_∞ = {S_0}` compacto, `ω ≡ 0`, bancos anidados y `ε_N = 0`-red, 3.7 (`E` funtor constante `∅ → ∅` en `Meas^⊇(Θ)`), 3.8 (atlas de una carta, `g_11 = id`, cociclos triviales), 3.9 (vacuo a nivel de presentación). El sistema de axiomas es conjuntamente satisfacible en ZFC; el Axioma 3.9 (meta-axioma de silencio) no asevera nada de primer orden y no genera contradicción.

**Resultados `[Proved]` — todos correctos**

| Resultado | Veredicto |
|---|---|
| Prop. 2.1 (rigidez ⇒ acción de gauge, homomorfismo) | Correcto (functorialidad del pushforward; sin circularidad con Prop. 4.1) |
| Lema 4.1 (monotonicidad de `κ_R`) | Correcto |
| Lema 4.2 (abertura de `Mod(Φ)` en cGCNF) | Correcto |
| Teo. 4.1 (transferencia de banco finito desde módulo de continuidad) | Correcto; la cadena `F(θ,S') ≤ F(θ,S) + ω(ε_N) < −τ` es válida con la desigualdad estricta |
| Cor. 4.1 (caso Lipschitz) | Correcto |
| Teo. 4.2 (no-contradicción kernel/SCE-IM) | Correcto (modelo verificado axioma por axioma) |
| Teo. 4.3 (holonomía trivial en el índice; iff en nivel programa) | Correcto (`E` aterriza en un poset; `μ((E_1∩K)△(E_2∩K)) = 0` iff acuerdo c.s.) |
| Teo. 4.4 (cociclo no trivial obstruye trivialización global) | Correcto (el descenso `g_ij = η_i^{-1}η_j` telescopa; "solo id es conjugado de id") |
| Prop. 4.1 (invarianza de gauge, conjugación de cociclos) | Correcto (`h'_{ijk} = a_i h_{ijk} a_i^{-1}`, álgebra verificada) |
| Prop. 4.2 (invarianza de curvatura bajo transporte rígido) | Correcto |
| Teo. 4.5 (certificación solo-sonido no fuerza obstrucción diagonal) | Correcto (no-implicación vía modelo con `Cert ≡ 0`) |
| Prop. 5.1 (independencia de `Σzip` y `(Hol_atlas, Hol_prot)`) | Correcto en sustancia: los pares de modelos testigo comparten el componente SCE-IM (dirección 1) y la estructura trivial de holonomía (dirección 2); el argumento funciona para **cualquier** completación de las componentes no definidas (ver D2) |
| Teo. 9.1 / Teo. 9.2 (cotas de Hoeffding) | Correctos (`X_t ∈ [0, μ_Θ(K)]` ⇒ `2e^{−2Tε²/μ(K)²}`; Bernoulli ⇒ `2e^{−2Tε²}`) |
| Prop. 9.1 (tamaño de muestra `T(ε,η) = ⌈(1/2ε²)log(2/η)⌉`) | Correcto (despeje verificado) |

También se verificaron (aunque etiquetados `[Model]`) el Lema 9.1 (transferencia Lipschitz-red del pool, correcto), la Prop. 9.2 (diagnóstico persistente de corte, correcta) y el esquema de la Prop. 9.3 (cotas superior e inferior de la zona gris, correcto incluyendo la condición `c_0 c_1 ε_N ≥ ω(ε_N)` y la exclusión estricta `F_s ≥ −τ`).

**Verificación estadística**

- Cotas de Hoeffding, fórmula de `ε_T = μ_Θ(K)√(log(2/η)/2T)` (Def. 9.30) y regla de decisión: todas correctas.
- MMD (Def. 9.14): fórmula U-estadística estándar no sesgada de Gretton et al. (2012).
- Wasserstein-1 por dualidad Kantorovich–Rubinstein (Def. 9.13): correcta.
- Sustitución ESS para MCMC (Remark 9.2): honestamente etiquetada `[Model]` con advertencia explícita de anti-conservatividad bajo mezcla lenta — apropiado.

**Nodo P1★ (contribución C6) — verificación numérica independiente**

- **Álgebra (Prop. 9.2):** el intercepto del protocolo fino es `(u₂g(u₁,m) − u₁g(u₂,m))/(u₂−u₁) = θ₀ + dm − f·u₁u₂` (los términos `(c+em)` se cancelan); verificado numéricamente: sesgo `−0.0449999921 = −f·u₁u₂` exacto. Con la rejilla `m ∈ {−0.5, 0, 0.5}` simétrica, la etapa `m → 0` es exacta y `mid_fine → θ₀ − f·u₁u₂`, `mid_full → θ₀`. La constante `|f|·u₁u₂ = 299.875 × 0.01 × 0.01500625 = 0.045000` ✓.
- **Normas de funcionales lineales:** calculadas independientemente desde la matriz de diseño: `‖φ_fine‖ = 2.079667`, `‖φ_full‖ = 0.721372` — idénticas a las registradas en `audit_log.json` (2.0796669 / 0.7213721).
- **Consistencia cuantitativa de la Tabla 1:** con `σ̂² = RSS/(12−5)` (insesgado para `σ²/n_cfg`) y `E[√(χ²₇/7)] = 0.96503`, la predicción analítica es `E[Û] = 2σ·E[√(χ²₇/7)]·‖φ_fine‖/√n_cfg = 4.4917/√n_cfg`. Los valores de la tabla dan `Û·√n_cfg = 4.377, 4.475, 4.479, 4.443, 4.508, 4.606` (media ≈ 4.48), con desviaciones z ≤ 2.3σ — consistentes con ruido Monte Carlo de 600 réplicas. Las desviaciones típicas de replicación predichas (`CV(σ̂) ≈ 0.267 ⇒ std ≈ 0.267·Û`) coinciden con las columnas s.e.×√600 de la tabla a 3–4 cifras significativas en todos los niveles.
- **Reproducibilidad del artefacto:** la ejecución fresca de `artifact/P1star_cut_state/p1star_cut_state.py` reproduce byte a byte `table_results.csv` y todos los valores impresos de la Tabla 1 y Figura 2; pendiente log–log `−0.4944`; parámetros congelados (`f = 299.875`, `σ = 1.119`, `R = 600`, `master_seed = 20260817`, `ε_U = 0.05`, `Δ_min = 0.0225`) registrados en `audit_log.json` conforme al Remark 9.4 y la Def. 9.19. Ambas decisiones pre-registradas pasan: colapso `0.02628 ≤ 0.05` ✓; holonomía persistente `0.045254 − 2×0.000517 = 0.04422 ≥ 0.0225` ✓. El script del esqueleto GW150914 (P1★★) verifica la puerta A5: rechaza ejecutarse sin archivo de pre-registro congelado.

**Referencias cruzadas y numeración.** 146 referencias internas auditadas contra el esquema de contadores independientes por entorno: **0 referencias rotas**, 0 objetivos mal numerados. Todas las referencias específicamente críticas (`Section 9.7.2` = P1★, `9.7.4` = P2, `9.8`, `Section 10`, Defs. 9.12/9.15/9.19/9.21/9.22/9.23/9.30, Defs. 10.7/10.8, Conj. 7.1/7.3, Rem. 9.1/9.4/9.9/9.11, Teos. 4.1/4.2/9.1/9.2, Props. 4.1/9.1–9.3, Lema 9.1, Axioma 3.6, Defs. 2.11–2.20, Tabla 1, Figura 2) resuelven correctamente. Dos imprecisiones menores de atribución (M1: `ε_hol` se atribuye a Def. 9.30 cuando se define en Def. 9.12; M2: la métrica `d_S` se atribuye a Def. 9.15 cuando se introduce como hipótesis del Lema 9.1).

**Entrega de contribuciones**

| Contribución | Veredicto | Soporte |
|---|---|---|
| C1 (red de clausura tipada) | Entregada | Defs. 2.1–2.23, Def. 2.21, Figura 1 |
| C2 (holonomía índice-trivial vs nivel-programa) | Entregada | Def. 2.14, Teo. 4.3, Defs. 9.3/9.5, Rem. 9.1 |
| C3 (cociclos de atlas obstruyen trivialización) | Entregada | Teo. 4.4 `[Proved]` + Prop. 4.1 |
| C4 (transferencia de banco finito + estimadores) | Entregada (con nota) | Teo. 4.1 `[Proved]`, Def. 9.23 (`d_eff`); nota: no se da estimador directo del módulo `ω`, solo de `d_eff` y de la pendiente compuesta `α/d_eff` |
| C5 (nodos experimentales verificables) | Entregada como especificación | P1–P5 con cotas Hoeffding, patrones de falsificación y pre-registro |
| C6 (nodo artefacto P1★) | Entregada y reproducible | §9.7.2, Tabla 1/Figura 2, Prop. 9.2, Def. 9.19, `artifact/` ejecutado |

Reglas A1–A5: cumplidas en lo sustantivo, con las desviaciones documentadas abajo.

#### Defectos demostrados — todos nivel-revisión (obligatorios antes de publicar; todos corregidos en la Adenda §7)

**D1 (error matemático real, no fatal): convención de composición en Def. 2.19 vs cociclo de Def. 2.20.** La Def. 2.19 (líneas 350–353) afirma que la familia de transiciones "adquiere una estructura de grupoide (con composición `g_ik := g_jk ∘ g_ij`) exactamente cuando todos los cociclos triples son triviales", donde el cociclo (Def. 2.20, línea 363) es `h_ijk := g_ij ∘ g_jk ∘ g_ki`. **La afirmación era falsa tal como estaba escrita**: con esa convención de composición la condición de consistencia es `g_jk ∘ g_ij ∘ g_ki = id`, que en grupos no abelianos no equivale a la del cociclo declarado. Contraejemplos verificados computacionalmente en `S₃`:

- `g₁₂ = (12)`, `g₂₃ = (23)`, `g₃₁ = (132)`: el cociclo del paper da `h₁₂₃ = id` ("holonomía trivial") pero la composición declarada da `g₂₃ ∘ g₁₂ = (132) ≠ g₁₃ = (123)` — no hay grupoide.
- `g₁₂ = (12)`, `g₂₃ = (23)`, `g₃₁ = (123)`: familia totalmente consistente (todos los caminos coinciden), pero el cociclo del paper da `h₁₂₃ = (132) ≠ id` — "holonomía no trivial" declarada sin dependencia de camino alguna.

Cascada: la Prop. 6.3 (`[Model]`, líneas 759–763), "Hol_atlas ≠ 0 ⇒ hay dependencia de camino", era falsa bajo la convención escrita (segundo contraejemplo) y trivialmente verdadera solo bajo la lectura tautológica del propio `h`. Se repara con la misma corrección de convención.

Alcance: ningún resultado `[Proved]` dependía de la frase defectuosa. El Teorema 4.4 (único pilar de C3) es correcto: el cálculo de descenso telescopa bajo cualquier convención, y la dirección de obstrucción demostrada es exactamente la afirmada. Prop. 4.1, Axioma 3.8 y el Modelo (b) de la Prop. 5.1 son internamente consistentes con el cociclo tal como está definido. La Conjetura 7.3 queda intacta.

Corrección (una línea): redefinir la composición como `g_ik := g_ij ∘ g_jk` (o, equivalentemente, redefinir `h_ijk := g_jk ∘ g_ij ∘ g_ki`) y reestablecer la Prop. 6.3 en consecuencia. Con la corrección, "grupoide ⟺ cociclos triviales" es verdadero y la Prop. 6.3 es demostrable. **Aplicada** (Prop. 6.3 re-etiquetada `[Proved]` con demostración).

**D2 (brecha de definición, no invalida el teorema): `MT_I` y `τ^o` sin definir.** La firma zipper `Σzip(E,o) := (κ(o), MT_I(o), τ^o)` (Def. 5.1, líneas 689–696) contenía dos componentes que **nunca se definían** (árbol de fusión `MT_I` y tiempos de arribo `τ^o`; tampoco se especificaba el intervalo `I` de umbrales). Aparecen en la prueba de la Prop. 5.1 ("merge tree trivial, hitting times triviales", línea 722), en H3, la Conjetura 7.1 y el nodo P4. Por qué no es fatal: la prueba de independencia de la Prop. 5.1 usa únicamente que (i) `Σzip` es una función del componente SCE-IM y (ii) los modelos testigo de cada dirección comparten **el mismo componente SCE-IM** (los Modelos (a)/(b) reutilizan verbatim el SCE-IM del Teorema 4.2; la segunda dirección solo cambia `err` de 0 a 1 manteniendo la holonomía trivial). Por tanto la no-implicación queda establecida **para cualquier completación** de `MT_I`/`τ^o`: ningún punto de la prueba depende de su contenido. Ningún resultado `[Proved]` calcula o descompone esas componentes. **Corregida:** Def. 5.1 reescrita (subniveles `S_ε(o) := {σ : err(σ,o) ≤ ε}` cerrados por semicontinuidad inferior, Axioma 3.4; árbol de fusión de la filtración sobre `I`; tiempo de arribo `τ^o(σ) := inf{ε ∈ I : σ ∈ S_ε(o)}` con `inf ∅ := +∞`).

**D3 (abreviatura subespecificada): forma de cuatro argumentos de `Δ_loop`.** La Def. 5.3 (líneas 703–709) afirmaba que `Δ_loop(N,N′,τ,δ;K)` abrevia la magnitud de nivel programa de la Def. 9.5 evaluada en el par canónico de protocolos de la Def. 9.21, pero `(N,N′,τ,δ)` **no determina** el estado inicial `c₀ = (S,τ,ξ)` ni el número `m` de pasos de aumentación que la Def. 9.21 exige; además los roles de `N,N′` (contravariantes en el índice, Def. 2.14) quedaban sin correspondencia declarada con `Aug^m` (que *aumenta* el banco). Por qué no es fatal: la Prop. 5.1 no usa esta forma (Modelo (a): sin programas de refinamiento; segunda dirección: holonomía trivial conservada). Los usos restantes (Prop. 6.2 `[Model]`, Conjetura 7.1) quedan bien planteados con la completación natural `m := N′−N`, `c₀ := (S_N, τ, ξ₀)` con `ξ₀` declarado — una línea. La contribución C2 descansa en el Teo. 4.3 y la Def. 9.5, no en esta abreviatura. **Corregida:** Def. 5.3 completada (`c₀ = (S_N, τ, ξ₀)` fijo pre-registrado, `m := N′−N` (N′ ≥ N), `p₁ = Aug^m∘Tighten_δ`, `p₂ = Tighten_δ∘Aug^m`); tercera aridad `Δ_loop(c_r; K) := Δ_loop(p₁(r), p₂(r); K)` definida en Def. 6.1; límite incoherente de la Prop. 6.2 corregido ("as N → ∞ con N′ ≥ N en barrido pre-registrado y (τ, δ, K) fijos").

**D4 (error de reporte, no de conclusión): la Tabla 1 no implementaba el estimador definido.** La Def. 9.18 (línea 1272) definía `Δ̂_cll := dist_H(I_fine, I_full)`, la distancia de Hausdorff de los intervalos de incertidumbre, con el paréntesis "igual a la diferencia de puntos medios **cuando los anchos coinciden**". El script y la Tabla 1 computaban solo `|mid_fine − mid_full|`; los anchos **no** coinciden (`‖φ_fine‖ = 2.0797`, `‖φ_full‖ = 0.7214`), de modo que la distancia de Hausdorff literal es `|mid diff| + 2σ̂(2.0797 − 0.7214)`:

| N | Tabla 1 (reportado) | Hausdorff literal (esperado) |
|---|---|---|
| 360 | 0.3009 | 0.8365 |
| 1440 | 0.1734 | 0.4412 |
| 5760 | 0.0834 | 0.2173 |
| 23040 | 0.0520 | 0.1190 |
| 92160 | 0.0449 | 0.0784 |
| 368640 | 0.0453 | 0.0620 (MC independiente: 0.06242 ± 0.000547) |

Por qué no es fatal: (i) los límites de la Prop. 9.2 son idénticos bajo ambos estimadores, porque ambos anchos `ŵ_p = 2σ̂‖φ_p‖ → 0` y `lim Δ̂ = lim|mid_fine − mid_full| = |f|u₁u₂ = 0.045`; (ii) el régimen diagnóstico de C6 (`Û → 0` mientras `Δ̂ ↛ 0`) se mantiene y es numéricamente más fuerte; (iii) **ambas decisiones pre-registradas siguen pasando** bajo el estimador literal (colapso: `0.02628 ≤ 0.05`; holonomía: `0.06242 − 2×0.000547 = 0.06133 ≥ 0.0225`). **Corregida:** Def. 9.18 redefinida como `Δ̂ := |mid_fine − mid_full|` (separación de puntos medios) con nota de la relación con la distancia de Hausdorff y del límite común `|f|u₁u₂`; docstring del script corregido.

#### Problemas menores (recomendados, no bloqueantes; todos los accionables corregidos)

1. **Notación sobrecargada no declarada:** `E` (instancia SCE-IM vs funtor de conjuntos certificados — colisión literal en la lista de nodos de la Def. 2.21), `S` (espacio sintáctico vs plantilla vs instancia de banco), `T` (dientes vs cartas vs tamaño de muestra), `K` (kernel vs ventana vs kernel de Markov), `F` (evolución vs puntaje vs CNF), `Φ` (dinámica vs fórmula), `Ω` (espacio semántico vs región de validez), `I` (alcance vs índice de cartas vs intervalo), `τ` (diente en Axioma 3.3 vs margen real en la capa de banco), `Prob` (conjunto de medidas vs categoría). Contextualmente no ambiguos en todas las fórmulas verificadas, pero deberían declararse en la sección de notación. **Corregido** (nuevo Remark 1.1 "Notation hygiene: declared overloads").
2. **Primitivos sin definir:** la familia de ventanas `𝒦` (Def. 2.6/Axioma 3.5) y el dominio "intentado" `A_r` (Def. 2.18) nunca se definían; `D_τ` (Axioma 3.3) quedaba huérfano (nunca se usa). `Autrig(N_r)` se define vía "Def. 2.23 aplicada fibra a fibra" sin especificar la rigidez de la red completa — recuperable, pero era el punto más blando del núcleo geométrico. **Corregido** (`𝒦` definida en Def. 2.5; `A_r` declarado como dato pre-registrado en Def. 2.18; `D_τ` declarado como región de restricción semántica del diente en Axioma 3.3; Def. 2.22 especifica qué preserva la rigidez; paréntesis de conjuntos analíticos del Axioma 3.6(iii) precisado: espacio Borel estándar ⇒ proyección analítica ⇒ universalmente medible).
3. **A4 (barras de error):** la pendiente ajustada `−0.494` (Remark 9.4) se reportaba sin barra de error, y las Props. 6.1–6.5 `[Model]` enuncian leyes asintóticas sin contrato de incertidumbre explícito (sí referencian estimadores auditables en §9). **Corregido** (Remark 9.4: "−0.4944 ± 0.0019 (1σ, propagada de los errores estándar de replicación)").
4. **A5 (pre-registro):** en el orden del documento el Remark 9.4 reporta resultados *antes* de la Def. 9.19 que fija la regla congelada; la verificación del congelamiento descansaba solo en `audit_log.json`. Los umbrales están derivados del modelo (`ε_U`, `Δ_min = |f|u₁u₂/2`) y no de los datos, pero la evidencia de congelamiento previo era declarativa. Los estudios de caso C y D carecían de plantillas de pre-registro completas. **Corregido** (Remark 9.4 abre declarando que parámetros y regla se congelaron antes del muestreo y constan en el audit log; Remark 10.2 extiende el esquema de pre-registro a los casos C y D).
5. **Bibliografía:** 4 de 11 entradas (`egc, geg, ceg, fbc`, preprints del propio autor) nunca se citaban en el texto; las citas realmente usadas (Hoeffding, Paulin, Gretton, Villani, Giraud, Breen, GW150914) están correctamente aplicadas. **Corregido** (ahora citados en abstract, Remark 2.1, Defs. 2.9/2.10).
6. **Etiquetas de evidencia:** la Prop. 6.3 estaba etiquetada `[Model]` siendo (tras la corrección D1) demostrable — sub-reclama; la Prop. 4.1 `[Proved]` incluye una conjunción condicionada a la Conjetura 7.3 (invarianza de la *clase de cohomología*) que no está probada — la redacción condicional es honesta pero la etiqueta excedía su alcance. **Corregido** (Prop. 6.3 re-etiquetada `[Proved]`; la cláusula de clase de cohomología quedó como condicional explícita "no probada aquí").
7. **Teorema 4.3 (parte índice):** "demuestra" en parte una declaración (Def. 2.14); su contenido sustantivo es solo `E(p₁) = E(p₂)` por destino posetal — correcto pero sobre-etiquetado. **Corregido** (prueba reformulada: el valor declarado en Def. 2.14 es consistente con el cálculo posetal).
8. **R2 del contrato de artefactos:** `audit_log.json` no contenía hash/versión del código (R2 de la Def. 10.8), pese a que el Remark 9.5 afirma conformidad R1–R5. **Corregido** (el script ahora calcula y registra `code_id` (SHA-256 de su propio código) en `audit_log.json`).
9. **Atribución de referencias menores (M1, M2).** **Corregido** (M1: la tolerancia `ε_hol` cita Def. 9.12 junto con Def. 9.30; M2: la métrica `d_S` cita el Lema 9.1).
10. **Figura 1** nunca se referenciaba en el texto; el pie mencionaba "Sections 1–3" aunque la Sección 1 no define morfismos. **Corregido** (ahora referenciada en el texto (§8) y el pie cita "Sections 2–3"; residuos menores: "public-style" eliminado; lista de nodos de Def. 2.21 sin doble "E").

#### Conclusión

El manuscrito cumple lo que promete en su propia declaración de alcance ("una capa de especificación auditable, no un teorema de completitud del conocimiento científico"): sus afirmaciones están tipadas por evidencia, los resultados `[Proved]` son correctos (verificados uno a uno, con el modelo de consistencia comprobado axioma por axioma), los resultados `[Model]`/`[Conjecture]` están aislados como tales con patrones de falsificación pre-registrados, los estimadores estadísticos son estándar y están bien aplicados, y el nodo artefacto P1★ es genuino y reproducible: la Tabla 1 es cuantitativamente consistente con el modelo generativo declarado y se reproduce al dígito con el script entregado.

Los cuatro defectos demostrados (D1–D4) eran reales y obligatorios de corregir antes de publicar — un error de convención de composición con una proposición `[Model]` colateral (D1), dos componentes del invariante `Σzip` sin definir (D2), una abreviatura de `Δ_loop(N,N′,τ,δ;K)` subespecificada (D3) y una columna de la Tabla 1 que no implementaba el estimador definido (D4) — pero en cada caso se demostró, con contraejemplos, recálculos y ejecuciones, que **ninguna afirmación esencial (C1–C6) ni resultado `[Proved]` quedaba invalidado**: los teoremas, los modelos testigo, las decisiones pre-registradas y el régimen diagnóstico de C6 sobreviven a las correcciones y a cualquier completación razonable.

**Veredicto final: ACEPTAR CON REVISIONES OBLIGATORIAS (certificación de solidez; sin falla fatal).** Estado post-corrección (Adenda §7): **certificación mantenida, sin correcciones pendientes obligatorias.**

#### Adenda §7 — correcciones aplicadas y re-verificación (17 de agosto de 2026)

**7.1 Correcciones aplicadas**

| # | Corrección | Cambio |
|---|---|---|
| D1 | Convención de composición de Def. 2.19 | `g_ik := g_jk ∘ g_ij` → `g_ik := g_ij ∘ g_jk` con dirección declarada ("`g_ij` lee cantidades de la carta `j` en la carta `i`") y frase explícita: el cociclo `h_ijk = g_ij∘g_jk∘g_ki` es exactamente la obstrucción a `g_ik = g_ij∘g_jk` |
| D1c | Prop. 6.3 (colateral de D1) | Re-etiquetada `[Proved]` con enunciado reformulado (dos caminos de cartas entre el mismo par) y demostración añadida (vía `g_ij∘g_jk ≠ g_ik` ⇒ sección movida) |
| D2 | `MT_I` y `τ^o` sin definir | Def. 5.1 reescrita: subniveles `S_ε(o) := {σ : err(σ,o) ≤ ε}` (cerrados por semicontinuidad inferior, Axioma 3.4), árbol de fusión de la filtración sobre `I`, y tiempo de arribo `τ^o(σ) := inf{ε ∈ I : σ ∈ S_ε(o)}` con `inf ∅ := +∞` |
| D3 | Forma de 4 argumentos de `Δ_loop` | Def. 5.3 completada: `c₀ = (S_N, τ, ξ₀)` fijo pre-registrado, `m := N′−N` (N′ ≥ N), `p₁ = Aug^m∘Tighten_δ`, `p₂ = Tighten_δ∘Aug^m` |
| D3b | Tercera aridad `Δ_loop(c_r; K)` | Def. 6.1 define `Δ_loop(c_r; K) := Δ_loop(p₁(r), p₂(r); K)` para el tipo de lazo fijo |
| D3c | Límite incoherente en Prop. 6.2 | "as N → ∞ for fixed (N′, τ, δ)" → "as N → ∞ con N′ ≥ N en barrido pre-registrado y (τ, δ, K) fijos" |
| D4 | Tabla 1 vs Def. 9.18 | Def. 9.18 redefinida: `Δ̂ := |mid_fine − mid_full|` (separación de puntos medios) con nota de la relación con la distancia de Hausdorff y del límite común `|f|u₁u₂`; docstring del script corregido |
| Menor 1 | Sobrecargas de notación | Nuevo Remark 1.1 "Notation hygiene: declared overloads" (E, S, T, K, F, Φ, Ω, I, τ, Prob) |
| Menor 2 | Primitivos `𝒦`, `A_r`, `D_τ` | `𝒦` definida en Def. 2.5; `A_r` declarado como dato pre-registrado en Def. 2.18; `D_τ` declarado como región de restricción semántica del diente en Axioma 3.3 |
| Menor 2b | Paréntesis de conjuntos analíticos (Axioma 3.6(iii)) | Precisado: espacio Borel estándar ⇒ proyección analítica ⇒ universalmente medible; medibilidad registrada como dato en general |
| Menor 2c | `Autrig(N_r)` blando | Def. 2.22 especifica qué preserva la rigidez (datos del kernel, funtor E, grafo de transiciones) |
| Menor 3 | A4: pendiente sin barra de error | Remark 9.4: "−0.4944 ± 0.0019 (1σ, propagada de los errores estándar de replicación)" |
| Menor 4 | A5: cronología | Remark 9.4 abre declarando que parámetros y regla (Def. 9.19) se congelaron antes del muestreo y constan en el audit log; Remark 10.2 extiende el esquema de pre-registro a los casos C y D |
| Menor 5 | Bibliografía | `egc, geg, ceg, fbc` ahora citados (abstract, Remark 2.1, Defs. 2.9/2.10) |
| Menor 6 | Prop. 4.1 sobre-etiquetada | La cláusula de clase de cohomología quedó como condicional explícita ("no probada aquí") |
| Menor 7 | Teo. 4.3 "por declaración" | Prueba reformulada: el valor declarado en Def. 2.14 es consistente con el cálculo posetal |
| Menor 8 | R2 (CodeID) del artefacto | El script ahora calcula y registra `code_id` (SHA-256 de su propio código) en `audit_log.json` |
| Menor 9 | Atribuciones M1/M2 | M1: la tolerancia `ε_hol` cita Def. 9.12 junto con Def. 9.30; M2: la métrica `d_S` cita el Lema 9.1 |
| Menor 10 | Figura 1 | Ahora referenciada en el texto (§8) y el pie cita "Sections 2–3" |
| Menor 10b | Residuos menores | C6: "public-style" eliminado; lista de nodos de Def. 2.21 sin doble "E" |

**7.2 Re-verificación**

1. **Compilación:** `pdflatex` (TeX Live 2025), 3 pasadas, exit 0, `-halt-on-error` sin errores; sin referencias ni citas indefinidas; etiquetas estables en la pasada final (`fig:net` → Figura 1, `tab:p1star` → Tabla 1, `fig:p1star` → Figura 2).
2. **Referencias cruzadas:** verificador automático sobre el archivo corregido: 125 entornos numerados reconstruidos, **76 referencias internas únicas verificadas, 0 problemas** (la cifra de 146 de arriba corresponde a los tokens referenciales individuales auditados por el revisor de la ronda 1 en la versión original). Los números de los entornos editados son los esperados (Remark 1.1; Defs. 5.1–5.3; Prop. 6.1–6.5 con 6.3 `[Proved]`; Def. 9.18; Axiomas 3.3/3.6; Defs. 2.5/2.9/2.10/2.18/2.19/2.21/2.22).
3. **D1 re-verificado en S₃:** con la convención corregida, `h₁₂₃ = id ⟺ g₁₂∘g₂₃ = g₁₃` (caso 1: cociclo trivial ⇒ composición consistente ✓) y `h₁₂₃ ≠ id ⟺` composición inconsistente (caso 2 ✓). La afirmación "grupoide exactamente cuando los cociclos son triviales" es ahora verdadera, y la Prop. 6.3 es demostrable.
4. **Artefacto:** el script corregido se re-ejecutó; `table_results.csv` es **idéntico byte a byte** al previo (los valores de la Tabla 1 no cambiaron: mismo seed y parámetros), ambas decisiones pre-registradas siguen pasando (colapso `0.02628 ≤ 0.05`; holonomía `0.045254 − 2×0.000517 = 0.04422 ≥ 0.0225`), y `audit_log.json` ahora incluye `code_id` (SHA-256) y las decisiones.
5. **Consistencia numérica:** los valores de la Tabla 1 permanecen consistentes con el modelo generativo declarado (predicción analítica `E[Û] = 4.4917/√n_cfg` vs `4.377–4.606` observado; desviaciones típicas de replicación coincidentes a 3–4 cifras).
6. **Álgebra D2:** con la nueva Def. 5.1, las referencias de la prueba de la Prop. 5.1 ("trivial merge tree, trivial hitting times") son ahora computables y siguen valiendo en los modelos testigo (SCE-IM compartido ⇒ `Σzip` idéntico; `err ≡ 1` ⇒ `Σzip` cambia).

**7.3 Estado final.** Todos los defectos D1–D4 y las menores accionables quedaron corregidos; ninguna corrección alteró los valores numéricos del artefacto, las decisiones pre-registradas, los límites de la Prop. 9.2 ni la numeración cruzada del documento. El manuscrito corregido compila sin errores y pasa la auditoría de referencias con 0 problemas; el PDF compilado está disponible en `Epistemic_Closure_Net - Riveros.pdf`. **La certificación de solidez se mantiene, ahora sin correcciones pendientes obligatorias.**

---

### 13. Physical Observer Geometry, Protocol Holonomy, Order by Non-Closure, and Spectral Obstructions
(segunda ronda de revisión del 19 de agosto de 2026 — versión corregida · `Physical_Observer_Geometry__Protocol_Holonomy__Order_by_Non-Closure__and_Spectral_Obstructions - Riveros.tex`; compilación de verificación: `Physical_Observer_Geometry_LaTeX_v2.pdf`, 29 páginas, sin errores)

#### Veredicto
**ACEPTADO (CERTIFICACIÓN).** La versión corregida está **matemáticamente correcta y en estado publicable**, con todas las afirmaciones numeradas demostradas o etiquetadas honestamente como hipótesis/conjetura. La versión corregida se obtuvo aplicando, con máximo rigor matemático, las observaciones de la primera revisión (`reporte_revision_pares_Physical_Observer_Geometry_2026-08-19.md`), sin amputar ni reducir el contenido matemático (ningún teorema, definición o demostración fue eliminado; la antigua Sección 9 —copia verbatim de la Sección 7— fue sustituida por contenido nuevo que computa el vector de obstrucción en el modelo binario). Cada corrección fue verificada de forma independiente por un panel adversarial (re-verificación simbólica con SymPy y auditorías cláusula por cláusula), incluyendo una ronda final que detectó y corrigió dos inconsistencias residuales.

#### Correcciones aplicadas (cierre de fallas, una a una)

| Falla (1ª revisión) | Corrección aplicada | Verificación |
|---|---|---|
| **F1** Holonomía abstracta ≡ 0 (Def. 5.9 = distancia al punto base, anulada por el Lema 5.7) | Def. 5.9 redefinida como defecto global de transporte: `Hol_abs(ℓ;π) := sup{ d_π(T_ℓu, u) : u ∈ S_π, ‖u‖_π ≤ 1 }`, con caracterización demostrada: `Hol_abs > 0 ⟺ G_ℓ ≠ id` sobre Q_π, y cota `Hol_abs ≤ L_ℓ + 1 < ∞`. Consecuencias: Def. 10.7 (holonomía UV/IR no trivial) satisfacible; "persistence" definida formalmente; el Teo. 5.19 y la Def. 5.18 ahora son no-vacías | ✔ verificado: cota, caracterización (ambas direcciones), finitud; la Prop. 5.10 (independencia de camino ⟹ holonomía 0) sigue siendo correcta con la nueva definición |
| **F2** El modelo binario no instancia el marco (γ_u, δ_v violan Def. 5.4.5; T_real ≠ T_γ; sin espacios S–I–E) | (a) Se construye el modelo sistema–instrumento–ambiente (X_S × X_I × X_E = {0,1}³, ley conjunta, τ_π constante → ν_π = δ_{(α,β,p)}); (b) la familia de consultas es la clausura por precomposición `Q := {q∘w : q ∈ {q0,q1,q*}, w ∈ Γ}`, con `G_{γw}(q) := q∘γw`: compatibilidad exacta por construcción y `L_{γw} ≤ 1`; (c) `T_real(Φ_π) = Φ_{γπ} = T_γ(Φ_π)` por el Lema 5.7 — consistencia total | ✔ verificado: clausura, compatibilidad, cota L ≤ 1, consistencia T_real ≡ T_γ; el modelo además **exhibe holonomía no trivial**: `Hol_abs(γ_α∘δ_v∘γ_{−α}; π) = 2` para estados interiores |
| **C.1** Teorema 5.17 falso tal como estaba ("< r"; paso `R_ε ≥ r ⟹ E_π(r) ≤ ε` inválido) | Conclusión corregida a `R_ε(π) ≤ r`, con hipótesis de compatibilidad explícita entre d_sem y el residuo normalizado, demostración por inclusión de bolas (sin monotonía de E_π), y ejemplo de agudeza (2 estados, R_ε = r = 1): la cota `≤` es óptima | ✔ verificado paso a paso; contraejemplo de agudeza verificado cláusula por cláusula; Teos. 8.9/8.10 no afectados |
| **C.2** Prop. 6.3 falsa (monotonía de E_π; E_π(0) = 0) | Afirmaciones condicionadas correctamente: (i) E_π(0) = 0 si d_prot(π,π′) = 0 ⟹ π′ = π; (ii) monotonía bajo marcos constantes en [0, r*]; (iii) la estimación local E_π(r) ≤ ω_π(r) se conserva (correcta) | ✔ verificado; el contraejemplo de marcos encogidos queda correctamente excluido por la hipótesis (ii) |
| **D.1** Secciones 7 y 9 duplicadas verbatim | La Sección 9 (duplicado) se sustituye por contenido nuevo: "Non-closure in the binary model" (Lemas 9.1–9.2, Teo. 9.3, Cor. 9.4, Teo. 9.5) que computa ∆_r en el modelo binario | ✔ verificado: ninguna pérdida de contenido único; la nueva sección es sustantiva |
| **D.2** Objetos indefinidos (O, d_prot, cinco funcionales, C^{g.i.}_IR, "persistence", familias de Prot_UV/IR) | Convenciones 5–6 (d_prot con bolas cerradas; O); discrepancia d_a y d^base_a en Def. 2.6; los cinco funcionales de la Def. 7.1 definidos concretamente (κ_r vía certificados, Hol^atlas vía la obstrucción del Teo. 2.12, Hol^prot vía Def. 5.9, g_r vía Res_obs, c_r vía ε_flat), conectados entre sí y con la Sección 10; C^{g.i.}_IR definida; "persistence" definida; las cinco familias de morfismos de Prot_UV/IR especificadas; orden de escala ⪯ en Res (Def. 5.2) | ✔ verificado |
| **D.3** Dil⁺ nunca usada pese al abstract | Párrafo tras la Def. 6.5: la dilatación es la constante local de Lipschitz óptima de E_π; `Dil⁺ < L ⟹ E_π(r) ≤ Lr en [0,r₀] ⟹ R_ε ≥ min(r₀, ε/L)`; con logro local del límite (p. ej., modelo binario, donde E_π(r) es lineal cerca de 0) se obtiene `R_ε ≥ min(r₁, ε/Dil⁺)` | ✔ verificado (el paso al límite L ↓ Dil⁺ requiere el logro local, ahora declarado) |
| **D.4** Teorema 3.4 tautológico | Def. 3.3 = inyectividad del perfil; Teo. 3.4 = identificación del observador por el perfil, con la instancia no trivial Teo. 8.1 | ✔ verificado |
| **D.5** R_ε definido dos veces sin reconciliar | Párrafo tras la Def. 6.4: equivalencia exacta de las Defs. 4.3 y 6.4 bajo marcos maximales (Q_{π,r} = Q_π ∩ Q_π′ en la bola); el modelo binario usa la Def. 4.3 en unidades d_sem (normas de consulta = 1; factor 2 entre convenciones) | ✔ verificado (ambas direcciones con la hipótesis correcta) |
| **D.6** Inconsistencia bolas abiertas/cerradas | Convención 5: bolas de protocolo cerradas `B^prot_r(π) := {π′ : d_prot ≤ r}`, usadas consistentemente en Defs. 5.11–6.4, Teo. 5.17, Sección 8 | ✔ verificado |
| **D.7** "Hypothesis 6.10" (numeración) | Referencia corregida a Hipótesis 6.11 | ✔ verificado |
| **D.8** Prop. 10.2 (hipótesis no declaradas); prueba del Teo. 10.11 no usa los supuestos 1–2 | Hipótesis explícitas (H autoadjunto ≥ 0, HΩ = 0, vacío único, E({0}) = |Ω⟩⟨Ω|, µ_O({0}) = 0); la prueba del Teo. 10.11 usa ahora los cuatro supuestos | ✔ verificado |
| **D.9** Signo ∂θ/∂β | Corregido a −p | ✔ verificado |

**Correcciones adicionales de la segunda ronda (auditoría adversarial de la propia corrección):**

- **Lema 9.1 / Teo. 9.3(ii):** la fórmula original del cálculo atlas (1−β)/2 usaba una reducción inválida sobre la órbita completa de consultas. Se corrige usando la discrepancia de consultas base `d^base_a` (Def. 2.6 ampliada): `Hol^atlas_r(π) = (1/2) max( max(α, 1−η−β−α), max(θ(π), 1−β−θ(π)) ) ≥ η/4`. Valores del Teo. 9.5 corregidos a 0.3 y 0.15 (η = 0.1); monotonía estricta en β verificada (dirección del preorden corregida).
- **Teo. 6.13:** cuantificación de δ completada (`δ < min(δ₀, R_ε, r*−R_ε)`).
- **Teo. 9.3(iii):** condición interior α+β < 1−η para `Hol^prot = 2` (degeneración de frontera documentada).
- **Justificación de r_word:** paso (t/2)(α+t/2) ≤ t corregido (vía la restricción D_η, no α < 1 y t ≤ 4).
- **Referencias:** [1]–[8] ahora citadas en el texto.
- **Huérfanos:** Def. 5.13 (P_π(r)) referenciada en el Remark 5.16; "r_π ⪰ r" con el orden de escala de Res.

#### Verificación final
- **Compilación:** sin errores ni advertencias relevantes (29 páginas).
- **Verificaciones simbólicas (SymPy):** conmutador c_{u,v} = (α,β,p+uv); residuo (1−α−β)|uv|; gradiente y cota de Lipschitz 2; inyectividad de Φ (Teo. 8.1); clausura por precomposición; valores exactos de la Sección 9 (0.3 y 0.15; identidad θ + (1−β−θ) = 1−β; cotas η/4, ηr²/8, 2r); linealidad de E_π(r) en el modelo binario.
- **Auditoría adversarial final:** todas las piezas verificadas CORRECTAS; dos inconsistencias residuales detectadas (fórmula de la Def. 7.1(2) y display del Teo. 9.3) fueron corregidas y re-verificadas.

#### Estado resultante
El documento está ahora **matemáticamente correcto y en estado publicable**, con todas las afirmaciones numeradas demostradas o etiquetadas honestamente como hipótesis/conjetura: la holonomía abstracta es una cantidad genuinamente no trivial (caracterizada exactamente), y el modelo binario la exhibe con valor exacto 2; el modelo binario es una instancia rigurosa del marco (S–I–E construido; compatibilidad exacta; T_real = T_γ); las cotas de acuerdo (ventana bilateral), los estimadores de banco finito y la no-compresibilidad son correctos; el vector de obstrucción está definido concretamente y es no trivial en el modelo binario (no trivialización global en toda escala; cociente con ≥ 2 clases; orden estricto). La reducción de Yang–Mills sigue siendo **condicional** (Puentes A y B como conjeturas explícitas) — correcto y honesto; no afirma resolver el problema del gap de masa.

**Residual (por diseño, no errores):** los Puentes A y B permanecen conjeturas; la reducción YM es condicional.

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
| COVERTRACE-SAT (Documento Unificado, Vol. I) | 0 | 0 | 5 obligatorias (citación) + menores de presentación | Sólido — certificado, condicionado a correcciones obligatorias de citación |
| Conexiones SAT–COVERTRACE (nota unificadora) | 0 | 0 | Todas las correcciones de ambas rondas aplicadas (C1–C6, M1–M7) | Sólido — certificado, aceptado en segunda ronda |
| Epistemic Closure Nets | 1 (D1 convención de composición, corregido) | 2 (D2 `MT_I`/`τ^o`, D3 `Δ_loop`, corregidos) | D4 (Tabla 1 vs Def. 9.18) + 10 menores, todas corregidas | Sólido — certificado, aceptado con revisiones obligatorias; sin pendientes tras la Adenda §7 |
| Physical Observer Geometry | 5 (F1, F2, C.1, C.2, D.9 de la primera versión, corregidos) | 2 (D.2, D.8, corregidos) | 7 (D.1, D.3–D.7) + 2 inconsistencias residuales de la segunda ronda, todas corregidas | Sólido — certificado, aceptado en segunda ronda |

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

### 10. COVERTRACE-SAT as Disjoint-Subcube Knowledge Compilation (Unified Document, Vol. I)
(Part I in English, January 2026, and Part II in Spanish, corrected version · review dated August 14, 2026 · `COVERTRACE_SAT_Disjoint_Subcube_Unificado.tex`, 1061 lines)

#### Verdict
**CERTIFIED AS MATHEMATICALLY SOUND — no fatal flaw found.** All central claims of both parts were verified by formal reconstruction of the proofs from first principles, exhaustive independent computational verification (Python 3.13), and adversarial audits aimed at refuting every bound, inequality and invariant, with no counterexamples. The defects found are exclusively of citation, notation and presentation and **do not invalidate any mathematical claim**. The certification is issued on condition that the citations (findings 1–5) be corrected before publication: bibliographic, not mathematical, defects.

#### Inventory of main results
**Part I (English):**
1. **COVERTRACE** (CubeDiff/AddCube): compilation of ¬F into disjoint subcubes with exact #SAT counting and witness extraction (Thm. 4.1, Prop. 4.2); `O((T+m)·c(n))` bound (Prop. 5.1).
2. **Parity lower bound:** `χ(O_n) = 2^{n−1}` (Lemma 6.1 / Thm. 6.2).
3. **DSOP compilation and conditional collapse:** polynomial compiler with polynomial encoding ⇒ `PH = P` (Thm. 7.4); polynomial-verifiable UNSAT certificates ⇒ `NP = coNP` (§7.5).
4. **Affine extension** (cosets of ker A) with exponential parity compression (Section 8).
5. **Volumetric Lemma 9.2** and **influence bound** (Cor. 9.5) for χ; Problem 9.6 declared open; GCT viewpoint (Section 10).

**Part II (Spanish):**
6. **Containment-invariant lemma** of COVERTRACE.
7. **Inequality `S_part(F) ≤ S_tr(F)`** for every unsatisfiable F (Thm. 2.1) and **explicit verified counterexample `S_part = 6 < 7 = S_tr`** (Prop. 2.2); honest degradation of PHP to an open problem with bound 4 (Cor. 2.6).
8. **Fourier–Walsh spectral bound:** `χ(S) ≥ 2^d · max_{|α|=d} |f̂(α)|` (Section 3).
9. **Polyhedral certificate and exact encoding** `φ_n`/`κ_n` (Section 4).
10. **Delimitation of Problem 9.6** (Section 5) and the August 14 correction note verified against the body.

#### Verified correct
- **Core algorithms:** the three CubeDiff cases are exhaustive and mutually exclusive; termination by strict decrease. **Exhaustive n=4 (6561 pairs) and n=5 (59049 pairs): 0 failures.** Lemma 3.2 verified under its hypotheses (the unconditional bound fails and the lemma excludes it). COVERTRACE: 500 CNFs n=4 and 200 n=5 verified after every clause by brute force: 0 failures. Witnesses: 259/259 valid. ✓
- **Parity bound:** `χ(O_n) = 2, 4, 8` for n=2,3,4 by exact DP; tight. ✓
- **Conditional collapse:** every implication (Valiant, Toda) verified; the conditional character is declared; §7.5 sound and complete with `O(K²n + Kmn)` verifiability. ✓
- **Lemma 9.2:** all 255 non-empty subsets of {0,1}³, 0 violations (87 tight). **Cor. 9.5:** 254 exhaustive n=3 + 200 sampled n=4: 0 violations. ✓
- **Inequality `S_part ≤ S_tr`:** 34,071 unsatisfiable CNFs n=3 (≤5 clauses) + 254 n=4: 0 violations. **Prop. 2.2 (6<7):** confirmed by three independent implementations, exact-cover DP over the 2^16 subsets, tree-resolution fixed point `D(⊥) = 7` (BKPS equivalence on 61 instances, 0 discrepancies), and **exhaustive enumeration of all decision trees with ≤6 leaves over 4 variables (26,657 proper + 46,949 with re-queries: 0 refuting)**. ✓
- **Spectral bound:** 256×4 inequalities n=3, 0 failures, tight; parity and majority examples verified numerically. ✓
- **Polyhedral certificate and encoding:** point-by-point verification (n=4, 16 points); fractional counterexample verified; integrality restriction necessary and declared in the text. ✓
- **Adversarial audits:** no refutation hypothesis (algebraic error, non-sequitur conclusion, counterexamples to bounds or invariants) survived its own scrutiny. ✓

#### Findings
| # | Type | Description |
|---|------|-------------|
| 1 | **Mandatory (citation)** | `kmr15`: the printed authors (Kothari, Meka, Raghavendra) do not correspond to the cited article; the real one is Kothari–Racicot-Desloges–Santha, *Separating Decision Tree Complexity from Subcube Partition Complexity*, APPROX/RANDOM 2015, LIPIcs 40:915–930. |
| 2 | **Mandatory (citation)** | `hegyvari24` does not exist as printed (wrong journal and title); the real one is N. Hegyvári, *The complexity of subcube partition relates to the additive structure of the support*, Information and Computation 299:105170 (2024). |
| 3 | **Mandatory (citation)** | `koriche13`: miscited title (real: *Knowledge Compilation for Model Counting: Affine Decision Trees*, IJCAI 2013); also never invoked in the text. |
| 4 | **Mandatory (citation)** | Missing Valiant entry for the #P-completeness of #SAT, invoked in the proof of Thm. 7.4. |
| 5 | **Mandatory (citation)** | No `\cite` anywhere in the document; several entries never mentioned in the text (ms01, ms08, bi25, dip19, lucas14, bbbv97, koriche13, hegyvari24, Ben-Sasson–Wigderson 2001). |
| 6 | Minor (presentation) | «Theorems 4.1–4.3» includes Observation 4.2 in the range; the abstract says it generalizes Prop. 9.4 when it corresponds to Cor. 9.5; Lemma 3.2 hypotheses elided in the abstract; lax wording of Remark 4.3 in Part I; schematic charging in Prop. 5.1 (make the ≤ T+m count explicit); Urquhart 1987 annotation mentions PHP (belongs to Haken 1985/folklore); notation x_0..x_3 vs x_1..x_n; «bi25» index without article number; volume-sum cost O(K) at word level (O(Kn) at bit level, still polynomial). |
| 7 | Originality remark | `S_part ≤ S_tr` is a direct consequence of the classical tree-resolution ↔ decision-tree equivalence (Beame–Karp–Pitassi–Saks 2002, cited) and `χ(O_n) = 2^{n−1}` is folklore; the genuine novelty lies in the explicit verified counterexample (6<7), the tight spectral bounds, and the honest delimitation of Problem 9.6. |

---

### 11. Connections between the SAT Equation Theorem and COVERTRACE-SAT (Unifying Note)
(11 pages, 8 references · note dated August 15, 2026 · second review round, corrected version · `Conexiones_SAT_Equation_COVERTRACE_ES.tex`)

#### Verdict
**ACCEPTED (CERTIFICATION).** The corrected version passes peer review. All mandatory (C1–C4) and recommended (C5–C6) corrections from the previous report were applied, and the fatal defect (the false flipping lemma) was eliminated: the lemma now states the correct flipping identity (XOR), with a valid proof and a paragraph explicitly documenting the difference from arithmetic addition. The independent computational verification was repeated in full: **all claims of the corrected document verify exactly** (0 failures in every suite), and the document compiles without errors or unresolved references.

#### Inventory of main results
1. **Fundamental identity:** `popcnt(S(F)) = |U(F)| = Σ_{u∈U} vol(u)` — the dense integer bitmask of `2ⁿ` bits (SAT Equation) and the disjoint family of subcubes (DSOP of ¬F, COVERTRACE) encode the same object: the forbidden region `U(F) ⊆ Ω_n`.
2. **Carry–disjunction duality:** the carries of the arithmetic sum are exactly the overlaps that COVERTRACE's disjointness invariant removes; the bitwise OR is their idempotization.
3. **Flipping lemma (XOR):** `t(k⊕2^j) = 1 − t(k)` for all k,j, proved via the parity of `popcnt`; the text explicitly warns that the addition version `t(k+2^j) = 1 − t(k)` is false (30.9 % counterexamples).
4. **Parity as the Thue–Morse number:** the SAT Equation integer of parity is the Thue–Morse number: its binary expansion is the Thue–Morse word of length `2ⁿ`; `popcnt(S_n) = 2^(n−1) = χ_⊔(O_n)`, also matching the Fourier–Walsh spectral bound of Part II.
5. **Closed form:** `S_C = 2^B · Π(1 + 2^{2^(n−i)})`; duality (c): OR = AddCube bit by bit; base-b multiplicities.
6. **Corollary of the dense representation:** the largest subcube in `O_n` has size 1 → optimal singleton coverage, `χ_⊔(O_n) = 2^(n−1)`.
7. **Dense–sparse comparison** (counting, membership, witness extraction, updates) and reformulation of the corpus's open problems in bitmask language.

#### Verified correct (exact arithmetic, independent re-verification)
- **XOR flipping lemma** `t(k⊕2^j) = 1−t(k)`, n=1..10: 0 failures; contrast with the addition identity `t(k+2^j) = 1−t(k)`, k<2^10: 2845/9217 failures = 30.9 % (matches the text). ✓
- **Corollary:** largest subcube in `O_n`, n=1..4: size 1 (optimal singleton coverage). ✓
- **Closed form** `S_C = 2^B·Π(1+2^{2^(n−i)})`: unit clause 15, balanced 12, empty 255, mixed 20560 — all equal to the direct OR. ✓
- **Thue–Morse:** recursion = product formula, n=0..8: `S_1=2, S_2=6, S_3=150, S_4=27030, S_5=2523490710, S_6=7608434000728254870`; `popcnt(S_n)=2^(n−1)`, n=1..8: 1,2,4,8,16,32,64,128; morphism `W_(n+1)=W_n·W̄_n` and `μ⁴(0)=W_4=0110100110010110`. ✓
- **Walsh factorization:** all `α⊆[n]`, n=1..7: 254/254 cases. ✓
- **Spectral bound:** `F̂f([n])=−½`, `2^n·|F̂|=2^(n−1)`, n=1..9: −1/2; 1,2,4,…,256. ✓
- **Fundamental identity (CubeDiff/AddCube):** 200 CNFs, 0 failures (disjointness, bit-by-bit coverage, popcnt=Σvol). **Duality (c):** OR = AddCube bit by bit, 200 CNFs, 0 failures. **Base-b multiplicities:** 50 CNFs, 0 failures. ✓
- **Part II counterexample:** UNSAT, S(F)=65535, certificate of 6 cubes (vol. 16), tree of 7 leaves; `S_part = 6 < 7 = S_tr`. **Conventions:** `T(C)+B(C)=2^n−1`. ✓

#### Findings
All first-round corrections were applied and verified in the corrected version:

| # | Type | Description | Status |
|---|------|-------------|--------|
| C1–C2 | Mandatory (mathematics) | Flipping lemma: `+` → `⊕`, proof corrected («flipping bit j changes popcnt(k) by ±1») | Applied (lines 224–234) |
| — | Clarification | Paragraph documenting the counterexample 3+2=5 and the exact condition of the addition identity | Added (line 236) |
| C3 | Mandatory | Corollary justification repaired (corrected lemma + alternative derivation: spectral bound + trivial singleton coverage) | Applied (line 260) |
| C4/C4b | Mandatory | «All identities…» qualified to the actually verified list; 4 new verification items added | Applied (lines 399–417) |
| C5 | Mandatory (citation) | `\cite` for the 8 bibliographic entries; `kmr15` authors corrected (Kothari–Racicot-Desloges–Santha) | Applied |
| C6 | Mandatory | Prop. Section 8.1: O(mn) clarified (pattern form; materializing costs 2ⁿ bits) | Applied (line 359) |
| M1–M7 | Minor | Borrowed notation defined; «fragmentation is null» → «linear in the number of clauses»; MSB/LSB convention clarified; non-tautological hypothesis replaced; carry scope qualified; word probes; base-b exponent | Applied |

**Document status:** compiles with `pdflatex` (3 passes) without errors, without unresolved-reference warnings or undefined citations; 11 pages; all 8 bibliographic entries cited in the body. **No regressions:** the verifications of untouched results (Thue–Morse, Walsh, spectral, fundamental identity, base b, Part II counterexample) were repeated and passed in full.

---

### 12. Epistemic Closure Nets: Curvature, Holonomy, Certification, and Meta-Closure in an Expansive Network Formalism
(manuscript dated February 2026 · review dated August 17, 2026 · `Epistemic_Closure_Net - Riveros.tex`, 1898 lines in the reviewed version, 1965 after applying the Addendum §7, plus the `artifact/` package)

#### Verdict

**SOUNDNESS CERTIFICATION — no fatal flaw.** All essential claims (contributions C1–C6) and all results tagged `[Proved]` are correctly supported by the definitions, axioms, proofs, data, and artifacts presented. The manuscript was not to be published in its original form without four mandatory corrections (D1–D4), but none of them was shown to invalidate or reverse any conclusion of the document: all are specification/labeling gaps repairable in a single revision pass, and the central claims survive any reasonable completion of those definitions. The verdict survived a dedicated adversarial audit: a reviewer holding the explicit hypothesis that the manuscript contained a fatal flaw tried to escalate each candidate defect to a fatal flaw and, in every case, showed that the corresponding essential claim stands. **Post-correction status:** the mandatory corrections D1–D4 and all actionable minor defects were applied to the manuscript and the artifact, and the corrected document was re-verified (Addendum §7): it compiles without errors, internal references audit with 0 problems, and the artifact's numerical values are unchanged. The soundness certification stands, now **with no mandatory corrections pending**.

#### Methodology

Two-round multi-agent review with independent computational verification: (Round 1) six independent reviewers on disjoint dimensions — internal consistency and cross-reference numbering; line-by-line verification of every `[Proved]` proof; statistical validity and numerical verification of the experimental node P1★; adversarial hunt for fatal flaws; completeness of definitions, notation, metatheory, and compliance with the auditability rules A1–A5; claims-to-deliverables mapping, bibliographic grounding, and artifact reproducibility. (Round 2) one adversarial auditor attempting to escalate every candidate defect to a fatal flaw. Independent numerical verification: analytical reconstruction of the P1★ harness from Definitions 9.16–9.18 and Remark 9.4, with execution of the reviewer's own code (Python 3.13/numpy) in addition to the delivered artifact.

#### Positive verification

- **Axiomatic consistency:** Theorem 4.2 (`[Proved]`) exhibits an explicit model of Axioms 3.1–3.9, verified axiom by axiom (trivial observable factoring through `X/Sim`; vacuous soundness with `Cert ≡ 0`; empty zipper; lower-semicontinuous `err ≡ 0`; `μ(Ω) = 1 < ∞`; compact `S_∞ = {S_0}`, `ω ≡ 0`, nested banks, `ε_N = 0`-net; constant functor `E`; one-chart atlas with trivial cocycles; presentation-level vacuity for the silence meta-axiom). The axiom system is jointly satisfiable in ZFC.
- **`[Proved]` results — all correct:** Prop. 2.1; Lemmas 4.1–4.2; Thms. 4.1–4.5 (transfer of a finite bank from a modulus of continuity, kernel/SCE-IM non-contradiction, index-trivial vs program-level holonomy, non-trivial cocycle obstructing global trivialization, soundness-only certification); Prop. 4.1 (gauge invariance), Prop. 4.2; Prop. 5.1 (independence of `Σzip` and `(Hol_atlas, Hol_prot)` — correct in substance for any completion of the undefined components, see D2); Thms. 9.1–9.2 (Hoeffding bounds) and Prop. 9.1 (sample size). The `[Model]`-labeled Lemma 9.1, Prop. 9.2, and the scheme of Prop. 9.3 were also verified.
- **Statistical verification:** Hoeffding bounds, the `ε_T` formula and decision rule, the Gretton MMD U-statistic, and Wasserstein-1 via Kantorovich–Rubinstein duality — all correct; the ESS substitution for MCMC is honestly labeled `[Model]` with an explicit anti-conservativity warning under slow mixing.
- **Node P1★ (contribution C6) — independent numerical verification:** the fine-protocol intercept algebra verified exactly (bias `−0.0449999921 = −f·u₁u₂`; constant `|f|·u₁u₂ = 0.045000`); linear functional norms recomputed from the design matrix (`2.079667` / `0.721372`, identical to `audit_log.json`); Table 1 quantitatively consistent with the declared generative model (analytical prediction `E[Û] = 4.4917/√n_cfg` vs observed `4.377–4.606`); a fresh execution reproduces `table_results.csv` byte-for-byte; both pre-registered decisions pass (collapse `0.02628 ≤ 0.05` ✓; persistent holonomy `0.04422 ≥ 0.0225` ✓); the GW150914 skeleton script enforces the A5 gate (refuses to run without a frozen pre-registration file).
- **Cross-references:** 146 internal references audited, 0 broken, 0 misnumbered targets; all critical references resolve correctly (two minor attribution imprecisions M1/M2, corrected).
- **Contributions C1–C6 delivered** (C4 with a note: no direct estimator of the modulus `ω`, only of `d_eff` and of the composite slope `α/d_eff`). Rules A1–A5 complied with in substance.

#### Demonstrated defects — all review-level, mandatory before publication, all corrected in Addendum §7

- **D1 (real non-fatal mathematical error):** the composition convention in Def. 2.19 vs the cocycle of Def. 2.20. As written, "the transition family acquires a groupoid structure (with composition `g_ik := g_jk ∘ g_ij`) exactly when all triple cocycles are trivial" was false: with that convention the consistency condition is `g_jk ∘ g_ij ∘ g_ki = id`, which in non-abelian groups is not equivalent to the declared cocycle. Two counterexamples verified computationally in `S₃` (cocycle trivial but no groupoid; fully consistent family with non-trivial "holonomy"). Collateral: Prop. 6.3 (`[Model]`) false as written. Scope: no `[Proved]` result depended on the defective sentence; Theorem 4.4 (the sole pillar of C3) is correct, and the descent computation telescopes under any convention. **Corrected:** composition redefined as `g_ik := g_ij ∘ g_jk` with declared direction; Prop. 6.3 re-labeled `[Proved]` with a proof.
- **D2 (definition gap, non-invalidating):** `MT_I` and `τ^o` undefined in the zipper signature `Σzip(E,o) := (κ(o), MT_I(o), τ^o)` (Def. 5.1). The independence proof of Prop. 5.1 uses only that `Σzip` is a function of the SCE-IM component and that the witness models share the same SCE-IM component, so the non-implication holds **for any completion** of `MT_I`/`τ^o`. **Corrected:** Def. 5.1 rewritten (sublevels `S_ε(o) := {σ : err(σ,o) ≤ ε}`, merge tree of the filtration over `I`, arrival time `τ^o(σ) := inf{ε ∈ I : σ ∈ S_ε(o)}` with `inf ∅ := +∞`).
- **D3 (underspecified abbreviation):** the four-argument form `Δ_loop(N,N′,τ,δ;K)` did not determine the initial state `c₀` nor the number `m` of augmentation steps required by Def. 9.21. Non-fatal: Prop. 5.1 does not use this form; the remaining uses are well-posed with the natural completion `m := N′−N`, `c₀ := (S_N, τ, ξ₀)`. **Corrected:** Def. 5.3 completed; the third arity `Δ_loop(c_r; K)` defined in Def. 6.1; the incoherent limit in Prop. 6.2 fixed.
- **D4 (reporting error, not a conclusion error):** Table 1 computed only `|mid_fine − mid_full|` while Def. 9.18 defined the Hausdorff distance of the uncertainty intervals (equal to the midpoint difference only when the widths coincide; here `‖φ_fine‖ = 2.0797`, `‖φ_full‖ = 0.7214`). Non-fatal: the limits of Prop. 9.2 are identical under both estimators, the C6 diagnostic regime holds (numerically stronger), and **both pre-registered decisions still pass** under the literal estimator. **Corrected:** Def. 9.18 redefined as `Δ̂ := |mid_fine − mid_full|` (midpoint separation) with a note on the relation to the Hausdorff distance and the common limit `|f|u₁u₂`; the script docstring corrected.

#### Minor issues (recommended, non-blocking; all actionable ones corrected)

Notational overloads (E, S, T, K, F, Φ, Ω, I, τ, Prob — now declared in a new Remark 1.1); undefined primitives `𝒦`, `A_r`, `D_τ` and the soft `Autrig(N_r)` (now defined/declared); the A4 error-bar gap (the slope is now reported as `−0.4944 ± 0.0019`); the A5 pre-registration chronology (now declared frozen in `audit_log.json`); 4 uncited self-preprint bibliography entries (now cited); evidence labels (Prop. 6.3 re-labeled `[Proved]`; the cohomology-class clause of Prop. 4.1 made an explicit conditional); Thm. 4.3 (index part) over-labeled (proof reformulated); the artifact contract R2 (the script now records `code_id`, the SHA-256 of its own code, in `audit_log.json`); the minor reference attributions M1/M2 (corrected); Figure 1 never referenced (now referenced in §8, and the caption cites "Sections 2–3").

#### Conclusion

The manuscript fulfills its own declared scope ("an auditable specification layer, not a completeness theorem of scientific knowledge"): claims are typed by evidence, the `[Proved]` results are correct (verified one by one, with the consistency model checked axiom by axiom), the `[Model]`/`[Conjecture]` results are isolated as such with pre-registered falsification patterns, the statistical estimators are standard and well applied, and the artifact node P1★ is genuine and reproducible: Table 1 is quantitatively consistent with the declared generative model and reproduces to the digit with the delivered script. The four demonstrated defects were real and mandatory to fix, but in each case it was shown with counterexamples, recalculations, and executions that **no essential claim (C1–C6) or `[Proved]` result was invalidated**: the theorems, the witness models, the pre-registered decisions, and the C6 diagnostic regime survive the corrections and any reasonable completion. **Final verdict: ACCEPT WITH MANDATORY REVISIONS (soundness certification; no fatal flaw).** Post-correction status (Addendum §7): **certification maintained, with no mandatory corrections pending.**

#### Addendum §7 — applied corrections and re-verification (August 17, 2026)

All mandatory corrections D1–D4 and the actionable minor defects were applied to the manuscript (`Epistemic_Closure_Net - Riveros.tex`) and the artifact (`artifact/P1star_cut_state/p1star_cut_state.py`), and the corrected document was re-verified: (1) `pdflatex` (TeX Live 2025), 3 passes, exit 0, no errors, no undefined references or citations; (2) automatic cross-reference checker: 125 numbered environments rebuilt, **76 unique internal references verified, 0 problems**; (3) D1 re-verified in `S₃` (with the corrected convention, "groupoid exactly when the cocycles are trivial" is now true and Prop. 6.3 is provable); (4) the corrected script was re-executed: `table_results.csv` is **byte-identical** to the previous one, both pre-registered decisions still pass, and `audit_log.json` now includes `code_id` (SHA-256) and the decisions; (5) the Table 1 values remain consistent with the declared generative model; (6) with the new Def. 5.1, the references of the Prop. 5.1 proof ("trivial merge tree, trivial hitting times") are now computable and still hold in the witness models. No correction altered the artifact's numerical values, the pre-registered decisions, the limits of Prop. 9.2, or the document's cross-numbering. The corrected manuscript compiles without errors and passes the reference audit with 0 problems; the compiled PDF is available in `Epistemic_Closure_Net - Riveros.pdf`. **The soundness certification stands, now with no mandatory corrections pending.**

---

### 13. Physical Observer Geometry, Protocol Holonomy, Order by Non-Closure, and Spectral Obstructions
(second review round dated August 19, 2026 — corrected version · `Physical_Observer_Geometry__Protocol_Holonomy__Order_by_Non-Closure__and_Spectral_Obstructions - Riveros.tex`; verification compilation: `Physical_Observer_Geometry_LaTeX_v2.pdf`, 29 pages, no errors)

#### Verdict
**ACCEPTED (CERTIFICATION).** The corrected version is **mathematically correct and in publishable state**, with all numbered claims proved or honestly labeled as hypotheses/conjectures. The corrected version was obtained by applying, with maximum mathematical rigor, the observations of the first review (`reporte_revision_pares_Physical_Observer_Geometry_2026-08-19.md`), without amputating or reducing the mathematical content (no theorem, definition, or proof was removed; the old Section 9 — a verbatim copy of Section 7 — was replaced by new content computing the obstruction vector in the binary model). Each correction was independently verified by an adversarial panel (symbolic re-verification with SymPy and clause-by-clause audits), including a final round that detected and corrected two residual inconsistencies.

#### Corrections applied (closure of failures, one by one)

| Failure (1st review) | Correction applied | Verification |
|---|---|---|
| **F1** Abstract holonomy ≡ 0 (Def. 5.9 = distance to the base point, annihilated by Lemma 5.7) | Def. 5.9 redefined as a global transport defect: `Hol_abs(ℓ;π) := sup{ d_π(T_ℓu, u) : u ∈ S_π, ‖u‖_π ≤ 1 }`, with proved characterization: `Hol_abs > 0 ⟺ G_ℓ ≠ id` on Q_π, and bound `Hol_abs ≤ L_ℓ + 1 < ∞`. Consequences: Def. 10.7 (non-trivial UV/IR holonomy) satisfiable; "persistence" formally defined; Thm. 5.19 and Def. 5.18 now non-vacuous | ✔ verified: bound, characterization (both directions), finiteness; Prop. 5.10 (path independence ⟹ holonomy 0) remains correct under the new definition |
| **F2** The binary model does not instantiate the framework (γ_u, δ_v violate Def. 5.4.5; T_real ≠ T_γ; no S–I–E spaces) | (a) The system–instrument–environment model is built (X_S × X_I × X_E = {0,1}³, joint law, τ_π constant → ν_π = δ_{(α,β,p)}); (b) the query family is the precomposition closure `Q := {q∘w : q ∈ {q0,q1,q*}, w ∈ Γ}`, with `G_{γw}(q) := q∘γw`: exact compatibility by construction and `L_{γw} ≤ 1`; (c) `T_real(Φ_π) = Φ_{γπ} = T_γ(Φ_π)` by Lemma 5.7 — total consistency | ✔ verified: closure, compatibility, bound L ≤ 1, consistency T_real ≡ T_γ; the model also **exhibits non-trivial holonomy**: `Hol_abs(γ_α∘δ_v∘γ_{−α}; π) = 2` for interior states |
| **C.1** Theorem 5.17 false as stated ("< r"; the step `R_ε ≥ r ⟹ E_π(r) ≤ ε` invalid) | Conclusion corrected to `R_ε(π) ≤ r`, with an explicit compatibility hypothesis between d_sem and the normalized residual, proof by ball inclusion (without monotonicity of E_π), and a sharpness example (2 states, R_ε = r = 1): the `≤` bound is optimal | ✔ verified step by step; sharpness example verified clause by clause; Thms. 8.9/8.10 unaffected |
| **C.2** Prop. 6.3 false (monotonicity of E_π; E_π(0) = 0) | Claims correctly conditioned: (i) E_π(0) = 0 if d_prot(π,π′) = 0 ⟹ π′ = π; (ii) monotonicity under constant frames on [0, r*]; (iii) the local estimate E_π(r) ≤ ω_π(r) is kept (correct) | ✔ verified; the shrinking-frames counterexample is correctly excluded by hypothesis (ii) |
| **D.1** Sections 7 and 9 duplicated verbatim | Section 9 (the duplicate) replaced by new content: "Non-closure in the binary model" (Lemmas 9.1–9.2, Thm. 9.3, Cor. 9.4, Thm. 9.5) computing ∆_r in the binary model | ✔ verified: no loss of unique content; the new section is substantive |
| **D.2** Undefined objects (O, d_prot, five functionals, C^{g.i.}_IR, "persistence", families of Prot_UV/IR) | Conventions 5–6 (d_prot with closed balls; O); discrepancy d_a and d^base_a in Def. 2.6; the five functionals of Def. 7.1 concretely defined (κ_r via certificates, Hol^atlas via the obstruction of Thm. 2.12, Hol^prot via Def. 5.9, g_r via Res_obs, c_r via ε_flat), connected to each other and to Section 10; C^{g.i.}_IR defined; "persistence" defined; the five morphism families of Prot_UV/IR specified; scale order ⪯ on Res (Def. 5.2) | ✔ verified |
| **D.3** Dil⁺ never used despite the abstract | Paragraph after Def. 6.5: the dilation is the optimal local Lipschitz constant of E_π; `Dil⁺ < L ⟹ E_π(r) ≤ Lr on [0,r₀] ⟹ R_ε ≥ min(r₀, ε/L)`; with local attainment of the limit (e.g., the binary model, where E_π(r) is linear near 0) one obtains `R_ε ≥ min(r₁, ε/Dil⁺)` | ✔ verified (the limit step L ↓ Dil⁺ requires the local attainment, now declared) |
| **D.4** Theorem 3.4 tautological | Def. 3.3 = injectivity of the profile; Thm. 3.4 = identification of the observer by the profile, with the non-trivial instance Thm. 8.1 | ✔ verified |
| **D.5** R_ε defined twice without reconciliation | Paragraph after Def. 6.4: exact equivalence of Defs. 4.3 and 6.4 under maximal frames (Q_{π,r} = Q_π ∩ Q_π′ on the ball); the binary model uses Def. 4.3 in d_sem units (query norms = 1; factor 2 between conventions) | ✔ verified (both directions under the correct hypothesis) |
| **D.6** Open/closed balls inconsistency | Convention 5: closed protocol balls `B^prot_r(π) := {π′ : d_prot ≤ r}`, used consistently in Defs. 5.11–6.4, Thm. 5.17, Section 8 | ✔ verified |
| **D.7** "Hypothesis 6.10" (numbering) | Reference corrected to Hypothesis 6.11 | ✔ verified |
| **D.8** Prop. 10.2 (undeclared hypotheses); proof of Thm. 10.11 does not use assumptions 1–2 | Explicit hypotheses (H self-adjoint ≥ 0, HΩ = 0, unique vacuum, E({0}) = |Ω⟩⟨Ω|, µ_O({0}) = 0); the proof of Thm. 10.11 now uses all four assumptions | ✔ verified |
| **D.9** Sign of ∂θ/∂β | Corrected to −p | ✔ verified |

**Additional second-round corrections (adversarial audit of the correction itself):**

- **Lemma 9.1 / Thm. 9.3(ii):** the original atlas-calculation formula (1−β)/2 used an invalid reduction over the full query orbit. Corrected using the base-query discrepancy `d^base_a` (extended Def. 2.6): `Hol^atlas_r(π) = (1/2) max( max(α, 1−η−β−α), max(θ(π), 1−β−θ(π)) ) ≥ η/4`. Values of Thm. 9.5 corrected to 0.3 and 0.15 (η = 0.1); strict monotonicity in β verified (preorder direction corrected).
- **Thm. 6.13:** quantification of δ completed (`δ < min(δ₀, R_ε, r*−R_ε)`).
- **Thm. 9.3(iii):** interior condition α+β < 1−η for `Hol^prot = 2` (boundary degeneration documented).
- **Justification of r_word:** the step (t/2)(α+t/2) ≤ t corrected (via the D_η restriction, not α < 1 and t ≤ 4).
- **References:** [1]–[8] now cited in the text.
- **Orphans:** Def. 5.13 (P_π(r)) referenced in Remark 5.16; "r_π ⪰ r" with the scale order of Res.

#### Final verification
- **Compilation:** no errors or relevant warnings (29 pages).
- **Symbolic verifications (SymPy):** commutator c_{u,v} = (α,β,p+uv); residual (1−α−β)|uv|; gradient and Lipschitz bound 2; injectivity of Φ (Thm. 8.1); precomposition closure; exact Section 9 values (0.3 and 0.15; identity θ + (1−β−θ) = 1−β; bounds η/4, ηr²/8, 2r); linearity of E_π(r) in the binary model.
- **Final adversarial audit:** all pieces verified CORRECT; two residual inconsistencies detected (the Def. 7.1(2) formula and the Thm. 9.3 display) were corrected and re-verified.

#### Resulting state
The document is now **mathematically correct and in publishable state**, with all numbered claims proved or honestly labeled as hypotheses/conjectures: abstract holonomy is a genuinely non-trivial quantity (exactly characterized), and the binary model exhibits it with exact value 2; the binary model is a rigorous instance of the framework (S–I–E built; exact compatibility; T_real = T_γ); the agreement bounds (two-sided window), the finite-bank estimators, and non-compressibility are correct; the obstruction vector is concretely defined and non-trivial in the binary model (no global trivialization at any scale; quotient with ≥ 2 classes; strict order). The Yang–Mills reduction remains **conditional** (Bridges A and B as explicit conjectures) — correct and honest; it does not claim to solve the mass-gap problem.

**Residual (by design, not errors):** Bridges A and B remain conjectures; the YM reduction is conditional.

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
| COVERTRACE-SAT (Unified Document, Vol. I) | 0 | 0 | 5 mandatory (citation) + minor presentation defects | Sound — certified, conditioned on mandatory citation corrections |
| Connections SAT–COVERTRACE (unifying note) | 0 | 0 | All corrections of both rounds applied (C1–C6, M1–M7) | Sound — certified, accepted in second round |
| Epistemic Closure Nets | 1 (D1 composition convention, corrected) | 2 (D2 `MT_I`/`τ^o`, D3 `Δ_loop`, corrected) | D4 (Table 1 vs Def. 9.18) + 10 minor, all corrected | Sound — certified, accepted with mandatory revisions; none pending after Addendum §7 |
| Physical Observer Geometry | 5 (F1, F2, C.1, C.2, D.9 of the first version, corrected) | 2 (D.2, D.8, corrected) | 7 (D.1, D.3–D.7) + 2 residual second-round inconsistencies, all corrected | Sound — certified, accepted in second round |

---

*Revisión completada el 10 y 11 de agosto de 2026 sobre extracciones `pdftotext -layout -enc UTF-8` de los PDFs originales; la revisión del octavo documento (Locality, Soft Causal Cones, and Informational Limits of Agency) se completó el 12 de agosto de 2026 con verificación numérica independiente y auditoría adversarial; la revisión del noveno documento (Teoría de Conservación de Óptimos y Complejidad) se completó el 14 de agosto de 2026 con verificación simbólica asistida por computadora (SymPy) y auditoría adversarial; la revisión del décimo documento (COVERTRACE-SAT como Compilación de Conocimiento por Subcubos Disjuntos, documento unificado del Vol. I) se completó el 14 de agosto de 2026 con revisión multiagente, verificación computacional independiente (Python 3.13) y auditorías adversariales. / Review completed on August 10–11, 2026 over `pdftotext -layout -enc UTF-8` extractions of the original PDFs; the review of the eighth document (Locality, Soft Causal Cones, and Informational Limits of Agency) was completed on August 12, 2026 with independent numerical verification and adversarial auditing; the review of the ninth document (Theory of Conservation of Optima and Complexity) was completed on August 14, 2026 with computer-assisted symbolic verification (SymPy) and adversarial auditing; the review of the tenth document (COVERTRACE-SAT as Disjoint-Subcube Knowledge Compilation, unified document of Vol. I) was completed on August 14, 2026 with multi-agent review, independent computational verification (Python 3.13), and adversarial audits; la revisión del undécimo documento (nota unificadora Conexiones entre el Teorema de la Ecuación SAT y COVERTRACE-SAT, versión corregida) se completó el 15 de agosto de 2026 en dos rondas con re-verificación computacional independiente de todas las identidades (aritmética exacta). / the review of the eleventh document (unifying note Connections between the SAT Equation Theorem and COVERTRACE-SAT, corrected version) was completed on August 15, 2026 in two rounds with independent computational re-verification of all identities (exact arithmetic).*


*La revisión del duodécimo documento (Epistemic Closure Nets: Curvature, Holonomy, Certification, and Meta-Closure in an Expansive Network Formalism, versión corregida) se completó el 17 de agosto de 2026 en dos rondas (seis revisores independientes + un auditor adversario), con verificación numérica independiente del nodo P1★ (Python 3.13/numpy) y re-verificación post-corrección (compilación `pdflatex` y auditoría de referencias con 0 problemas); las cuatro correcciones obligatorias (D1–D4) y todas las menores accionables fueron aplicadas y re-verificadas. / The review of the twelfth document (Epistemic Closure Nets: Curvature, Holonomy, Certification, and Meta-Closure in an Expansive Network Formalism, corrected version) was completed on August 17, 2026 in two rounds (six independent reviewers + one adversarial auditor), with independent numerical verification of node P1★ (Python 3.13/numpy) and post-correction re-verification (`pdflatex` compilation and reference audit with 0 problems); the four mandatory corrections (D1–D4) and all actionable minor defects were applied and re-verified. La revisión del decimotercer documento (Physical Observer Geometry, Protocol Holonomy, Order by Non-Closure, and Spectral Obstructions, versión corregida) se completó el 19 de agosto de 2026 en segunda ronda de revisión por pares, con re-verificación simbólica (SymPy) y auditorías adversariales cláusula por cláusula; el documento queda matemáticamente correcto y en estado publicable. / The review of the thirteenth document (Physical Observer Geometry, Protocol Holonomy, Order by Non-Closure, and Spectral Obstructions, corrected version) was completed on August 19, 2026 in a second peer-review round, with symbolic re-verification (SymPy) and clause-by-clause adversarial audits; the document is now mathematically correct and in publishable state.*
