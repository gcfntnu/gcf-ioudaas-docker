FROM quay.io/uninett/jupyterhub-singleuser:20210324-27d46e5

USER root

# R pre-requisites
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    fonts-dejavu \
    tzdata \
    libhdf5-dev \
    liblzma-dev \
    build-essential \
    libcurl4-gnutls-dev \
    libxml2-dev \
    libssl-dev \
    gfortran \
    gcc && apt-get clean && \
    rm -rf /var/lib/apt/lists/*


RUN conda config --add channels defaults && \
    conda config --add channels bioconda && \
    conda config --add channels conda-forge
    
USER notebook

RUN conda install -c conda-forge --yes mamba
RUN mamba install --quiet --yes \
    'r-base' \
    'r-tidyverse' \
    'r-wgcna' \
    'r-plyr' \
    'r-rcolorbrewer' \
    'r-data.table' \
    'r-ggplot2' \
    'bioconductor-deseq2' \
    'bioconductor-apeglm' \
    'bioconductor-limma' \
    'bioconductor-edger' \
    'r-biocmanager' && \
    mamba clean -ai

#RUN R --slave -e "BiocManager::install(c('foreign', 'limma', 'edgeR', 'DESeq2', 'WGCNA', 'ggplot2', 'data.table', 'plyr', 'tidyverse', 'RColorBrewer', 'apeglm', 'crayon'), ask=FALSE)"

