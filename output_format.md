# **JSON v14 Specification**

## **bin2file.json**

`"json_version": 14;` used to check for necessary fields. Some versions will only add info and be backwards compatible. This check is made strict to be safe.

`"pangenome_length": 52441; ` length in nucleotides of the pangenome. This is usally greater than the length of any individual path. If a path visits nodes more than one time, this my change.

`"zoom_levels"; ` One entry for each level of the zoom stack where the key is a string version of the bin width and the value is a list of chunks at that bin width.



*   `"1"; `bin width of 1 nucleotide, this level contains “fasta” sequence for visualization
    *   `"bin_width": 1; ` same as above` `
    *   `"last_bin": 52441; ` This is the pangenome length / the bin width with rounding accounted for.
    *   `"Files";`  A preview index of every chunk file at this zoom level.
        *   `"file": "chunk000_bin1.schematic.json";`  data filename to Fetch after prefixing data_source/bin_width/
        *   `"first_bin": 0; ` first bin of the first component of this chunk
        *   `"last_bin": 171;` last bin of the last component of this chunk
        *   `"component_count": 38;`  number of `"components"`  in `"file"` . Used to calculate the number of padding columns when using width compression.
        *   `"link_count": 137;`  number of `"arrivals"`  plus `"departures" ` in `"file"` . The number of Link columns that need to be accounted for when using width compression.
        *   `"fasta": "seq_chunk000_bin1.fa"; ` filename for sequence for visualization of this chunk. Only Appears at bin width 1.

## chunk000_bin1.schematic.json 


`"json_version": 14; ` used to check for necessary fields. Some versions will only add info and be backwards compatible. This check is made strict to be safe.

`"bin_width": 1; ` Number of pangenome nucleotides in each bin or column

`"first_bin": 0; ` first bin of the first component of this chunk (see bin 0 note)

`"last_bin": 171; ` last bin of the last component of this chunk

`"Components";`  contiguous blocks of linear presence/absence variants; insertion and deletions shared by the individuals/paths.
* **Special Note:** Bin 0 is reserved to mean the beginning or end of an individual path.  All paths start at bin 0, traverse through any number of other bins and then end at bin 0.  Links to Bin 0 should not be rendered like normal links. This causes a "dummy component" at the beginning of the pangenome with first_bin,last_bin: 0.

*   `"first_bin": 1; ` first bin coordinate inside this component
*   `"last_bin": 2; ` last bin coordinate inside this component (inclusive)
*   `"occupants";`  if the information in the interval [`"components.first_bin"` , `""components.last_bin"` ] refers to the i-th individual/path.
    *   `[true, false, false, ...];` “occupants” is a precompute shortcut. Each row is true if “matrix” has any coverage > 0.5 in that row. 
*   `"matrix":` 
    *   `[[[1,0,[[1136,1136]]], [], ...]:` 2D array of “cells”. Each row is an individual, each column is a gene locus or “bin”. Cells list the information for each individual at that bin. Each cell consists of *bin_id_*, *mean_cov*, *mean_inv*, *mean_pos* and an array of positional ranges of a path.
*   `"arrivals";` 
    *   `"upstream": 3; ` last bin coordinate of departure component
    *   `"downstream": 1; ` first bin coordinate of this component
    *   `"participants": [false, false, false, ...]; ` array of length N paths, true if the path contains this rearrangement
*   `"departures";` 
    *   `"upstream": 2; ` last bin coordinate of this component
    *   `"downstream": 6; ` first bin coordinate of arriving component
    *   `"participants": [false, false, false, ...]; ` array of length N paths, true if the path contains this rearrangement
    * **Special Note:** The last entry of every departures array is a special value containing the "Adjacent Connectors". These are the list of individuals which traverse from Component N to N+1 instead of taking a non-linear link.  There is no matching "arrivals" column and the adjacent connectors are rendered differently in schematize. For this reason `sum(len(departures)) = sum(len(arrivals)) + component_count`. Not all departures have a corresponding arrival. This will be changed ([see this comment](https://github.com/graph-genome/Schematize/issues/80#issuecomment-628136157)).

* `"x": 0; ` cumulative left X coordinate to speed up the visualization in columns. assumes that the Matrix is shown in there is no width compression. The value in columns does not change regardless of the pixels per column.

* `"path_names":`  individual/path names. Used to identify and correlate with faster files and phylogenetic tree.  This specific ordering of individuals is also used to reference the index of An individual in compressed participants and occupants, As well as haplo block row ordering in future versions.

* `"total_nr_files": 253`  Total number of files at this zoom level, used to calculate the zero padding on the file name. Needed in component segmentation but not schematize.

* `"pangenome_length": 52441 ` Copy of the pangenome length in nucleotides.

* `"filename": "chunk000_bin1.schematic.json" ` Own filename. Needed in component segmentation but not Schematize. May be useful for checking cache integrity.  
