#The three galerucella species were analysed with the same pipeline. Here we used G. calmariensis as an example. 
###########################1. de-novo assembly###################################################################
#de-novo assembly using the Supernova 2.1.0 
supernova run --id=G.calm --fastqs=demuxed_fastq_files --maxreads=all


###########################2. draft genome polishing#############################################################
#polished the draft assembly using purge_dups v.1.0.1 
purge_dups/bin/split_fa $rawgc/purgedgc.fa  > $rawgc/gc.fa.split 
minimap2 -xasm5 -DP $rawgc/gc.fa.split $rawgc/gc.fa.split | gzip -c - > $rawgc/gc.fa.split.self.paf.gz
purge_dups/bin/purge_dups -2 -T cutoffs -c TX.base.cov $rawgc/Gc.fa.split.self.paf.gz > dups.bed 2> purge_dups.log
python3 purge_dups/scripts/hist_plot.py -c cutoffs TX.stat gc.cov.png
/purge_dups/bin/get_seqs dups.bed $rawgc/gc.fasta

#scaffolded using arcs+links pipeline
##Run Long Ranger basic on raw chromium reads to produce interleaved linked reads file
longranger basic --id=outputprefix --fastqs=/Path/to/directory/of/raw/chromium/shortreads/fastqgzfile
##Make sure the soft link of your assembly (assembly.fasta) and barcode file (barcodedchromium.fq.gz) is in the links working directory, run arcs-links:
##a: maximum link ratio between two best contig pairs, defalt a=0.3, higher values such as a= 0.7 and 0.9 is recommended when running LINKS within ARCS but higher values lead to least accurate scaffolding 
arcs-make arcs draft=my_scaffolds reads=barcodedchromium threads=18 a=0.7

##contamination detection, human,bacterial, archaeal, and viral databases were used
kraken --threads 16 --db /dbkraken/ gc.final.fa  > gc.kraken
kraken-translate --db /dbkraken/ gc.kraken > gc.labels

############################3. assessing assembly quality########################################################
#assessed the completeness of polished genome assemblies using busco
db=$endopterygota_odb10
python run_BUSCO.py -o busco_final_gc -i gc_final.fa -l $db -m genome
