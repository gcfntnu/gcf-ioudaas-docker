# See the value of userImage in
#
#   https://github.com/Uninett/helm-charts/blob/master/repos/stable/jupyterhub/values.yaml
#
# to determine the latest base image

FROM quay.io/uninett/jupyterhub-singleuser:20190911-e0a7653

# Install system packages
RUN conda install --quiet --yes \
   'r-base' \
   'r-biocmanager' && \
   conda clean -tipsy

RUN R --slave -e "BiocManager::install(c('DESeq2', 'WGCNA', 'ggplot2'))"


