# Seguimiento-1
## Descripción del formato GFF3
Es un archivo de texto plano, delimitado por tabulaciones, contiene anotaciones genómicas que se refiere a la asignación de nombre, función y coordenadas a las regiones funcionales de una secuencia de ADN dentro de un genoma. Estas anotacionesestan organizadas en 9 columnas. Es ampliamente usado en bioinformática por la facilidad de uso de herramientas de línea de comandos como `grep` y `cut` con los que se puede extraer información facilmente.
Cada línea representa un feature del genoma (genes, exones, regiones, etc). Si un campo no tiene dato, se escribe un punto `(.)`.

Las columnas se asignan de la siguiente forma: 
| **Columna** | **Descripción**                                                                                 | **Ejemplo**                           |
| ------------| ------------------------------------------------------------------------------------------------| ------------------------------------- |
| seqid       | Identificador de la secuencia (cromosoma, scaffold o contig).                                   | `AAGV03000001.1`, `chr1`              |
| source      | Fuente del dato (software o base de datos que generó la anotación).                             | `NCBI`, `GenBank`, `Ensembl`          |
| type (feature) | Tipo de característica anotada.                                                              | `gene`, `exon`, `CDS`                 |
| start       | Número de nucleótido donde esta la posición inicial de la característica (base 1).              | `1000`                                |
| end         | Número de nucleótido donde esta la posición final de la característica.                         | `5000`                                |
| score       | Valor numérico que indica la confiabilidad del feature anotado, puede ser un `P-value`          | `0.95`, `.`                           |
| strand      | Hebra donde se encuentra: `+` (sentido), `-` (antisentido), `.` (sin hebra), `?` (desconocido). | `+`                                   |
| phase       | Solo aplica para `CDS`. Indica cuántos nucleótidos sobran antes del próximo codón.              | `0`, `1`, `2`                         |
| attributes  | Información adicional en pares `clave=valor`, como su nombre visible o su relación con otros elementos. | `Parent=transcript1`          |

Ojo: En genomas que ya estan muy bien secuenciados como el de los humanos, el campo seqid puede verse como `chr1`, `chr2`, etc. En el caso de *Dasypus novemcinctus*, se utilizan identificadores de ensamblaje como AAGV03000001.1, que representan scaffolds o contigs en lugar de cromosomas completamente definidos.

De esta forma, una linea en un formato GFF3 se vería así: 

`chr1      ensembl exon    184114  197611  .       -       .       ID=transcript:ENSDNOT00000002212;Parent=gene:ENS`

(The-Sequence-Onthology, 2020)
## Organismo: *Dasypus novemcinctus*
El armadillo de nueve bandas es un mamifero pequeño nativo del sureste de America, tiene un caparazón bandeado y una temperatura corporal baja, entre 33 a 35 °C. Por este motivo y por su susceptibilidad y respuesta fisiológica al microorganismo *Mycobacterium leprae*, es un organismo modelo ideal para el estudio de la lepra. Durante su época reproductiva, en la implantación embrionaria siempre se forman cuadruplicados, esta poliembrionía consistente de la especie también lo ha convertido en un modelo de interés para comprender diversos aspectos de la gemelaridad. (Hickman et al., 2016)

## Comandos utilizados
(Ver el archivo `comandos.txt` para ejecutar cada paso.)

## Resultados del análisis
**Número total de features:** Al contar las líneas únicas en la columna 3, se obtienen **18** tipos distintos.

**Número de regiones (secuencias únicas):** En el encabezado del archivo se escriben las unidades estructurales sobre las que se realizan las anotaciones, utilizando líneas que comienzan con ##sequence-region. Estas muestran los identificadores (seqid) de cada una. En el caso específico del genoma de *Dasypus novemcinctus*, no se cuenta con regiones anotadas sobre cromosomas completos, en cambio, las anotaciones se encuentran sobre scaffolds, de los cuales se identificaron **46 559** únicos.

Para conocer cuántas secuencias únicas existen en el archivo (es decir, cuántas regiones del genoma han sido anotadas), se pueden emplear varias estrategias:
1. Contar las líneas que comienzan con ##sequence-region en el encabezado.
2. Identificar los valores únicos en la columna seqid, ya que las anotaciones (como genes, exones, CDS) pueden repetirse en la misma secuencia.
3. Contar las líneas donde el tipo (type, columna 3) es scaffold, asegurando que el seqid asociado no se repita. Esto funciona solo si cada scaffold está declarado una única vez, como es habitual.

**Número de genes listados:** Este genoma tiene un total de **33 374** genes listados 

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
