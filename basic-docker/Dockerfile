FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
ARG PYTHON_VERSION=3.7

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
     /opt/conda/bin/conda install -y python=$PYTHON_VERSION numpy pyyaml scipy ipython mkl \
     mkl-include ninja cython typing jupyter matplotlib tqdm pandas scikit-learn && \
     /opt/conda/bin/conda install -y pytorch=1.2 torchvision cudatoolkit=10.0 -c pytorch && \
     /opt/conda/bin/conda install -y -c menpo opencv && \
     /opt/conda/bin/conda install -y -c conda-forge tensorboardx && \
     /opt/conda/bin/conda install -y -c anaconda scikit-image && \
     /opt/conda/bin/conda clean -ya && rm -rf /var/lib/apt/lists/*
ENV PATH /opt/conda/bin:$PATH

RUN pip install tb-nightly && \
    pip install --extra-index-url https://developer.download.nvidia.com/compute/redist/nightly/cuda/10.0 nvidia-dali-nightly && \
    CC="cc -mavx2" pip install -U --force-reinstall pillow-simd && \
    rm -rf /var/lib/apt/lists/*
    
RUN wget -O /root/.cache/torch/checkpoints/vgg19-dcbb9e9d.pth https://download.pytorch.org/models/vgg19-dcbb9e9d.pth
    
WORKDIR /

EXPOSE 8889
