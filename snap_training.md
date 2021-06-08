## Snap

The input file used for training SNAP comes from the Ab-initio training pipeline output at the default location `results/BlastFilteredGFF/codingGeneFeatures.filter.longest_cds.complete.good_distance_blast-filtered.gff3` called `annotation.gff` in this protocol. 
Those input file are accessible here:  
  * [galerucella_calmariensis](./annotation/galerucella_calmariensis/abinitio_profiles/snap)  
  * [galerucella_pusilla](./annotation/galerucella_pusilla/abinitio_profiles/snap)  
  * [galerucella_tenella](./annotation/galerucella_tenella/abinitio_profiles/snap) 
  
Before to train SNAP we also need the genome fasta file (genome.fa), and concatenate the gff and fasta files together using the following commands:

```
echo "##FASTA" >> annotation.gff
cat genome.fa >> annotation.gff
```

The annotation and genome then need to be converted into SNAP compatible formats. The Maker script maker2zff is used for that purpose:

```
maker2zff -n annotation.gff
```

This produce two files – **genome.ann** and **genome.dna**


Finally, you run a small utility script from [GAAS](https://github.com/NBISweden/GAAS) (in the same folder) that will string together the different formatting steps to produce a SNAP hmm profile:

```
gaas_snap_train.sh <species_name>
```

The result file you should use is called **<species_name>.hmm**
