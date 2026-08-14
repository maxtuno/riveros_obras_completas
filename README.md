# Obras Completas — Oscar Riveros / Complete Works — Oscar Riveros

Compilación digital de las investigaciones de Oscar Riveros: nueve manuscritos originales, su revisión matemática por pares, el aviso del autor y la licencia. Edición compilada — Agosto 2026.

Digital compilation of Oscar Riveros's research: nine original manuscripts, their mathematical peer review, the author's disclaimer, and the license. Compiled edition — August 2026.

---

## Estado del repositorio / Repository status

**Español:** Este repositorio contiene las obras que ya pasaron la revisión por pares. Ocho manuscritos están libres de observaciones pendientes (solo se documentan defectos menores); el octavo (Locality, Soft Causal Cones, and Informational Limits of Agency) está certificado en solidez matemática, condicionado a las correcciones editoriales obligatorias documentadas en `PEER_REVIEW.md`. El resto de las obras del autor —el volumen compilado completo, los manuscritos complementarios y los ejercicios resueltos— se encuentra en revisión. El repositorio se irá actualizando a medida que cada obra quede completamente libre de observaciones.

**English:** This repository contains the works that have already passed peer review. Eight manuscripts are free of pending observations (only minor defects are documented); the eighth (Locality, Soft Causal Cones, and Informational Limits of Agency) is certified mathematically sound, conditioned on the mandatory editorial corrections documented in `PEER_REVIEW.md`. The rest of the author's works —the full compiled volume, the complementary manuscripts, and the solved exercises— is under review. The repository will be updated as each work becomes completely free of observations.

---

## Español

### Contenido del repositorio

| Archivo | Contenido |
|---------|-----------|
| `A_Unique_Encoding_of_Satisfying_Assignments.pdf` | A Unique Encoding of Satisfying Assignments for Balanced CNFs |
| `Autorreferencia Segura - Riveros.pdf` | Autorreferencia Segura en Familias Dinámicas de Estados |
| `coherent_flow_companion.pdf` | Coherent Flow: A Companion Note to Epistemic Geometry |
| `continuous_epistemic_geometry.pdf` | Continuous Epistemic Geometry: cGCNF, Disjoint Compilation, and Black-Hole Observables |
| `Epistemic_Geometry_of_Closure - Riveros.pdf` | Epistemic Geometry of Closure: SCE-IM, Coherent Flow, and Operational Completeness |
| `epistemic_geometry_riveros.pdf` | Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions Across Logic, Computation, and Physics |
| `sat-equation-generalized.pdf` | A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding |
| `Locality_Soft_Causal_Cones_and_Informati.pdf` | Locality, Soft Causal Cones, and Informational Limits of Agency |
| `tcoc_riveros.pdf` | Teoría de Conservación de Óptimos y Complejidad |
| `PEER_REVIEW.md` | Revisión matemática por pares de los nueve documentos |
| `DISCLAMER.md` | Aviso sobre la asistencia de IA (español e inglés) |
| `LICENSE.txt` | Licencia |

### Los documentos

**1. A Unique Encoding of Satisfying Assignments for Balanced CNFs**
Teorema de la Ecuación SAT: toda fórmula CNF balanceada sobre `n` variables Booleanas queda caracterizada unívocamente por el número `S = Σ_C 2^{T(C)}`, donde `T(C)` es el número binario del vector de signos de la cláusula `C`. Escrito con al menos `2ⁿ` bits, la expansión binaria de `S` codifica exactamente la tabla de verdad de la fórmula: un `1` marca una asignación que no satisface `F` y un `0` una que sí la satisface.

**2. Autorreferencia Segura en Familias Dinámicas de Estados**
Teoría axiomática de la autorreferencia segura: velocidad crítica local `ν_c` y su uniformidad, condiciones de divergencia global y alcanzable, invariancia de tubos seguros móviles bajo política ISS, estabilidad práctica exponencial y el criterio de no-retorno mediante conjuntos invariantes disjuntos del captor.

**3. Coherent Flow: A Companion Note to Epistemic Geometry**
Nota complementaria del programa de Geometría Epistémica: islas coherentes y descenso determinista con terminación finita, balance detallado del kernel Metropolis–Hastings, curvatura epistémica KL con su caso separable `I(A;B)`, identidad exacta de Lyapunov para el flujo coherente y equilibrio único en la hoja de interfaz.

**4. Continuous Epistemic Geometry: cGCNF, Disjoint Compilation, and Black-Hole Observables**
Semántica continua para fórmulas CNF: apertura de los conjuntos de modelos, estimación Monte Carlo con cotas de Hoeffding, compilación por subcubos disjuntos con su barrera de fragmentación `2ⁿ`, y transferencia por bancos finitos `ε-net` con margen.

**5. Epistemic Geometry of Closure: SCE-IM, Coherent Flow, and Operational Completeness**
Sistema SCE-IM: curvatura epistémica con estabilidad Lipschitz e invariancia de signo, completitud operacional de zippers, completitud con recursos y estabilidad de la curvatura acotada; cierra el programa con las redes de cierre epistémico.

**6. Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions Across Logic, Computation, and Physics**
Marco unificador de la Geometría Epistémica sobre cinco líneas técnicas: física discreta verificable por SAT (GCNF, Gauss–Bonnet discreto, conos causales Booleanos), la ecuación SAT, compilación disjunta COVERTRACE con barrera de paridad y colapso PH condicional, curvatura epistémica con el principio de refinamiento derivacional (DRP) y la obstrucción gödeliana, Espacio Métrico en Capas (LMS), localidad y agencia, y los teoremas de unificación: el trilema de verificación física finita (Teo. 8.7) y la obstrucción unificada (Teo. 8.8).

**7. A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding**
Generalización del Teorema de la Ecuación SAT de fórmulas balanceadas a fórmulas CNF arbitrarias: cada cláusula aporta una máscara binaria que pone un `1` en cada posición correspondiente a una asignación que la falsifica, y el OR bit a bit de todas las máscaras produce el entero `S = OR_j OR_{M′⊆MC_j} 2^{B(C_j) + Σ_{i∈M′} 2^{N−i}}`, cuya expansión binaria con `2^N` bits codifica exactamente la tabla de verdad de `F` sin acarreos, aun cuando cláusulas distintas compartan asignaciones falsificantes.

**8. Locality, Soft Causal Cones, and Informational Limits of Agency**
Esqueleto axiomático (desarrollo no lineal) para control local e indistinguibilidad remota: cota de Lieb–Robinson de doble suma con refinamiento geométrico `K_µ`, identidad de Duhamel a dos tiempos con flujo causal en el tiempo restante `T−s`, supresión exponencial de la influencia y la agencia fuera del cono causal blando, cierre de la capacidad de comunicación vía Holevo y Fannes–Audenaert bajo indistinguibilidad geométrica, y reglas de responsabilidad remota que respetan los límites causales salvo control «efectivamente omnipotente».

**9. Teoría de Conservación de Óptimos y Complejidad**
Teoría local para estudiar cuándo una representación geométrica o alternativa de una familia de problemas de optimización discreta preserva simultáneamente el óptimo combinatorio y la complejidad temporal polinomial: conservación exacta del conjunto de minimizadores (Thm 5.1), transferencia de complejidad bajo exactitud fuerte (Thm 5.3), transporte de óptimos entre representaciones afínmente equivalentes (Prop. 6.5, Cor. 6.6), criterio lineal necesario y suficiente —no constructivo en general— de existencia de levantamientos exactos de costos (Thm 7.2), cambio de representación correctamente tipado (Thm 8.13) y el esquema suficiente que aísla la cadena completa de hipótesis de representación exacta, fidelidad polinomial, extracción fuerte y puente formal hacia optimización exacta para convertir el programa de los pedigree polytopes en un teorema del tipo `P = NP` (Thm 9.5), con la instanciación en STSP explícitamente abierta.

### Revisión por pares — `PEER_REVIEW.md`

Auditoría matemática exhaustiva de los nueve manuscritos: cada documento fue leído íntegramente y verificado teorema por teorema, definición por definición y prueba por prueba (sobre extracciones `pdftotext -layout -enc UTF-8` de los PDFs originales; la revisión del octavo incluye además verificación numérica independiente y auditoría adversarial, y la del noveno verificación simbólica asistida por computadora (SymPy) y auditoría adversarial). Veredicto general: los nueve documentos son matemáticamente correctos y rigurosos, sin errores fatales. Ocho están libres de observaciones pendientes (solo defectos menores documentados); el octavo (Locality, Soft Causal Cones, and Informational Limits of Agency) está certificado en solidez matemática, condicionado a las correcciones editoriales obligatorias de integridad y atribución documentadas en la revisión.

### Aviso — `DISCLAMER.md`

Declaración del autor sobre el papel de la IA en la redacción y la revisión de estas obras: la matemática como lenguaje falseable e independiente de la interpretación, la curvatura entre sintaxis y semántica que estudia la Geometría Epistémica, y el valor del conocimiento humano frente a la recombinación del corpus. Disponible en español e inglés.

### Licencia

© 2025–2026 Oscar Riveros. Todos los derechos reservados. Ver [LICENSE.txt](LICENSE.txt).

---

## English

### Repository contents

| File | Contents |
|------|----------|
| `A_Unique_Encoding_of_Satisfying_Assignments.pdf` | A Unique Encoding of Satisfying Assignments for Balanced CNFs |
| `Autorreferencia Segura - Riveros.pdf` | Safe Self-Reference in Dynamic Families of States |
| `coherent_flow_companion.pdf` | Coherent Flow: A Companion Note to Epistemic Geometry |
| `continuous_epistemic_geometry.pdf` | Continuous Epistemic Geometry: cGCNF, Disjoint Compilation, and Black-Hole Observables |
| `Epistemic_Geometry_of_Closure - Riveros.pdf` | Epistemic Geometry of Closure: SCE-IM, Coherent Flow, and Operational Completeness |
| `epistemic_geometry_riveros.pdf` | Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions Across Logic, Computation, and Physics |
| `sat-equation-generalized.pdf` | A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding |
| `Locality_Soft_Causal_Cones_and_Informati.pdf` | Locality, Soft Causal Cones, and Informational Limits of Agency |
| `tcoc_riveros.pdf` | Theory of Conservation of Optima and Complexity |
| `PEER_REVIEW.md` | Mathematical peer review of the nine documents |
| `DISCLAMER.md` | Disclaimer on AI assistance (Spanish and English) |
| `LICENSE.txt` | License |

### The documents

**1. A Unique Encoding of Satisfying Assignments for Balanced CNFs**
The SAT Equation Theorem: every balanced CNF formula over `n` Boolean variables is uniquely characterized by the number `S = Σ_C 2^{T(C)}`, where `T(C)` is the binary number of clause `C`'s sign vector. Written with at least `2ⁿ` digits, the binary expansion of `S` encodes exactly the truth table of the formula: a `1` marks an assignment that does not satisfy `F` and a `0` one that does.

**2. Safe Self-Reference in Dynamic Families of States**
Axiomatic theory of safe self-reference: local critical velocity `ν_c` and its uniformity, global and reachable divergence conditions, invariance of safe moving tubes under an ISS policy, practical exponential stability, and the no-return criterion via invariant sets disjoint from the captor.

**3. Coherent Flow: A Companion Note to Epistemic Geometry**
Companion note to the Epistemic Geometry program: coherent islands and deterministic descent with finite termination, detailed balance of the Metropolis–Hastings kernel, KL epistemic curvature with its separable case `I(A;B)`, exact Lyapunov identity for the coherent flow, and unique equilibrium on the interface leaf.

**4. Continuous Epistemic Geometry: cGCNF, Disjoint Compilation, and Black-Hole Observables**
Continuous semantics for CNF formulas: openness of model sets, Monte Carlo estimation with Hoeffding bounds, disjoint-subcube compilation with its `2ⁿ` fragmentation barrier, and finite `ε-net` bank transfer with margin.

**5. Epistemic Geometry of Closure: SCE-IM, Coherent Flow, and Operational Completeness**
The SCE-IM system: epistemic curvature with Lipschitz stability and sign invariance, operational zipper completeness, completeness with resources, and bounded curvature stability; closes the program with epistemic closure nets.

**6. Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions Across Logic, Computation, and Physics**
Unifying framework of Epistemic Geometry over five technical lines: SAT-verifiable discrete physics (GCNF, discrete Gauss–Bonnet, Boolean causal cones), the SAT equation, disjoint COVERTRACE compilation with parity barrier and conditional PH collapse, epistemic curvature with the derivational refinement principle (DRP) and the Gödelian obstruction, Layered Metric Space (LMS), locality and agency, and the unification theorems: the trilemma of finite physical verification (Thm. 8.7) and the unified obstruction theorem (Thm. 8.8).

**7. A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding**
Generalization of the SAT Equation Theorem from balanced formulas to arbitrary CNF formulas: each clause contributes a binary mask that sets a `1` in every position corresponding to an assignment that falsifies it, and the bitwise OR of all masks yields the integer `S = OR_j OR_{M′⊆MC_j} 2^{B(C_j) + Σ_{i∈M′} 2^{N−i}}`, whose binary expansion with `2^N` bits encodes exactly the truth table of `F` without carries, even when distinct clauses share falsifying assignments.

**8. Locality, Soft Causal Cones, and Informational Limits of Agency**
Axiomatic skeleton (nonlinear development) for local control and remote indistinguishability: double-sum Lieb–Robinson bound with geometric refinement `K_µ`, two-time Duhamel identity with causal flow in the remaining time `T−s`, exponential suppression of influence and agency outside the soft causal cone, communication capacity closure via Holevo and Fannes–Audenaert under geometric indistinguishability, and remote responsibility rules respecting the causal limits except under «effectively omnipotent» control.

**9. Theory of Conservation of Optima and Complexity**
Local theory for studying when a geometric or alternative representation of a family of discrete optimization problems simultaneously preserves the combinatorial optimum and polynomial time complexity: exact conservation of the minimizer set (Thm 5.1), complexity transfer under strong exactness (Thm 5.3), transport of optima between affinely equivalent representations (Prop. 6.5, Cor. 6.6), a linear necessary-and-sufficient — non-constructive in general — criterion for the existence of exact cost lifts (Thm 7.2), a correctly typed representation change (Thm 8.13), and the sufficient scheme isolating the full chain of exact-representation, polynomial-fidelity, strong-extraction, and formal-bridge-to-exact-optimization hypotheses needed to turn the pedigree polytopes program into a theorem of the type `P = NP` (Thm 9.5), with the STSP instantiation explicitly open.

### Peer review — `PEER_REVIEW.md`

Exhaustive mathematical audit of the nine manuscripts: each document was read in full and verified theorem by theorem, definition by definition, and proof by proof (on `pdftotext -layout -enc UTF-8` extractions of the original PDFs; the review of the eighth also includes independent numerical verification and adversarial auditing, and that of the ninth computer-assisted symbolic verification (SymPy) and adversarial auditing). Overall verdict: all nine documents are mathematically correct and rigorous, without fatal errors. Eight are free of pending observations (only minor documented defects); the eighth (Locality, Soft Causal Cones, and Informational Limits of Agency) is certified mathematically sound, conditioned on the mandatory integrity and attribution corrections documented in the review.

### Disclaimer — `DISCLAMER.md`

The author's statement on the role of AI in writing and reviewing these works: mathematics as a falsifiable language independent of interpretation, the syntax–semantics curvature studied by Epistemic Geometry, and the value of human knowledge against the recombination of the corpus. Available in Spanish and English.

### License

© 2025–2026 Oscar Riveros. All rights reserved. See [LICENSE.txt](LICENSE.txt).
