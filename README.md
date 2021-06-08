
Galerucella spp (leaf beetle species) genomes project (Yang et al., 2021)

---------------------------

## Table of Contents

   * [Foreword](#foreword)
   * [Assembly](#assembly)
   * [Annotation](#Annotation)  
      * [Repeat library](#repeat_library)
      * [MAKER evidence-based](#maker_evidence_based)
      * [Ab-initio training](#ab_initio_training)
      * [MAKER ab-initio evidence-driven](maker_ab_initio_evidence_driven)
      * [Functional annotation](functional_annotation)
      * [Other](other)

---------------------------

## Foreword

Here are presented information about assembly and annotation of closely related leaf beetle species (Galerucella spp).

## Assembly

Scripts for Genome assemblies is available [here](./commandline_genome_assembly_polishing.md)

## Annotation

The three galerucella species were annotated following the same approach. The protocol of the different steps is described below.

### Repeat library

Protocol to prepare the repeat library is available [here](https://www.biostars.org/p/411101/#411101).

**Results:**  
  * [galerucella_calmariensis](./annotation/galerucella_calmariensis/repeat_lib.fa)  
  * [galerucella_pusilla](./annotation/galerucella_pusilla/repeat_lib.fa)  
  * [galerucella_tenella](./annotation/galerucella_tenella/repeat_lib.fa)  

### MAKER evidence-based

Gene annotation was performed using the MAKER package version 3.01.02 with the repeat library, the protein and transcriptome data as described in the manuscript.  
The Maker parameter files used are available here:
  * [galerucella_calmariensis](./annotation/galerucella_calmariensis/MAKER/rc1)  
  * [galerucella_pusilla](./annotation/galerucella_pusilla/MAKER/rc1)  
  * [galerucella_tenella](./annotation/galerucella_tenella/MAKER/rc1)  

Results have been collected from MAKER output folder using `gaas_maker_merge_outputs_from_datastore.pl` from [GAAS](https://github.com/NBISweden/GAAS).

### Ab-initio training

#### Augustus

Augustus has been trained using the NBIS `AbinitioTraining` nextflow pipeline available [here](https://github.com/NBISweden/pipelines-nextflow).

Commit used for this study was `e1a0648c90331a8ab9170de643a0b7d579278f24`

#### SNAP

Protocol to train SNAP is available [here](./snap_training.md).

The resulting hmm profiles are available here:
  * [galerucella_calmariensis](./annotation/galerucella_calmariensis/abinitio_profiles/snap)  
  * [galerucella_pusilla](./annotation/galerucella_pusilla/abinitio_profiles/snap)  
  * [galerucella_tenella](./annotation/galerucella_tenella/abinitio_profiles/snap)  

### MAKER ab-initio evidence-driven

Gene annotation was performed using the MAKER package version 3.01.02 with the repeat library, the protein, the transcriptome data and the abinitio hmm profiles as described in the manuscript.  
The Maker parameter files used are available here:
  * [galerucella_calmariensis](./annotation/galerucella_calmariensis/MAKER/rc4)  
  * [galerucella_pusilla](./annotation/galerucella_pusilla/MAKER/rc4)  
  * [galerucella_tenella](./annotation/galerucella_tenella/MAKER/rc4)  

Results have been collected from MAKER output folder using `gaas_maker_merge_outputs_from_datastore.pl` from [GAAS](https://github.com/NBISweden/GAAS).

### Functional annotation

The functional annotation has been performed using the NBIS `FunctionalAnnotation` nextflow pipeline available [here](https://github.com/NBISweden/pipelines-nextflow).

Commit used for this study was `3a4d29a20d8ea261f7e766882547f754b06d1e2b`

### Other

The tool GFF toolkit [AGAT](https://github.com/NBISweden/AGAT) has been used to generate the statistics of the different annotations. It is also used by the `gaas_maker_merge_outputs_from_datastore.pl` script and by `AbinitioTraining` and `FunctionalAnnotation` nextflow pipelines.
