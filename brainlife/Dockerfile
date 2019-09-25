FROM ubuntu:18.04
MAINTAINER Serge Koudoro <skab12@gmail.com>

ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates curl git gcc && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# install miniconda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

RUN pip install --upgrade setuptools pip

# install default requirement
RUN pip install numpy scipy cython nibabel h5py

# install optional dependency
RUN conda config --set always_yes yes --set changeps1 no && \
    conda config --add channels conda-forge && \
    conda install --yes cvxpy

RUN pip install scikit-learn scikit-image statsmodels fury matplotlib tables pandas

# install DIPY
RUN pip install dipy==0.16.0

#make it work under singularity
RUN ldconfig && mkdir -p /N/u /N/home /N/dc2 /N/soft

#https://wiki.ubuntu.com/DashAsBinSh
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

ENV PYTHONNOUSERSITE=true