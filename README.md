BlobTools v1.1.2
===============================

This code has been forked from [BlobTools](https://github.com/DRL/blobtools) and has been assigned the semver
release id `v1.1.2`. This increments the last release from the primary repository and accommodates the trivial
changes in the `setup.py` for the code to install with `pip3`.

A modular command-line solution for visualisation, quality control and taxonomic partitioning of genome datasets

- Discussions, questions and answers: [BlobTools GoogleGroup](https://groups.google.com/forum/#!forum/blobtools)
- Issues, bug reports and feature requests: [GitHub issues](https://github.com/DRL/blobtools/issues)
- Documentation: [blobtools.readme.io](https://blobtools.readme.io)
- Citation: [Laetsch DR and Blaxter ML, 2017](https://f1000research.com/articles/6-1287/v1)

![](https://github.com/DRL/blobtools/blob/master/example/blobplot.png)

Obtaining BlobTools
------------
- **Option A**: Download latest [release](https://github.com/DRL/blobtools/releases/latest)
- **Option B**: Clone repository
  ```
  git clone https://github.com/DRL/blobtools.git
  ```

Enter directory
------------
  ```
  cd blobtools
  ```

Install dependencies
------------
- Create [Conda](https://conda.io/en/latest/miniconda.html) environment and install dependencies

  ```
  conda create -n blobtools
  conda activate blobtools
  conda install -c anaconda -c bioconda matplotlib docopt tqdm wget pyyaml git pysam
  ```
  
Download NCBI taxdump and create nodesdb
------------
  ```
  wget ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/taxdump.tar.gz -P data/
  tar zxf data/taxdump.tar.gz -C data/ nodes.dmp names.dmp
  ./blobtools nodesdb --nodes data/nodes.dmp --names data/names.dmp
  ```

Create blobplot
------------
  ```
  ./blobtools create -i example/assembly.fna -b example/mapping_1.sorted.bam -t example/blast.out -o example/test && \
  ./blobtools view -i example/test.blobDB.json && \
  ./blobtools plot -i example/test.blobDB.json
  ```
Usage
-----
```
    ./blobtools --help
```

Docker
------

A docker container can be build using the following command:
```
     docker build -t drl/blobtools .
```
This docker image can be run with sample data as follows:
```
     docker run -v $PWD/example:/example/  -t  drl/blobtools ./blobtools create -i /example/assembly.fna -b /example/mapping_1.sorted.bam -t /example/blast.out -o /example/test
```
