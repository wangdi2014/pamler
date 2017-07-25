# PAMLer

PAML on steroids, basically. 

With this pipeline, we want to compute site-specific dn/ds for ~4000 genes that have interfacial residues interacting with virus. 

Contributors: Kernyu and Albert

# Objective

Make the following pipeline

![](assets/pipeline-20170725.png)

# How to use it

* Install `jq` first

    # Download CCR5 cdna using ENSMBL API
    $bash src/ensembl_filter_json.sh CCR5 cdna | python src/json2fasta.py
    # Download CCR5 protein using ENSMBL API
    $bash src/ensembl_filter_json.sh CCR5 protein | python src/json2fasta.py
    
    # Alignment using MUSCLE
    $bash src/ensembl_filter_json.sh CCR5 cdna | python src/json2fasta.py  | muscle -physout tmp.phy # XXX this produces a phylip format that is not compatible with PAML.

    # Generate PAML ctl file
    $bash src/generate_template.ctl.sh <alignment> <tree> <outputfile> > tmp.ctl



# TODO

* [ ] gene --> tidy data for site specific dnds 
    * [ ] alignment format issue: muscle/clustalw produces an alignment
    * [ ] rst parser



