Personal Identification Pipeline
================================

This pipeline takes a minION sequencing results (a directory with FAST5 files),
maps them to the human genome, and compares them against a collection
of 23-and-Me files, looking for a potential match.


Prerequisites
-------------

The pipeline requires the following components:

* wget, GNU sed, and other standard unix command-line programs
* samtools, bgzip, tabix <http://www.htslib.org/>
* BWA <https://github.com/lh3/bwa>
* Python 2.7 with following python modules:
    * poretools <https://github.com/arq5x/poretools>
    * numpy, scipy
    * pysam
* For plotting - R <www.r-project.org> with these libraries:
    * hexbin
    * RColorBrewer
    * gplots
    * naturalsort
    * optparse

Detailed Installation Instructions
----------------------------------

These programs have been tested on Ubuntu 14.04 64bit GNU/Linux machine.
Other environments might require some adjustments.

Download the latest pipeline code

    # Using GIT
    git clone https://github.com/TeamErlich/personal-identification-pipeline
    cd personal-identification-pipeline

    # Or using ZIP
    wget https://github.com/TeamErlich/personal-identification-pipeline/archive/master.zip
    unzip master.zip

The `setup` directory contains helper script to install the required software:

    # Install required packages:
    sudo ./setup/setup-ubuntu1404.sh

    # Install python modules:
    sudo pip install -r ./setup/requirements.txt

    # Install samtools 1.3.1 (will use 'sudo' automatically)
    ./setup/setup-samtools.sh

    # Install bgzip/tabix 1.3.1 (will use 'sudo' automatically)
    ./setup/setup-htslib.sh

    # Install BWA 0.7.15 (will use 'sudo; automatically)
    ./setup/setup-bwa.sh


Building data files
-------------------

The personal-identification pipeline requires few pre-processed data files.

Download hg19 reference genome, build BWA index (this will take some time,
depending on the machine's hardware. About ~70m on a 2.5Ghz Intel XEON E5):

    ./setup/setup-hg19.sh

Download dbSNP-138 Common and build db (requires downloading ~620MB,
will take some time depending on the network speed):

    ./setup/setup-snp138common.sh

Optionally, download Yaniv Erlich's genotype file:

    ./setup/setup-YE-genotype.sh

Example
-------

The `demo` directory contains a simplified example of the pipeline workflow.
See `./demo/README.md` for more details.


Help and Usage information
--------------------------

The following scripts support help and usage information with
the `--help` parameter (`-h` in case of the shell script):

    run-personal-id-pipeline.sh -h
    run-parallel-calc-prob.sh -h
    poretools-basenames.py --help
    sam-to-bedseq.py --help
    sam-discard-dups.py --help
    calc-match-probs.py --help
    generate-snp-list.py --help


Contact
-------

Yaniv Erlich <yaniv@cs.columbia.edu>

<http://TeamErlich.org>


License
-------

Copyright (C) 2016 Yaniv Erlich (yaniv@cs.columbia.edu)

All Rights Reserved.

This software is restricted to educational, research, not-for-profit purposes.

See LICENSE file for full details.

Contact Yaniv Erlich for commercial licensing opportunities.
