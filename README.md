# Seguimiento-1
## Descripción del formato GFF3
Es un archivo de texto plano, delimitado por tabulaciones, contiene anotaciones genómicas que se refiere a la asignación de nombre, función y coordenadas a las regiones funcionales de una secuencia de ADN dentro de un genoma. Estas anotacionesestan organizadas en 9 columnas. Es ampliamente usado en bioinformática por la facilidad de uso de herramientas de línea de comandos como `grep` y `cut` con los que se puede extraer información facilmente.
Cada línea representa un feature del genoma (genes, exones, regiones, etc). Si un campo no tiene dato, se escribe un punto `(.)`.

Las columnas se asignan de la siguiente forma: 
1. seqid: Identificador de la secuencia (por ejemplo, cromosoma o contig).
2. source: Fuente del dato (software o base de datos que generó la anotación).
3. type (feature): Tipo de característica (gene, exon, CDS...), según el Sequence Ontology.
4. start: Posición inicial de la característica (1-based).
5. end: Posición final.
6. score: Valor numérico opcional (puede ser un valor estadístico como un E-value o P-value).
7. strand: Hebra en la que se encuentra la característica: +, -, ., o ?.
8. phase: Solo para CDS. Indica cuántos nucleótidos sobran antes de que empiece el siguiente codón (0, 1 o 2).
9. attributes: Información adicional en formato clave=valor, como el ID del feature, su nombre visible, su relación con otros elementos (ej. Parent=transcript1) y otras anotaciones.

De esta forma, una linea en un formato GFF3 se vería así: 



(The-Sequence-Onthology, 2020)
## Organismo: *Dasypus novemcinctus*
El armadillo de nueve bandas es un mamifero pequeño nativo del sureste de America, tiene un caparazón bandeado y una temperatura corporal baja, entre 33 a 35 °C. Por este motivo y por su susceptibilidad y respuesta fisiológica al microorganismo *Mycobacterium leprae*, es un organismo modelo ideal para el estudio de la lepra. Durante su época reproductiva, en la implantación embrionaria siempre se forman cuadruplicados, esta poliembrionía consistente de la especie también lo ha convertido en un modelo de interés para comprender diversos aspectos de la gemelaridad. (Hickman et al., 2016)

## Comandos utilizados
(Ver el archivo `comandos.txt` para ejecutar cada paso.)

## Resultados del análisis
**Número total de features:** 18

**Número de regiones (secuencias únicas):** 612731

**Número de genes listados:** 33374

**Top 10 de tipos de features más anotados en el genoma:**
| #  | Tipo               | Cantidad |
| -- | ------------------ | -------- |
| 1  | biological\_region | 612731   |
| 2  | exon               | 262138   |
| 3  | CDS                | 237769   |
| 4  | scaffold           | 46559    |
| 5  | mRNA               | 26551    |
| 6  | gene               | 22711    |
| 7  | five\_prime\_UTR   | 16849    |
| 8  | three\_prime\_UTR  | 11702    |
| 9  | ncRNA\_gene        | 9163     |
| 10 | lnc\_RNA           | 3688     |

### Referencias 
The-Sequence-Onthology (2020). Specifications [Repositorio de GitHub]. https://github.com/The-Sequence-Ontology/Specifications/blob/master/gff3.md

Hickman, D., Johnson, J., Vemulapalli, T., Crisler, J., & Shepherd, R. (2016). Commonly used animal models. In Elsevier eBooks (pp. 117–175). https://doi.org/10.1016/b978-0-12-802151-4.00007-4
