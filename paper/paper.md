---
title: '
COVID-19 Biohackathon April 5-11 2020 - Pangenome Browser'
tags:
  - pangenome_browser
  - pantograph
authors:
  - name: Josiah Seaman
    orcid: 0000-0003-2374-630X
    affiliation: 1 
  - name: Simon Heumos
    orcid: 0000-0003-3326-817X
    affiliation: 2
  - name: Toshiyuki T. Yokoyama 
    orcid: 0000-0002-7345-6397
    affiliation: 3
  - name: Torsten Pook
    orcid: 0000-0001-7874-8500 
    affiliation: 4
  - name: Jerven Bolleman
    orcid: 0000-0002-7449-1266
    affiliation: 5
  - name: Artem Tarasov
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Bonface Munyoki
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Eloi Durant
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Hannah Sewell
    orcid: 0000-0000-0000-0000
    affiliation: IN-PART
  - name: Travis Clark
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Thomas Townsley
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Dmytro Trybushnyi
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Jack Tierney
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Jacob Windsor
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Robert Fornof
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Njagi Mwaniki
    orcid: 0000-0002-4858-2375
    affiliation: 8
  - name: Mark Seaman
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Kaytie Innamorati
    orcid: 0000-0000-0000-0000
    affiliation: 
  - name: Jörg Hagmann
    orcid: 0000-0002-7232-3103
    affiliation: 7
  - name: Erik Garrison
    orcid: 0000-0003-3821-631X
    affiliation: 6
  - name: Andrea Guarracino
    orcid: 0000-0001-9744-131X
    affiliation: 9
affiliations:
  - name: Royal Botanic Gardens Kew
    index: 1
  - name: Quantitative Biology Center, University of T¨ubingen, T¨ubingen, Germany, 72076
    index: 2
  - name: The University of Tokyo, Chiba, Japan
    index: 3
  - name: University of Goettingen
    index: 4
  - name: Swiss-Prot group, Swiss Institute of Bioinformatics, Geneva
    index: 5
  - name: University of California Santa Cruz
    index: 6
  - name: Computomics GmbH
    index: 7
  - name: Pwani University
    index: 8
  - name: University of Rome Tor Vergata, Via della Ricerca Scientifica 1, Rome, Italy
    index: 9
date: 11 April 2020
bibliography: paper.bib
---
# Introduction or Background

As part of the one week COVID-19 Biohackathon April 5-11 2020, we formed
a working group on the interactive visualization of graphical pangenomes.

Success or failure of our efforts to fight COVID19 rely on the sequence diversity of the virus itself. Tests for infection by SARS-CoV-19 rely on knowing the exact sequence of the virus, vaccines are designed to mimic the exact structure of a specific protein without rearrangements and drugs are designed to target proteins which they assume will not change. Having a clear idea of where sequence diversity lies or where rearrangements and variants appear to be arising will give researchers a headstart in their hunt for therapeutics and aid our fight of the disease. In addition, normal reference based sequencing can lead to under-representations of the full diversity because of bias in the way the genomes are built. Methods of building and fully visualizing the genetic diversity of the virus need to be developed.

TODO intro graphical pangenomes \
TODO intro pantograph pangenome browser

The `Pangenome Browser' working group at the 2020 edition of the
VirtualBioHackathon addressed themselves with different aspects of a pangenome browser:

- TODO item1
- TODO item2

## Component Schematization FAIRification

We added a new schema ontology and RDF output format to Component Schematization, building
on the VG ontology. RDF allows combining data in the visualisation, with arbritary other data encodded in RDF. This allows us to use SPARQL (a generic W3C standard graph query language) queries to allign components, bins and other visual artifacts with genome, protein and chemical annotations using SPARQL.


## COVID-19 Annotated Pangenome graph

The pangenome graphs build from sequences deposited in INDSC are serialized as RDF and loaded into https://covid-19-sparql.expasy.org. This SPARQL endpoint contains the pangenome, as well as the annotated sequences from INDSC, the annotated protein sequences from UniProt. Receptors, by UniProt and NeXtProt, as well as close orthologes from OMA and expression data from Bgee.

This query system allows us to ask varied questions of the data in combination with the FAIR Component Schematization. Queries, such as in this variant, what are the annotations present in the mainline sequences but missing here.

## Display of Nucleotides Above Graphical Representation of Graph Genome

We added the successful rendering of the appropriate nucleotides above the matrix that represents the graph genome. This is read in from fasta files and then processed so that at each bin the correct letter is shown. This will allow researchers to clearly see what sequence changes have occured in the genome as well as the rearrangement


## Tables, figures and so on

Please remember to introduce tables (see Table 1) before they appear on the document. We recommend to center tables, formulas and figure but not the corresponding captions. Feel free to modify the table style as it better suits to your data.

Table 1
| Header 1 | Header 2 |
| -------- | -------- |
| item 1 | item 2 |
| item 3 | item 4 |

Remember to introduce figures (see Figure 1) before they appear on the document. 

![Project Overview](./overview.png)
 
Figure 1. A figure corresponding to the logo of our BioHackrXiv preprint.

# Other main section on your manuscript level 1

Feel free to use numbered lists or bullet points as you need.
* Item 1
* Item 2


## HaploBlocker Extension

The HaploBlocker implementation was indented to merge locally similar specimens. Based on this potential break points of the genome sequence are identified and specimens can be sorted according to their local similarities. Even tough is has shown to be highly useful for common livestock and crop populations, this kind of sorting is not required for common viruses, like CoVID-19 and the Sars family as genome usually only have a size of a couple of kilobase pairs with no recombination and relatively small number of mutations.

As part of the CoVID-19-Biohackathon, a specific Virus-mode of our HaploBlocker implementation was developed, with is allowing for no variation between specimens (merging_error = 0, min_similarity = 1 in HB), as specimens of the SARS2 family on average were only different in 70 basepairs. The resulting haplotype library only had a single haplotype block in most regions, but clearing indications with specimens are different to the local main variant (Figure 2). 

![sars2](https://user-images.githubusercontent.com/38560663/78676994-77bee880-78e7-11ea-8c0d-d85d36077577.PNG)
Figure 2. HaploBlocker visualization of 169 Sars2 strands

When however also including Sars1 specimens there was basically no overlap within the families (Figure 3). Therefore, an additional mode was implemented to specifically identify regions with shared variation between different parts of the SARS family by identified subgroups in HaploBlocker, but even when allowing for major deviations between specimens of different families only very limited overlap could be identified (Figure 4). 

![Sars1vsSars2_regular](https://user-images.githubusercontent.com/38560663/78677501-1c412a80-78e8-11ea-9428-5b0bc3139df5.PNG)
Figure 3. HaploBlocker visualization of 343 strands of the Sars-family

![Sars1vsSars2](https://user-images.githubusercontent.com/38560663/78677903-92de2800-78e8-11ea-8e4c-ae2e7d6caf53.PNG)
Figure 4. Overlapping haplotype blocks between the Sars1 and Sars2 family.

Thirdly, the HaploBlocker pipeline now provided output-file containing information of the obtained haplotype library to allow coloring by haplotype blocks. This is particular helpful for users to identify long-range assosiations between specimens.


# Discussion and/or Conclusion

We recommend to include some discussion or conclusion about your work. Feel free to modify the section title as it fits better to your manuscript.

# Future work

And maybe you want to add a sentence or two on how you plan to continue. Please keep reading to learn about citations and references.

For citations of references, we prefer the use of parenthesis, last name and year. If you use a citation manager, Elsevier – Harvard or American Psychological Association (APA) will work. If you are referencing web pages, software or so, please do so in the same way. Whenever possible, add authors and year. We have included a couple of citations along this document for you to get the idea. Please remember to always add DOI whenever available, if not possible, please provide alternative URLs. You will end up with an alphabetical order list by authors’ last name.

# Jupyter notebooks, GitHub repositories and data repositories

* Please add a list here
* Make sure you let us know which of these correspond to Jupyter notebooks. Although not supported yet, we plan to add features for them
* And remember, software and data need a license for them to be used by others, no license means no clear rules so nobody could legally use a non-licensed research object, whatever that object is

# Acknowledgements
Please always remember to acknowledge the BioHackathon, CodeFest, VoCamp, Sprint or similar where this work was (partially) developed.

# References

Leave thise section blank, create a paper.bib with all your references
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI4NzEwNDQ1NywtMjEzMTcwODcwNiwtMT
MxNjE0ODA2NiwzNDk3MTkxMTgsNDEwMzM4MTMsLTg2NDUwNTMw
MSwxNDc4NDMwMjkyLC0xMzYyMTUxMTgxLC0yMTM5MDUyMzQyXX
0=
-->
