# BRIGaid
(SOS) BRIGaid generates xml files contaning the necessary data to aid in the execution of [BRIG](http://brig.sourceforge.net/) (Blast Ring Image Generator). 
This file will then be opened in BRIG and will fill all the necessary fields.

## __Usage__ (Commander)

```
% brigaid.py -q reference_sequence.fna -rfd path/to/reference/dir -od path/to/output/dir -of path/to/output/dir/output_file -oi path/to/output/BRIG/output_image -t Image_title -a annotation_file.gbk --genes genes_of_interest.txt --contig_order contig_order.tsv --blast_options "-evalue 0.001 -num_threads 6" --legend_pos upper-center --image_format png --height 3000 --width 3000 --java_memory 2000 --colormap viridis
```

### __Basic use__ (Human)
BRIGaid will generate an xml file with the necessary parameters to create an image using a reference file in ```.fasta``` format and the files contained on the reference directory and also indicates where the output of BRIG should go.

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title 
```

### __Tweak BRIG options__ (Alien)
BRIGaid also allows the tweaking of some of BRIG's parameters such as:

* Arguments for Blast 
```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --blast_options "-evalue 0.001 -num_threads 6"
```

* Position of the legend of BRIG's output image.

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --legend_pos upper-center
```

* Format of BRIG's output image.

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --image_format png
```

* Height and width (in pixels) of BRIG's output image.

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --height 3000 --width 3000
```

* Amount of memory (in bytes) Java is allowed to use for BRIG

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --java_memory 2000
```

* Colormap for the color of the rings

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --colormap viridis
```

### __Ring annotation__ (Time traveler)
BRIGaid accepts tab-delimited files or annotated Genbank files allowing the annotations of the rings.

Example of tab-delimited file:

```
#START	STOP	Label	Colour	Decoration
137680	139977	prot_1	black	clockwise-arrow
251394	253547	prot_2	black	clockwise-arrow
```


Command:

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --annotation annotations.gbk
```

It is also possible to provide a list of specific genes (one-per-line) to annotate the rings.

Example of a list of specific genes:

```
prot_1
prot_2
prot_3
```


Command:

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --annotation annotations.gbk --genes genes.txt
```

### __Ordering Contigs__ (Esper)

BRIGaid is able to order the contigs of the provided files by providing a simple tab-delimited file containing the preferred order of the contigs.

```
% brigaid.py -q reference_sequence.fna --ref_dir path/to/reference/dir --out_dir path/to/output/dir --out_xml path/to/output/dir/output_file --out_img path/to/output/BRIG/output_image --title Image_title --contig_order contig_order.tsv
```

Example of possible tab-delimited file:
```
order   contig
1       Contig8
2       Contig10
```


## __Dependencies__
* __[Biopython](https://biopython.org/)__ v1.74 

_Cock PA, Antao T, Chang JT, Chapman BA, Cox CJ, Dalke A, Friedberg I, Hamelryck T, Kauff F, Wilczynski B and de Hoon MJL (2009) Biopython: freely available Python tools for computational molecular biology and bioinformatics. Bioinformatics, 25, 1422-1423_

* __[matplotlib](https://matplotlib.org/)__ v3.1.1

_J. D. Hunter, "Matplotlib: A 2D Graphics Environment", Computing in Science & Engineering, vol. 9, no. 3, pp. 90-95, 2007._ 