FROM quay.io/uninett/jupyterhub-singleuser:20181130-e94981a

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


USER notebook

RUN conda install --quiet --yes \
    'r-base' \
    'r-biocmanager' && \
    conda clean -tipsy

RUN R --slave -e "BiocManager::install(c('limma', 'edgeR', 'DESeq2', 'WGCNA', 'ggplot2', 'data.table', 'plyr', 'tidyverse', 'rcolorbrewer', 'apeglm'. 'crayon'))"

