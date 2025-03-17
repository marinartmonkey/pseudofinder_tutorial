## **1. ¿Qué es Pseudofinder?**

`Pseudofinder` es una **herramienta bioinformática de código abierto**
diseñada para detectar pseudogenes en genomas de baterias y arqueas.
Desarrollada en `Python 3`, se basa en archivos GenBank anotados para
identificar candidatos a pseudogenes.

## **2. Instalación**

### **2.1. Clona el repositorio.**

Descarga el código fuente desde `GitHub` ejecutando en la terminal:

    git clone https://github.com/filip-husnik/pseudofinder.git

### **2.2. Instala las dependencias.**

Pseudofinder requiere `Python 3` y varias bibliotecas adicionales.
Puedes instalar las dependencias utilizando `pip`. Por ejemplo, con pip:

    pip install biopython plotly pandas numpy reportlab

### **2.3. Instala BLAST+.**

Pseudofinder utiliza `BLAST+` para las búsquedas de secuencias. Puedes
instalarlo desde el Centro Nacional de Información Biotecnológica (NCBI)
o utilizando `conda`:

    conda install -c bioconda blast

### **2.4. Prepara una base de datos de proteínas.**

Descarga y formatea una base de datos de proteínas, como la base de
datos no redundante (NR) de NCBI, para las búsquedas `BLAST`. Aunque
esta base de datos es la ideal, su instalación es costosa, ya que se
trata de una base de datos gigante (&gt;100 GB). En su lugar, se instala
la de `SwissProt`.

    wget https://ftp.expasy.org/databases/uniprot/current_release/knowledgebase/complete/uniprot_sprot.fasta.gz

Después, descomprime la carpeta descargada en tu directorio de trabajo y
extrae en ella el fichero `uniprot_sprot. fasta`.

    makeblastdb -in uniprot_sprot.fasta -dbtype prot -out swissprot

Deberías obtener algo como:

    Building a new DB, current time: 03/17/2025 10:14:00
    New DB name:   C:\Users\marin\Desktop\gbk_files\swissprot
    New DB title:  uniprot_sprot.fasta
    Sequence type: Protein
    Keep MBits: T
    Maximum file size: 3000000000B
    Adding sequences from FASTA; added 572970 sequences in 19.9419 seconds.

Con esto la base de datos `SwissProt` ha sido creada correctamente.

### **2.5. Anota tu genoma.**

Asegúrate de que tu genoma de interés esté anotado en formato `GenBank`
(.gbk). Se recomienda utilizar herramientas como Prokka con las opciones
`--compliant` y `--rfam` para generar anotaciones compatibles.

Si ya tienes los genomas anotados te puedes saltar este paso.

### **2.6. Ejecuta Pseudofinder.**

Una vez que hayas preparado todo, puedes ejecutar `Pseudofinder` para
detectar pseudogenes en tu genoma anotado:

    python pseudofinder.py annotate --genome tu_genoma.gbk --database ruta_a_tu_base_de_datos --outprefix resultado

## **3. Anexos**

Para más info.:

-   Consulta mi Github: <https://github.com/marinartmonkey>
