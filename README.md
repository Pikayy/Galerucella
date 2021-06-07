
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

---------------------------

## Foreword

Here are presented information about assembly and annotation of closely related leaf beetle species (Galerucella spp).

## Assembly

Scripts for Genome assemblies is available [here](./commandline_genome_assembly_polishing.md)

## Annotation

### Repeat library

Protocol to prepare the repeat library is available [here](https://www.biostars.org/p/411101/#411101).

**Results:**. 
[galerucella_calmariensis](./annotation/galerucella_calmariensis/repeat_lib.fa)  
[galerucella_pusilla](./annotation/galerucella_pusilla/repeat_lib.fa)  
[galerucella_tenella](./annotation/galerucella_tenella/repeat_lib.fa)  

### MAKER evidence-based

### Ab-initio training

#### Augustus

Augustus has been trained using the NBIS `AbinitioTraining` nextflow pipeline available [here](https://github.com/NBISweden/pipelines-nextflow).

Commit used for this study was `e1a0648c90331a8ab9170de643a0b7d579278f24`

#### SNAP

Protocol to train SNAP is available [here](./snap_training.md).

### MAKER ab-initio evidence-driven

### Functional annotation

The functional annotation has been performed using the NBIS `FunctionalAnnotation` nextflow pipeline available [here](https://github.com/NBISweden/pipelines-nextflow).

Commit used for this study was `3a4d29a20d8ea261f7e766882547f754b06d1e2b`
