# Automatismos Industriales · Recuperación — I.E.S. Trinidad Arroyo (Palencia)

Web de clase para los alumnos de 1MB que **repiten** Automatismos. Es **el mismo material** que la web de Automatismos (`BernardoTorio/automatismos`), pero con **otra línea de tiempo**: aquí se va por delante de la clase normal. Por eso lo nuevo se publica primero aquí y **no se sube a `automatismos` hasta que el profesor lo diga**.

Se publica con GitHub Pages desde la rama `main`, carpeta raíz: `https://bernardotorio.github.io/RecuperacionAutomatismos/` (repositorio `BernardoTorio/RecuperacionAutomatismos`).

Todas las reglas de la web de Automatismos valen aquí (su `CLAUDE.md` manda): nombres de archivo que no cambian, animaciones en la raíz, pestañas `#inicio`, `#temas`, `#ejercicios` y `#animaciones`, criterios de dibujo, letra delante del número (T, P, E), «Qué está pasando» y «Para qué sirve» debajo del dibujo, corriente sutil, modo claro y oscuro, prueba en escritorio y en móvil (400 px). **Nunca se suben zips ni .docx.**

## Qué hay
```
index.html                  portada (la de Automatismos, solo con los Temas 6, 7 y 8): var HOY = 7;
temas/                      T6_Dimensionamiento_protecciones.pdf
                            T7_Conexionado_motores_trifasicos_Automatismos.pdf   (Tema 7)
                            T7_Resolucion_averias_Automatismos.pdf               (Tema 8: el archivo conserva su nombre)
ejercicios/                 T6_Ejercicios_Dimensionamiento_protecciones.pdf (Ejercicios 1)
                            T7_Ejercicios_Conexionado_motores_trifasicos_Automatismos.pdf (Ejercicios 2: 40 preguntas tipo test)
                            T7_Ejercicios_Resolucion_averias_Automatismos.pdf (Ejercicios 3: 60 preguntas; conserva su nombre)
practicas/                  P6_Automatismos.pdf (Práctica 6 · Arranque estrella-triángulo; sale como «chip» del Tema 7 y en #ejercicios)
intensidad_calor.html … cuadro_motores.html    las seis animaciones del Tema 6, copiadas tal cual de Automatismos (vuelven a #ejercicios)
motor_red.html              T7.7  Estrella o triángulo: el motor y la red  (vuelve a #animaciones)
estrella_triangulo.html     T7.12 Arranque estrella-triángulo              (vuelve a #animaciones)
averias_protecciones.html   T8.11 ¿Qué protección salta?  (vuelve a #animaciones)
busca_averia.html           T8.12 Busca la avería          (vuelve a #animaciones)
```
- **Renumeración del 27/11/2026** (lo decidió el profesor): el Tema 7 es ahora **Conexionado de motores trifásicos** y **Resolución de averías pasa a ser el Tema 8** (sus ejercicios, Ejercicios 3; sus animaciones, T8.11 y T8.12). Los **nombres de archivo no cambian** (`T7_Resolucion_averias…`, `averias_protecciones.html`, `busca_averia.html`). Hecho: la portada y los rótulos de las dos animaciones. **Pendiente:** los dos PDF de averías siguen diciendo por dentro «Tema 7» y «Ejercicios 2» (hay que regenerarlos desde su Word de `C:\dev\originales`), y los guiones `claude/automatismos/T7/gen_anim.py` y `gen_index.py` del proyecto siguen con la numeración vieja: antes de regenerar con ellos, cambiar T7.11 → T8.11, T7.12 → T8.12, «Tema 7» → «Tema 8», «Ejercicios 2» → «Ejercicios 3» y los puntos 7.12 y 7.13 → 8.12 y 8.13.
- Lo del Tema 6 es **copia** de la web de Automatismos: si allí cambia algo, se copia aquí otra vez (no se edita aquí por separado).
- Las soluciones de los ejercicios **no se publican aquí**: las de averías están en `C:\dev\originales\automatismos\ejercicios\T7_Soluciones_Resolucion_averias_Automatismos.docx`; las del Tema 7 y las de la Práctica 6, en la web provisional (`BernardoTorio/provisional`, sección `#t7`).
- `bernardotorio.github.io` es el mismo sitio para todas las webs: la marca «✓ vista» de las animaciones del Tema 6 se comparte con la web de Automatismos (misma clave `visto:<archivo>`).

## Tema 7 · Conexionado de motores trifásicos
- Apuntes (11 páginas): bobinados y caja de bornes (U1 V1 W1 arriba, W2 U2 V2 abajo), estrella (pletinas tumbadas) y triángulo (pletinas de pie), las dos tensiones de una red (la de red, entre fases, y la de fase y neutro: escalera 130 · 230 · 400 · 690), las dos tensiones de la placa, cómo se elige la conexión, qué pasa si te equivocas y el arranque estrella-triángulo.
- Motores del tema (los del punto 6.2): **Motor A** 3 kW, Δ 230 V 11,0 A · Y 400 V 6,4 A; **Motor B** 11 kW, Δ 400 V 21,5 A · Y 690 V 12,4 A. En los ejercicios, además, Motor C (1,5 kW, 230/400 V, 6,1/3,5 A) y Motor D (7,5 kW, 400/690 V, 14,8/8,5 A).
- Arranque estrella-triángulo: **-KM1** línea, **-KM2** estrella (con el puente arriba, en sus tornillos 1-3-5) y **-KM3** triángulo (L1 a W2, L2 a U2, L3 a V2). El tiempo lo cuenta **-KT1**, un contactor aparte con el bloque temporizado a la conexión (55-56 y 67-68), como en la Práctica 5. Enclavamiento con los 61-62. El bornero -X1 tiene seis tornillos (1-2-3 a U1 V1 W1; 4-5-6 a W2 U2 V2). **-F1 va debajo de -KM1**: por él solo pasa la corriente de un bobinado y su ruleta se pone en la corriente pequeña de la placa (caja Y).
- `motor_red.html` (T7.7): red de 230, 400 o 690 V, motor A o B y pletinas; dice qué recibe cada bobinado. Guarda la red en `localStorage` (clave `red`, la misma de las animaciones de averías). `estrella_triangulo.html` (T7.12): fuerza y mando con el motor de cálculo de las animaciones de las prácticas, ruleta de -KT1 de 1 a 5 s, gráfica de la corriente y selector 230 V taller / 400 V fábrica.
- Todo sale de guiones guardados en el proyecto «Materiales para instituto» (`claude/automatismos/T7_conexionado/` y `claude/automatismos/T7_conexionado_estado.md`): **no se editan a mano los HTML**.

## Tema 8 · Resolución de averías (antes, Tema 7)
- Todo el tema, los Ejercicios 2 y las dos animaciones usan **el mismo cuadro**: un esquema de fuerza de fábrica (red de 400 V) con cuatro motores. Es la antigua Práctica 10, redibujada con los criterios actuales y con valores que cumplen el Tema 6:
  - `-F0` fusibles generales 3 × 63 A gG (cable de 16 mm²) → `-Q0` magnetotérmico general 40 A curva C (cable de 6 mm²).
  - Línea de `-M1` (5,5 kW Δ, 11 A): diferencial `-Q5` 40 A 30 mA → guardamotor `-Q1` 10-14 A, ruleta 11 A → `-KM1`.
  - Línea de `-M2` (4 kW Y, 8,3 A): diferencial `-Q6` → guardamotor `-Q2` 6,3-10 A, ruleta 8,3 A → `-KM2`.
  - Grupo de `-M3` y `-M4`: `-Q7` 16 A curva C (cable de 2,5 mm²) → diferencial `-Q8` 40 A 30 mA → `-Q3` 6 A C → `-KM3` → térmico `-F3` 2,5-4 A a 3,5 A → `-M3` (1,5 kW Y, 3,5 A); y `-Q4` 10 A C → `-KM4` → `-F4` 6-9 A a 6,4 A → `-M4` (3 kW Y, 6,4 A). Arranque de 6 veces.
  - Entre el último aparato de cada línea y su motor va el **bornero de fuerza `-X1`**, con los tornillos 1 a 12 (tres por motor: 1-2-3 para -M1 … 10-11-12 para -M4). De ahí salen las mangueras de 1,5 mm². **U1, V1 y W1 son los tornillos del motor** y se rotulan pegados a él, no en el cuadro.
  - Los magnetotérmicos y los guardamotores **no llevan símbolo de mando** (nada de la «T» de pulsador): solo la línea discontinua que va del nombre a los contactos.
  - Letras de medida del esquema (línea de -M1): Ⓐ Ⓑ el 1 y el 5 de -Q1 · Ⓒ Ⓓ el 2 y el 6 de -Q1 · Ⓔ Ⓕ el 2 y el 6 de -KM1 · Ⓖ Ⓗ el U1 y el W1 de -M1.
- **Dos redes** (punto 7.13): la de una fábrica, que es la del cuadro (400 V entre fases, con neutro; 230 V entre fase y PE; motores de 230/400 V en estrella), y la del **taller** (230 V entre fases, **sin neutro**; unos 130 V entre fase y PE; los mismos motores en triángulo; el mando, entre dos fases). Lo dijo el profesor el 22/11/2026: hay que explicar las dos.
- **Selector de red en las dos animaciones** («La red»: 400 V fábrica / 230 V taller; se recuerda en `localStorage`, clave `red`). A 400 V es el cuadro del papel. A 230 V **los cuatro motores piden la misma corriente que a 400 V** (11 A, 8,3 A, 3,5 A y 6,4 A): son motores de menos potencia, en triángulo, y se rotulan «Δ · 230 V» sin los kW. Por eso **no cambia ninguna protección ni ningún cable** (lo pidió el profesor el 23/11/2026: «si tienen todos la misma intensidad, tanto en 400 como en 230», la general no tiene que cambiar). Solo cambian el rótulo de la red, el de los motores y las tensiones: en `busca_averia.html`, 230 V entre fases, 133 V con PE y unos 115 V en la fase que falta; en `averias_protecciones.html`, la carcasa sin tierra queda con «unos 130 V».
- Los ocho tipos de avería: sobrecarga, cortocircuito, derivación a tierra, falta de fase, mal contacto, cable dañado, fases cambiadas y protección mal elegida o mal ajustada.
- Modelo de clase (no «corregirlo»): salta la protección **más cercana aguas arriba**; el relé térmico no corta la fuerza (abre su 95-96 y cae el contactor); en la falta de fase la pinza marca 0 A en una fase y una vez y media en las otras, y la fase que falta marca «unos 200 V» por los bobinados; tensión fantasma 20-30 V = 0 V; el diferencial de 30 mA salta entre 15 y 30 mA.
- `busca_averia.html` usa la línea de `-M3` con sus propias letras (A B C entrada de -Q3 · D E F salida de -Q3 · G H J salida de -KM3 · K M P motor) y siete averías; se abre en una con `#1`…`#7`. `averias_protecciones.html` tiene 14 averías; se abre en una con `#1`…`#14`.
- Las dos animaciones, las figuras y los Word salen de guiones guardados en el proyecto «Materiales para instituto» (`claude/automatismos/T7/` y `claude/automatismos/T7_averias_estado.md`): **no se editan a mano los HTML**; se cambia el guion y se regeneran.
