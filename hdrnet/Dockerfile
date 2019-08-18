FROM nvidia/cuda:8.0-cudnn5-runtime-ubuntu16.04
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
    libglfw3-dev \
    libglm-dev \
    libx11-dev \
    libomp-dev \
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
RUN curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
     chmod +x ~/miniconda.sh && \
     ~/miniconda.sh -b -p /opt/conda && \
     rm ~/miniconda.sh && \
     /opt/conda/bin/conda install -y python=$PYTHON_VERSION && \
     /opt/conda/bin/conda clean -ya
ENV PATH /opt/conda/bin:$PATH

RUN git clone https://github.com/google/hdrnet.git
RUN cd hdrnet/hdrnet && pip install -r requirements.txt && make
