# Define Base Image
FROM belkakari/pytorch-basicS

# Install dependencies

RUN apt-get update && apt-get install -y \
    git \
    cmake \
    build-essential \
    libboost-program-options-dev \
    libboost-filesystem-dev \
    libboost-graph-dev \
    libboost-regex-dev \
    libboost-system-dev \
    libboost-test-dev \
    libeigen3-dev \
    libsuitesparse-dev \
    libfreeimage-dev \
    libgoogle-glog-dev \
    libgflags-dev \
    libglew-dev \
    qtbase5-dev \
    libqt5opengl5-dev \
    libcgal-dev \
    libcgal-qt5-dev

# Install ceres solver
RUN cd /opt
WORKDIR /opt
RUN apt-get install -y libatlas-base-dev libsuitesparse-dev libgoogle-glog-dev libeigen3-dev libsuitesparse-dev
RUN git clone https://ceres-solver.googlesource.com/ceres-solver
RUN cd ceres-solver
WORKDIR /opt/ceres-solver
RUN mkdir build
RUN cd build
WORKDIR /opt/ceres-solver/build
RUN cmake .. -DBUILD_TESTING=OFF -DBUILD_EXAMPLES=OFF
RUN make
RUN make install


# Install Colmap

RUN cd /opt
WORKDIR /opt
RUN git clone https://github.com/colmap/colmap
RUN cd colmap
WORKDIR /opt/colmap
RUN mkdir build
RUN cd build
WORKDIR /opt/colmap/build
RUN cmake ..
RUN make
RUN make install
RUN cd /

# Install pytorch 3d stuff
RUN pip install kornia pyrender trimesh rtree shapely &&\
    conda install -y -c open3d-admin open3d
