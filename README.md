
<h1>Actividad-grupal</h1> 


# Análisis bioinformático de variantes genéticas
Análisis bioinformático de secuencias de DNA, con el fin de identificar variantes genéticas, en forma de SNP o indels, en varias parejas de individuos. Además, tras la identificación de dichas variantes, podréis determinar su relación con patologías monogénicas y, adicionalmente, determinar la probabilidad de que la descendencia de dichas parejas pueda padecer la enfermedad mendeliana identificada.
Se proporcionará una carpeta con los ficheros .fq correspondientes y las parejas asignadas.
 
    1. Indexar el genoma de referencia hg38 (podéis descargarlo aquí) mediante bwa:

bwa index https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip

    2. Alinear las lecturas al genoma de referencia. Para todos los individuos de esta actividad, contamos con lecturas single-end:

bwa mem https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip > https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip

    3. Convertir el fichero .sam a .bam:

samtools view -S -b https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip > https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip

    4. Ordenar el contenido del fichero .bam:

samtools sort https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip -o https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip

    5. Generar un índice del fichero .bam:

samtools index https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip

    6. Llevar a cabo el llamado de variantes:

bcftools mpileup -Ou -f https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip | bcftools call -vmO z -o https://raw.githubusercontent.com/Kotty2998/Actividad-grupal-/main/Resultados sorted/grupal_Actividad_3.8.zip
Una vez ejecutados estos pasos a partir de cada fichero .fq, y tras obtener los archivos .vcf correspondientes, tendréis que identificar las variantes para cada individuo, asociarlas a un fenotipo (una enfermedad monogénica).

