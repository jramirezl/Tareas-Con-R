# Usa una imagen base con miniconda
FROM mcr.microsoft.com/devcontainers/miniconda:0-ubuntu-22.04

# Instala dependencias necesarias del sistema
RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libgit2-dev \
    libzmq3-dev \
    libclang-dev \
    libglpk-dev \
    build-essential \
    wget \
    curl \
    unzip \
    nano

# Configura conda y crea un entorno con R y Jupyter
RUN conda update -n base -c defaults conda && \
    conda create -n r_env -y -c conda-forge \
    r-base=4.3 \
    r-irkernel \
    r-ggplot2 \
    r-dplyr \
    r-tidyr \
    r-readr \
    r-faraway \
    r-ggally \
    notebook && \
    conda clean --all -f -y

# Activar conda env por defecto al entrar
RUN echo "conda activate r_env" >> ~/.bashrc
ENV PATH /opt/conda/envs/r_env/bin:$PATH

# Exponer puerto para Jupyter
EXPOSE 8888
