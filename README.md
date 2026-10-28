# Obras Completas — Oscar Riveros
## Complete Works — Oscar Riveros

Compilación bilingüe de la investigación matemática de Oscar Riveros: trece documentos con revisión por pares certificada y dos ediciones —español e inglés— de un manuscrito de trabajo sobre consultas a la Ecuación SAT. Incluye la nota unificadora del Vol. I, el informe de revisión por pares, el aviso del autor y la licencia.

Bilingual compilation of Oscar Riveros's mathematical research: thirteen peer-reviewed documents and two editions —Spanish and English— of a working paper on queries to the SAT Equation. Includes the Vol. I unifying note, the peer-review report, the author's disclaimer, and the license.

---

## Documento destacado / Featured paper

### Consultas comprimidas sobre la Ecuación SAT
### Compressed Queries on the SAT Equation

**bit, rank, select y oráculos de conteo para CNF arbitrarias**  
**bit, rank, select, and counting oracles for arbitrary CNFs**

Oscar Riveros — Versión final del manuscrito de trabajo, 28 de octubre de 2026  
Final working-manuscript version, October 28, 2026

| Edición | PDF |
|---------|-----|
| Español | **[Consultas_Comprimidas_Ecuacion_SAT.pdf](Consultas_Comprimidas_Ecuacion_SAT.pdf)** |
| English | **[Compressed_Queries_on_the_SAT_Equation.pdf](Compressed_Queries_on_the_SAT_Equation.pdf)** |

**Español.** El artículo estudia cómo consultar el entero `S(F)` de `2ⁿ` bits de la Ecuación SAT sin materializarlo, y qué parte de esa maquinaria puede acercarse al problema `P` frente a `NP`. Separa la consulta puntual `bit(k) = 1 − F(assign(k))`, de coste `O(m)`, de las consultas agregadas `rank`, `select`, `#SAT` y el muestreo uniforme. Demuestra la equivalencia exacta entre coberturas disjuntas de la región prohibida y DF-CNF; construye un motor `rank`–`select` sobre una DSOP de tamaño `K` con coste `O(nK)` y `O(n²K)` sin materializar la tabla; reduce `rank` a conteo exacto de modelos; y combina ambas rutas en un algoritmo híbrido. Su contribución conceptual es el mapa de barreras: un compilador uniforme polinómico de cualquiera de estas representaciones implicaría `#SAT ∈ FP` y, por Toda, `PH = P`. Corrige el teorema de consultas afines, incorpora el ejemplo de Sasao —discutido por Bernasconi, Ciriani, Luccio y Pagli— que descarta a la DSOP como ruta universal, y formula un programa explícito hacia `P = NP` (cotas para ADSOP, puertas traseras afines, compilación directa a ZDD y Fourier, verificación de certificados). La instanciación subexponencial se mantiene como la hipótesis H-ETH y se demuestra condicionalmente. La evaluación experimental, preliminar, confirma que el compilador —no el motor de consulta— es el cuello de botella.

**English.** The paper studies how to query the `2ⁿ`-bit integer `S(F)` of the SAT Equation without materializing it, and how much of that machinery can be brought to bear on `P` versus `NP`. It separates the point query `bit(k) = 1 − F(assign(k))`, costing `O(m)`, from the aggregate queries `rank`, `select`, `#SAT`, and uniform sampling. It proves the exact equivalence between disjoint covers of the forbidden region and DF-CNFs; builds a `rank`–`select` engine over a size-`K` DSOP with cost `O(nK)` and `O(n²K)` without materializing the truth table; reduces `rank` to exact model counting; and combines both routes into a hybrid algorithm. Its conceptual contribution is the barrier map: a uniform polynomial compiler for any of these representations would imply `#SAT ∈ FP` and, by Toda's theorem, `PH = P`. It corrects the affine-query theorem, incorporates the Sasao example —as discussed by Bernasconi, Ciriani, Luccio, and Pagli— ruling out DSOP as a universal route, and states an explicit research program toward `P = NP` (ADSOP lower bounds, affine backdoors, direct ZDD and Fourier compilation, certificate verification). The subexponential instantiation is kept as hypothesis H-ETH and proved conditionally. The preliminary experimental evaluation confirms that the compiler —not the query engine— is the bottleneck.

> **Estado / Status.** Versión final de un manuscrito de trabajo, sujeta a futuras actualizaciones. Se publica con el propósito de compartir conocimiento en tiempo real. Solo se garantiza una revisión de pares simple; la revisión adversarial y las revisiones adicionales de este documento corren por cuenta del lector. No forma parte del corpus certificado en `PEER_REVIEW.md`.
>
> Final version of a working manuscript, subject to future updates. It is published to share knowledge in real time. Only a simple peer review is guaranteed; adversarial and further reviews of this document are the reader's responsibility. It is not part of the certified corpus in `PEER_REVIEW.md`.

---

## Estado del repositorio / Repository status

**Español.**
- **Trece documentos certificados** con revisión matemática por pares; el informe completo, con veredictos, hallazgos y correcciones, está en [`PEER_REVIEW.md`](PEER_REVIEW.md).
- **Dos ediciones de un manuscrito de trabajo** (español e inglés) sobre consultas a la Ecuación SAT. Quedan fuera del corpus certificado: solo cuentan con una revisión de pares simple, y sus revisiones adicionales corren por cuenta del lector.
- El resto de las obras del autor —volumen compilado, manuscritos complementarios y ejercicios resueltos— se encuentra en revisión.

**English.**
- **Thirteen certified documents** with mathematical peer review; the full report, including verdicts, findings, and corrections, is in [`PEER_REVIEW.md`](PEER_REVIEW.md).
- **Two editions of a working paper** (Spanish and English) on queries to the SAT Equation. They are outside the certified corpus: they have only a simple peer review, and further reviews are the reader's responsibility.
- The rest of the author's works —compiled volume, complementary manuscripts, and solved exercises— are under review.

---

## Contenido del repositorio / Repository contents

**Estado / Status:** *Certificado / Certified* = revisado por pares; *Trabajo / Working paper* = manuscrito en proceso, revisión simple.

| Archivo / File | Contenido / Contents | Estado / Status |
|----------------|----------------------|-----------------|
| `A_Unique_Encoding_of_Satisfying_Assignments.pdf` | A Unique Encoding of Satisfying Assignments for Balanced CNFs — Teorema de la Ecuación SAT para CNF balanceadas. | Certificado |
| `Autorreferencia Segura - Riveros.pdf` | Autorreferencia Segura en Familias Dinámicas de Estados — velocidad crítica, divergencia, tubos invariantes y no-retorno. | Certificado |
| `coherent_flow_companion.pdf` | Coherent Flow: A Companion Note to Epistemic Geometry — islas coherentes, balance detallado, curvatura KL y equilibrio único. | Certificado |
| `continuous_epistemic_geometry.pdf` | Continuous Epistemic Geometry — semántica continua para CNF, Monte Carlo con Hoeffding, compilación disjunta y transferencia `ε-net`. | Certificado |
| `Epistemic_Geometry_of_Closure - Riveros.pdf` | Epistemic Geometry of Closure — SCE-IM, curvatura Lipschitz, completitud de zippers y estabilidad con recursos. | Certificado |
| `epistemic_geometry_riveros.pdf` | Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions — marco unificador, física discreta verificable y teoremas 8.7–8.8. | Certificado |
| `sat-equation-generalized.pdf` | A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding — OR bit a bit sin acarreos. | Certificado |
| `Locality_Soft_Causal_Cones_and_Informati.pdf` | Locality, Soft Causal Cones, and Informational Limits of Agency — cota Lieb–Robinson, Duhamel, supresión exponencial y límites de agencia. | Certificado |
| `tcoc_riveros.pdf` | Teoría de Conservación de Óptimos y Complejidad — minimizadores, transferencia de complejidad, levantamientos exactos y esquema condicional `P = NP`. | Certificado |
| `COVERTRACE_SAT_Disjoint_Subcube_Unificado.pdf` | COVERTRACE-SAT: compilación por subcubos disjuntos (Vol. I, documento unificado) — #SAT, cota de paridad, colapso condicional de PH, Fourier y certificado poliédrico. | Certificado |
| `SAT_Equation_ES.pdf` | El Teorema de la Ecuación SAT y su Generalización — edición en español de los manuscritos 1 y 7. | Certificado |
| `COVERTRACE_SAT_Disjoint_Subcube_Unificado_ES.pdf` | COVERTRACE-SAT como Compilación de Conocimiento por Subcubos Disjuntos — traducción íntegra al español del Vol. I. | Certificado |
| `Conexiones_SAT_Equation_COVERTRACE_ES.pdf` | Conexiones entre el Teorema de la Ecuación SAT y COVERTRACE-SAT — nota unificadora: `popcnt(S(F)) = \|U(F)\| = Σ vol(u)`, dualidad acarreo–disyunción y caso paridad/Thue–Morse. | Certificado |
| `Epistemic_Closure_Net - Riveros.pdf` | Epistemic Closure Nets — red tipada, holonomía, cociclos, bancos finitos, nodos P1–P5 y artefacto P1★. | Certificado |
| `Physical_Observer_Geometry_LaTeX_v2.pdf` | Physical Observer Geometry — holonomía de protocolo, orden por no-clausura, obstrucciones espectrales y reducción Yang–Mills condicional. | Certificado |
| `Consultas_Comprimidas_Ecuacion_SAT.pdf` | Consultas comprimidas sobre la Ecuación SAT — versión final en español del manuscrito de trabajo. | Trabajo |
| `Compressed_Queries_on_the_SAT_Equation.pdf` | Compressed Queries on the SAT Equation — final English edition of the working paper. | Working paper |
| `PEER_REVIEW.md` | Revisión matemática por pares de los trece documentos certificados / Mathematical peer review of the thirteen certified documents. | Informe |
| `DISCLAMER.md` | Aviso del autor, alcance, asistencia de IA y perspectiva sobre la IA y la investigación / Author's disclaimer, scope, AI assistance, and perspective on AI and research. | Aviso |
| `LICENSE.txt` | Licencia / License. | Legal |

---

## Revisión por pares / Peer review

La auditoría matemática de los trece documentos certificados —teorema por teorema, definición por definición y prueba por prueba— está en [`PEER_REVIEW.md`](PEER_REVIEW.md). Incluye verificación numérica y simbólica independiente, auditorías adversariales y el estado de las correcciones en los casos que las requirieron.

The mathematical audit of the thirteen certified documents —theorem by theorem, definition by definition, and proof by proof— is in [`PEER_REVIEW.md`](PEER_REVIEW.md). It includes independent numerical and symbolic verification, adversarial audits, and the correction status where applicable.

Las dos ediciones del manuscrito de trabajo sobre consultas a la Ecuación SAT no forman parte de esa auditoría: solo cuentan con una revisión de pares simple.

The two editions of the working paper on queries to the SAT Equation are not part of that audit: they have only a simple peer review.

---

## Aviso / Disclaimer

El aviso del autor sobre la asistencia de IA, el estatus de la matemática como lenguaje falseable y la perspectiva sobre la IA y la investigación está en [`DISCLAMER.md`](DISCLAMER.md).

The author's disclaimer on AI assistance, the status of mathematics as a falsifiable language, and the perspective on AI and research is in [`DISCLAMER.md`](DISCLAMER.md).

---

## Licencia / License

© 2025–2026 Oscar Riveros. Todos los derechos reservados. Ver [`LICENSE.txt`](LICENSE.txt).

© 2025–2026 Oscar Riveros. All rights reserved. See [`LICENSE.txt`](LICENSE.txt).
