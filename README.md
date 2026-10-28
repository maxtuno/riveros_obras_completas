# Obras Completas — Oscar Riveros
## Complete Works — Oscar Riveros

Este repositorio reúne la obra matemática de Oscar Riveros. Trece documentos ya pasaron por revisión de pares. También incluye un artículo de trabajo y una nota técnica complementaria, ambos en español e inglés. El informe de revisión, el aviso del autor y la licencia están incluidos.

This repository collects Oscar Riveros's mathematical work. Thirteen documents have been peer reviewed. It also includes a working paper and a companion technical note, both in Spanish and English. The peer-review report, the author's disclaimer, and the license are included.

---

## Manuscritos en curso / Work in progress

### Consultas comprimidas sobre la Ecuación SAT
**Compressed Queries on the SAT Equation**

*bit, rank, select y oráculos de conteo para CNF arbitrarias*  
*bit, rank, select, and counting oracles for arbitrary CNFs*

Versión final del manuscrito de trabajo, 28 de octubre de 2026.  
Final working-manuscript version, October 28, 2026.

Descargar: **[español](Consultas_Comprimidas_Ecuacion_SAT.pdf)** · **[English](Compressed_Queries_on_the_SAT_Equation.pdf)**

La Ecuación SAT guarda la tabla de verdad de una CNF en un entero de `2ⁿ` bits. El artículo se pregunta cómo consultar ese entero sin construirlo. La consulta puntual es barata; el problema está en `rank`, `select`, `#SAT` y el muestreo uniforme. La aportación principal es un mapa de barreras: si alguna de las representaciones estudiadas admitiera un compilador uniforme polinómico, se seguiría `#SAT ∈ FP` y, por el teorema de Toda, `PH = P`. El texto también corrige el teorema de consultas afines, incorpora el ejemplo de Sasao discutido por Bernasconi, Ciriani, Luccio y Pagli, que descarta la DSOP como ruta universal, y plantea un programa de investigación hacia `P = NP`. La parte experimental es preliminar y apunta a que el cuello de botella está en el compilador, no en el motor de consultas.

The SAT Equation stores the truth table of a CNF in a `2ⁿ`-bit integer. The paper asks how to query that integer without building it. Point queries are cheap; the hard part is `rank`, `select`, `#SAT`, and uniform sampling. The main contribution is a barrier map: if any of the representations studied here had a uniform polynomial compiler, it would follow that `#SAT ∈ FP` and, by Toda's theorem, `PH = P`. The paper also corrects the affine-query theorem, incorporates the Sasao example discussed by Bernasconi, Ciriani, Luccio, and Pagli, which rules out DSOP as a universal route, and sets out a research program toward `P = NP`. The experimental side is preliminary and points to the compiler, not the query engine, as the bottleneck.

Es la versión final de un manuscrito de trabajo. Se publica para compartir resultados mientras el programa avanza. Solo tiene una revisión de pares simple, así que las revisiones adversariales y las comprobaciones adicionales quedan del lado del lector. No forma parte del corpus certificado de `PEER_REVIEW.md`.

This is the final version of a working manuscript. It is published to share results as the program develops. It has only had a simple peer review, so adversarial reviews and further checks are left to the reader. It is not part of the certified corpus in `PEER_REVIEW.md`.

### Complejidad de representaciones para la Ecuación SAT
**Representation Complexity of the SAT Equation**

*cotas superiores, inferiores y compilación híbrida*  
*upper bounds, lower bounds, and hybrid compilation*

Manuscrito de trabajo, 28 de octubre de 2026.

Descargar: **[español](Complejidad_Representaciones_Ecuacion_SAT.pdf)** · **[English](Representation_Complexity_SAT_Equation.pdf)**

La nota retoma donde termina el artículo anterior, pero cambia la pregunta. En lugar de preguntar si una representación universal resuelve `P = NP`, estudia qué propiedades estructurales fijan el tamaño mínimo de una representación y el coste de construirla. Reúne un paisaje de DSOP, ADSOP, ZDD y Fourier con inclusiones y separaciones incondicionales; un teorema de composición por regiones y un perfil de anchura híbrida; cotas superiores parametrizadas por puertas traseras y treewidth; y una distinción entre tamaño de representación, tamaño de compilación híbrida y tiempo de compilación uniforme. También corrige el bucle CEGAR: para detectar una asignación falsificadora fuera de la cobertura hay que consultar `¬F ∧ ¬Cov(C)`, no `F ∧ ¬Cov(C)`. No pretende demostrar `P = NP`; su objetivo es un mapa de cotas y una agenda de problemas abiertos.

The note picks up where the previous paper ends, but changes the question. Instead of asking whether a universal representation solves `P = NP`, it studies which structural properties determine the minimum size of a representation and the cost of building it. It brings together a landscape of DSOP, ADSOP, ZDD, and Fourier with inclusions and unconditional separations; a region-composition theorem and a hybrid width profile; upper bounds parameterized by backdoors and treewidth; and a distinction between representation size, hybrid compilation size, and uniform compilation time. It also corrects the CEGAR loop: to detect a falsifying assignment outside the cover, one must query `¬F ∧ ¬Cov(C)`, not `F ∧ ¬Cov(C)`. It does not claim to prove `P = NP`; its goal is a map of bounds and an agenda of open problems.

**Estado.** Es un manuscrito de trabajo. Se publica para compartir el mapa de cotas mientras el programa avanza. No forma parte del corpus certificado de `PEER_REVIEW.md`.

This is a working manuscript, published to share the map of bounds as the program develops. It is not part of the certified corpus in `PEER_REVIEW.md`.

---

## Estado del repositorio / Repository status

Trece documentos tienen revisión por pares certificada. El informe completo, con veredictos, hallazgos y correcciones, está en [`PEER_REVIEW.md`](PEER_REVIEW.md).

Thirteen documents have certified peer review. The full report, including verdicts, findings, and corrections, is in [`PEER_REVIEW.md`](PEER_REVIEW.md).

El artículo sobre consultas a la Ecuación SAT y la nota sobre complejidad de representaciones son trabajos en curso y no forman parte de ese corpus. El resto de las obras del autor, como el volumen compilado y los ejercicios resueltos, sigue en revisión.

The paper on queries to the SAT Equation and the note on representation complexity are works in progress and are not part of that corpus. The rest of the author's work, such as the compiled volume and the solved exercises, is still under review.

---

## Contenido / Contents

*Certificado* = revisado por pares; *Trabajo* / *Working paper* = en curso.

| Archivo / File | Contenido / Contents | Estado / Status |
|----------------|----------------------|-----------------|
| `A_Unique_Encoding_of_Satisfying_Assignments.pdf` | A Unique Encoding of Satisfying Assignments for Balanced CNFs. El teorema de la Ecuación SAT para CNF balanceadas. | Certificado |
| `Autorreferencia Segura - Riveros.pdf` | Autorreferencia Segura en Familias Dinámicas de Estados. Velocidad crítica, divergencia, tubos invariantes y no-retorno. | Certificado |
| `coherent_flow_companion.pdf` | Coherent Flow: A Companion Note to Epistemic Geometry. Islas coherentes, balance detallado, curvatura KL y equilibrio único. | Certificado |
| `continuous_epistemic_geometry.pdf` | Continuous Epistemic Geometry. Semántica continua para CNF, Monte Carlo con Hoeffding, compilación disjunta y transferencia `ε-net`. | Certificado |
| `Epistemic_Geometry_of_Closure - Riveros.pdf` | Epistemic Geometry of Closure. SCE-IM, curvatura Lipschitz, completitud de zippers y estabilidad con recursos. | Certificado |
| `epistemic_geometry_riveros.pdf` | Epistemic Geometry: Finite Verification, Curvature, and Structural Obstructions. Marco unificador, física discreta verificable y teoremas 8.7–8.8. | Certificado |
| `sat-equation-generalized.pdf` | A Generalization of the SAT Equation Theorem to Arbitrary CNF Formulas via Bitwise OR Encoding. OR bit a bit sin acarreos. | Certificado |
| `Locality_Soft_Causal_Cones_and_Informati.pdf` | Locality, Soft Causal Cones, and Informational Limits of Agency. Cota Lieb–Robinson, Duhamel, supresión exponencial y límites de agencia. | Certificado |
| `tcoc_riveros.pdf` | Teoría de Conservación de Óptimos y Complejidad. Minimizadores, transferencia de complejidad, levantamientos exactos y esquema condicional `P = NP`. | Certificado |
| `COVERTRACE_SAT_Disjoint_Subcube_Unificado.pdf` | COVERTRACE-SAT: compilación por subcubos disjuntos (Vol. I, documento unificado). #SAT, cota de paridad, colapso condicional de PH, Fourier y certificado poliédrico. | Certificado |
| `SAT_Equation_ES.pdf` | El Teorema de la Ecuación SAT y su Generalización. Edición en español de los manuscritos 1 y 7. | Certificado |
| `COVERTRACE_SAT_Disjoint_Subcube_Unificado_ES.pdf` | COVERTRACE-SAT como Compilación de Conocimiento por Subcubos Disjuntos. Traducción íntegra al español del Vol. I. | Certificado |
| `Conexiones_SAT_Equation_COVERTRACE_ES.pdf` | Conexiones entre el Teorema de la Ecuación SAT y COVERTRACE-SAT. Nota unificadora: `popcnt(S(F)) = \|U(F)\| = Σ vol(u)`, dualidad acarreo–disyunción y caso paridad/Thue–Morse. | Certificado |
| `Epistemic_Closure_Net - Riveros.pdf` | Epistemic Closure Nets. Red tipada, holonomía, cociclos, bancos finitos, nodos P1–P5 y artefacto P1★. | Certificado |
| `Physical_Observer_Geometry_LaTeX_v2.pdf` | Physical Observer Geometry. Holonomía de protocolo, orden por no-clausura, obstrucciones espectrales y reducción Yang–Mills condicional. | Certificado |
| `Consultas_Comprimidas_Ecuacion_SAT.pdf` | Consultas comprimidas sobre la Ecuación SAT. Versión final en español del manuscrito de trabajo. | Trabajo |
| `Compressed_Queries_on_the_SAT_Equation.pdf` | Compressed Queries on the SAT Equation. Final English edition of the working paper. | Working paper |
| `Complejidad_Representaciones_Ecuacion_SAT.pdf` | Complejidad de representaciones para la Ecuación SAT. Cotas superiores, inferiores y compilación híbrida. | Trabajo |
| `Representation_Complexity_SAT_Equation.pdf` | Representation Complexity of the SAT Equation. Upper bounds, lower bounds, and hybrid compilation. | Working paper |
| `PEER_REVIEW.md` | Revisión matemática por pares de los trece documentos certificados / Mathematical peer review of the thirteen certified documents. | Informe |
| `DISCLAMER.md` | Aviso del autor, alcance, asistencia de IA y perspectiva sobre la IA y la investigación / Author's disclaimer, scope, AI assistance, and perspective on AI and research. | Aviso |
| `LICENSE.txt` | Licencia / License. | Legal |

---

## Revisión por pares / Peer review

La auditoría de los trece documentos certificados está en [`PEER_REVIEW.md`](PEER_REVIEW.md). Se revisó cada teorema, definición y prueba, con verificación numérica o simbólica independiente y auditorías adversariales cuando hacía falta.

The audit of the thirteen certified documents is in [`PEER_REVIEW.md`](PEER_REVIEW.md). Every theorem, definition, and proof was reviewed, with independent numerical or symbolic verification and adversarial audits where needed.

Las publicaciones de trabajo quedan fuera de esa auditoría. El artículo bilingüe solo cuenta con una revisión simple; la nota sobre complejidad de representaciones es un manuscrito de trabajo.

The work-in-progress publications are outside that audit. The bilingual paper has only had a simple review; the note on representation complexity is a working manuscript.

---

## Aviso / Disclaimer

El aviso del autor sobre la asistencia de IA, el estatus de la matemática como lenguaje falseable y la perspectiva sobre la IA y la investigación está en [`DISCLAMER.md`](DISCLAMER.md).

The author's disclaimer on AI assistance, the status of mathematics as a falsifiable language, and the perspective on AI and research is in [`DISCLAMER.md`](DISCLAMER.md).

---

## Licencia / License

© 2025–2026 Oscar Riveros. Todos los derechos reservados. Ver [`LICENSE.txt`](LICENSE.txt).

© 2025–2026 Oscar Riveros. All rights reserved. See [`LICENSE.txt`](LICENSE.txt).
