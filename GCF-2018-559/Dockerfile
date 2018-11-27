FROM quay.io/uninett/jupyterhub-singleuser:20181117-d19dbd4


USER root

# R pre-requisites
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    fonts-dejavu \
    tzdata \
    gfortran \
    gcc && apt-get clean && \
    rm -rf /var/lib/apt/lists/*


USER notebook

RUN conda config --add channels defaults
RUN conda config --add channels r
RUN conda config --add channels bioconda
RUN conda config --add channels conda-forge

RUN conda install --quiet --yes \
    'r-base' \
    'r-irkernel=0.8*' \
    'r-plyr' \
    'r-devtools' \
    'r-tidyverse' \
    'r-rsqlite' \
    'r-reshape2' \
    'r-rcurl' \
    'r-crayon=' \
    'r-htmltools=0.3*' \
    'r-htmlwidgets=1.0*' \
    'bioconductor-deseq2=1.18*' \
    'bioconductor-apeglm' \
    'r-wgcna' \
    'r-ggplot2' \
    'r-rcolorbrewer' \
    'r-stringr' \
    'r-data.table' && \
    conda clean -tipsy

