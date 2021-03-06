FROM nvidia/cuda:8.0-cudnn5-devel-ubuntu14.04
ARG PYTHON_VERSION=3.5

# Setup basic packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    curl \
    vim \
    ca-certificates \
    libjpeg-dev \
    libpng-dev \
    libglm-dev \
    libx11-dev \
    libegl1-mesa-dev \
    libsndfile1 \
    pkg-config \
    wget \
    zip \
    unzip \
    tmux \
    htop \
    cmake \
    imagemagick &&\
    rm -rf /var/lib/apt/lists/*

# Install conda
RUN curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-4.3.14-Linux-x86_64.sh  && \
    chmod +x ~/miniconda.sh && \
    ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda install -y python=$PYTHON_VERSION && \
    /opt/conda/bin/conda install -y -c menpo opencv && \
    /opt/conda/bin/conda clean -ya
ENV PATH /opt/conda/bin:$PATH

RUN pip install numpy==1.12.0 \
                Cython==0.17 && \
                scipy \
    pip install setproctitle==1.1.10 \
                pyglib==0.1 \
                scikit_image==0.9.3 \
                tensorflow_gpu==1.1.0 \
                python_gflags==3.1.1 \
                python_magic==0.4.13
