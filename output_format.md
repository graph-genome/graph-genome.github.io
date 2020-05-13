**JSON v14**

**bin2file.json**

* <code>"json_version": 14;</code></strong>used to check for necessary fields. Some versions will only add info and be backwards compatible. This check is made strict to be safe.

* <code>"pangenome_length": 52441; </code></strong>length in nucleotides of the pangenome.  This will be greater than the Length of any individual path 

* <code>"zoom_levels"; </code></strong>One entry for each level of the zoom stack where the key is a string version of the bin width and the value is a list of chunks at that bin width.



*   `"1"; `bin width of 1 nucleotide, this level contains “fasta” sequence for visualization
    *   **<code>"bin_width": 1; </code></strong>same as above<code> </code>
    *   <strong><code>"last_bin": 52441; </code></strong>This is the pan genome length / the bin width with rounding accounted for.
    *   <strong><code>"Files";</code></strong> A preview index of every chunk file at this zoom level 
        *   <strong><code>"file": "chunk000_bin1.schematic.json";</code></strong> data filename to Fetch after prefixing data_source/bin_width/
        *   <strong><code>"first_bin": 0; </code></strong>first bin of the first component of this chunk
        *   <strong><code>"last_bin": 171;</code></strong>last bin of the last component of this chunk
        *   <strong><code>"component_count": 38;</code></strong> number of <strong><code>"components"</code></strong> in <strong><code>"file"</code></strong>. Used to calculate the number of padding columns when using width compression 
        *   <strong><code>"link_count": 137;</code></strong> number of <strong><code>"arrivals"</code></strong> plus <strong><code>"departures" </code></strong>in <strong><code>"file"</code></strong>. The number of Link columns that need to be accounted for when using width compression.
        *   <strong><code>"fasta": "seq_chunk000_bin1.fa"; </code></strong>filename for sequence for visualization of this chunk. Only Appears at bin width 1 

<strong>chunk000_bin1.schematic.json</strong>

**<code>"json_version": 14; </code></strong>used to check for necessary fields. Some versions will only add info and be backwards compatible. This check is made strict to be safe.

**<code>"bin_width": 1; </code></strong>Number of nucleotides in each bin or column

* <code>"first_bin": 0; </code></strong>first bin of the first component of this chunk

* <code>"last_bin": 171; </code></strong>last bin of the last component of this chunk

* <code>"Components";</code></strong> contiguous blocks of linear presence/absence variants; insertion and deletions shared by the individuals/paths.



*   **<code>"first_bin": 1; </code></strong>first bin coordinate inside this component
*   <strong><code>"last_bin": 2; </code></strong>last bin coordinate inside this component (inclusive)
*   <strong><code>"occupants";</code></strong> if the information in the interval [<strong><code>"components.first_bin"</code></strong>, <strong><code>""components.last_bin"</code></strong>] refers to the i-th individual/path.
    *   <code>[true, false, false, ...];</code> “occupants” is a precompute shortcut. Each row is true if “matrix” has any coverage > 0.5 in that row. 
*   <strong><code>"matrix":</code></strong>
    *   <code>[[[1,0,[[1136,1136]]], [], ...]:</code> 2D array of “cells”.  Each row is an individual, each column is a gene locus or “bin”. Cells list the information for each individual at that bin.  
*   <strong><code>"arrivals";</code></strong>
    *   <strong><code>"upstream": 3; </code></strong>last bin coordinate of departure component
    *   <strong><code>"downstream": 1; </code></strong>first bin coordinate of this component
    *   <strong><code>"participants": [false, false, false, ...]; </code></strong>array of length N paths, true if the path contains this rearrangement
*   <strong><code>"departures";</code></strong>
    *   <strong><code>"upstream": 2; </code></strong>last bin coordinate of this component
    *   <strong><code>"downstream": 6; </code></strong>first bin coordinate of arriving component
    *   <strong><code>"participants": [false, false, false, ...]; </code></strong>array of length N paths, true if the path contains this rearrangement

<strong><code>"x": 0; </code></strong>cumulative left X coordinate to speed up the visualization in columns. assumes that the Matrix is shown in there is no width compression. The value in columns does not change regardless of the pixels per column.

**<code>"path_names":</code></strong> individual/path names. Used to identify and correlate with faster files and phylogenetic tree.  This specific ordering of individuals is also used to reference the index of An individual in compressed participants and occupants, As well as haplo block row ordering in future versions. 

**<code>"total_nr_files": 253</code></strong> Total number of files at this zoom level,  used to calculate the zero padding on the file name. Needed in component segmentation but not schematize.

**<code>"pangenome_length": 52441 </code></strong>Copy of the pangenome length in nucleotides. 

**<code>"filename": "chunk000_bin1.schematic.json" </code></strong>Own filename. Needed in component segmentation but not Schematize. May be useful for checking cache integrity.  
