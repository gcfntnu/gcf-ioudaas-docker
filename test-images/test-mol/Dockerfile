# See the value of userImage in
#
#   https://github.com/Uninett/helm-charts/blob/master/repos/stable/jupyterhub/values.yaml
#
# to determine the latest base image

FROM quay.io/uninett/jupyterhub-singleuser:20180703-0ff1eb6

# Install system packages
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
RUN R --slave -e "BiocManager::install(c('limma', 'edgeR', 'DESeq2', 'WGCNA', 'ggplot2', 'data.table', 'plyr', 'tidyverse', 'rcolorbrewer', 'apeglm', 'crayon'))"


