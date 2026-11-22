# Automatismos Industriales · Recuperación — I.E.S. Trinidad Arroyo (Palencia)

Web de clase para los alumnos de 1MB que **repiten** Automatismos. Es **el mismo material** que la web de Automatismos (`BernardoTorio/automatismos`), pero con **otra línea de tiempo**: aquí se va por delante de la clase normal. Por eso lo nuevo se publica primero aquí y **no se sube a `automatismos` hasta que el profesor lo diga**.

Se publica con GitHub Pages desde la rama `main`, carpeta raíz: `https://bernardotorio.github.io/RecuperacionAutomatismos/` (repositorio `BernardoTorio/RecuperacionAutomatismos`).

Todas las reglas de la web de Automatismos valen aquí (su `CLAUDE.md` manda): nombres de archivo que no cambian, animaciones en la raíz, pestañas `#inicio`, `#temas`, `#ejercicios` y `#animaciones`, criterios de dibujo, letra delante del número (T, P, E), «Qué está pasando» y «Para qué sirve» debajo del dibujo, corriente sutil, modo claro y oscuro, prueba en escritorio y en móvil (400 px). **Nunca se suben zips ni .docx.**

## Qué hay
```
index.html                  portada (la de Automatismos, solo con los Temas 6 y 7): var HOY = 7;
temas/                      T6_Dimensionamiento_protecciones.pdf · T7_Resolucion_averias_Automatismos.pdf
ejercicios/                 T6_Ejercicios_Dimensionamiento_protecciones.pdf (Ejercicios 1)
                            T7_Ejercicios_Resolucion_averias_Automatismos.pdf (Ejercicios 2: 60 preguntas tipo test)
intensidad_calor.html … cuadro_motores.html    las seis animaciones del Tema 6, copiadas tal cual de Automatismos (vuelven a #ejercicios)
averias_protecciones.html   T7.11 ¿Qué protección salta?  (vuelve a #animaciones)
busca_averia.html           T7.12 Busca la avería          (vuelve a #animaciones)
```
- Lo del Tema 6 es **copia** de la web de Automatismos: si allí cambia algo, se copia aquí otra vez (no se edita aquí por separado).
- Las soluciones de los Ejercicios 2 **no se publican**: están en `C:\dev\originales\automatismos\ejercicios\T7_Soluciones_Resolucion_averias_Automatismos.docx`.
- `bernardotorio.github.io` es el mismo sitio para todas las webs: la marca «✓ vista» de las animaciones del Tema 6 se comparte con la web de Automatismos (misma clave `visto:<archivo>`).

## Tema 7 · Resolución de averías
- Todo el tema, los Ejercicios 2 y las dos animaciones usan **el mismo cuadro**: un esquema de fuerza de fábrica (red de 400 V) con cuatro motores. Es la antigua Práctica 10, redibujada con los criterios actuales y con valores que cumplen el Tema 6:
  - `-F0` fusibles generales 3 × 63 A gG (cable de 16 mm²) → `-Q0` magnetotérmico general 40 A curva C (cable de 6 mm²).
  - Línea de `-M1` (5,5 kW Δ, 11 A): diferencial `-Q5` 40 A 30 mA → guardamotor `-Q1` 10-14 A, ruleta 11 A → `-KM1`.
  - Línea de `-M2` (4 kW Y, 8,3 A): diferencial `-Q6` → guardamotor `-Q2` 6,3-10 A, ruleta 8,3 A → `-KM2`.
  - Grupo de `-M3` y `-M4`: `-Q7` 16 A curva C (cable de 2,5 mm²) → diferencial `-Q8` 40 A 30 mA → `-Q3` 6 A C → `-KM3` → térmico `-F3` 2,5-4 A a 3,5 A → `-M3` (1,5 kW Y, 3,5 A); y `-Q4` 10 A C → `-KM4` → `-F4` 6-9 A a 6,4 A → `-M4` (3 kW Y, 6,4 A). Arranque de 6 veces.
  - Entre el último aparato de cada línea y su motor va el **bornero de fuerza `-X1`**, con los tornillos 1 a 12 (tres por motor: 1-2-3 para -M1 … 10-11-12 para -M4). De ahí salen las mangueras de 1,5 mm². **U1, V1 y W1 son los tornillos del motor** y se rotulan pegados a él, no en el cuadro.
  - Los magnetotérmicos y los guardamotores **no llevan símbolo de mando** (nada de la «T» de pulsador): solo la línea discontinua que va del nombre a los contactos.
  - Letras de medida del esquema (línea de -M1): Ⓐ Ⓑ el 1 y el 5 de -Q1 · Ⓒ Ⓓ el 2 y el 6 de -Q1 · Ⓔ Ⓕ el 2 y el 6 de -KM1 · Ⓖ Ⓗ el U1 y el W1 de -M1.
- **Dos redes** (punto 7.13): la de una fábrica, que es la del cuadro (400 V entre fases, con neutro; 230 V entre fase y PE; motores de 230/400 V en estrella), y la del **taller** (230 V entre fases, **sin neutro**; unos 130 V entre fase y PE; los mismos motores en triángulo; el mando, entre dos fases). Lo dijo el profesor el 22/11/2026: hay que explicar las dos.
- **Selector de red en las dos animaciones** («La red»: 400 V fábrica / 230 V taller; se recuerda en `localStorage`, clave `red`). A 400 V es el cuadro del papel. A 230 V los motores de 230/400 V van en triángulo y cambian placas, ruletas y calibres: `-M1` pasa a ser de 2,2 kW Δ 8,4 A (el de 5,5 kW es de 400/690 V y no se puede conectar a 230 V), `-Q1` 6,3-10 A a 8,4 A · `-M2` 4 kW Δ 14,3 A, `-Q2` 14-18 A a 14,3 A · `-M3` 1,5 kW Δ 6 A, `-Q3` 10 A C, `-F3` 4-6 A a 6 A · `-M4` 3 kW Δ 11 A, `-Q4` 16 A C, `-F4` 9-13 A a 11 A · `-Q7` 20 A C · `-Q0` 40 A (suma 39,7 A). En `busca_averia.html` cambian además las medidas: 230 V entre fases, 133 V con PE, unos 115 V en la fase que falta. Lo que salta en cada avería es lo mismo en las dos redes.
- Los ocho tipos de avería: sobrecarga, cortocircuito, derivación a tierra, falta de fase, mal contacto, cable dañado, fases cambiadas y protección mal elegida o mal ajustada.
- Modelo de clase (no «corregirlo»): salta la protección **más cercana aguas arriba**; el relé térmico no corta la fuerza (abre su 95-96 y cae el contactor); en la falta de fase la pinza marca 0 A en una fase y una vez y media en las otras, y la fase que falta marca «unos 200 V» por los bobinados; tensión fantasma 20-30 V = 0 V; el diferencial de 30 mA salta entre 15 y 30 mA.
- `busca_averia.html` usa la línea de `-M3` con sus propias letras (A B C entrada de -Q3 · D E F salida de -Q3 · G H J salida de -KM3 · K M P motor) y siete averías; se abre en una con `#1`…`#7`. `averias_protecciones.html` tiene 14 averías; se abre en una con `#1`…`#14`.
- Las dos animaciones, las figuras y los Word salen de guiones guardados en el proyecto «Materiales para instituto» (`claude/automatismos/T7/` y `claude/automatismos/T7_averias_estado.md`): **no se editan a mano los HTML**; se cambia el guion y se regeneran.
